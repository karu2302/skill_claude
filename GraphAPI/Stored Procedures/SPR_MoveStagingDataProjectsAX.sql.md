# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataProjectsAX.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataProjectsAX.sql`
- SHA-256 of original file: `e0ec50eb5e5483661a2778d070e82c0251874c0473d0751faba6b077b2ab7777`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataProjectsAX] @ProjectsAX [GraphAPI].[ProjectsAX] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI ProjectsAX'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'ProjectsAX',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[ProjectsAX] --WITH (TABLOCK)
		([BudgetClosed],
		[BudgetEuro],
		[Country],
		[DemeOrganisationalStructureId],
		[DEMETurnover],
		[EndDate],
		[Exclude],
		[ImpactConversionProjectNumber],
		[JointVenture],
		[ProjectId],
		[ProjectName],
		[ProjectTitle],
		[ProjectWithC02],
		[QHSESCampaigns],
		[QHSESCampaignTopic],
		[QHSESendDate],
		[QHSEStartDate],
		[QHSEStatus],
		[StartDate])
	SELECT 
		H.[BudgetClosed] AS [BudgetClosed],
		H.[BudgetEuro] AS [BudgetEuro],
		H.[Country] AS [Country],
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		H.[DEMETurnover] AS [DEMETurnover],
		H.[EndDate] AS [EndDate],
		H.[Exclude] AS [Exclude],
		H.[ImpactConversionProjectNumber] AS [ImpactConversionProjectNumber],
		H.[JointVenture] AS [JointVenture],
		H.[ProjectId] AS [ProjectId],
		H.[ProjectName] AS [ProjectName],
		H.[ProjectTitle] AS [ProjectTitle],
		H.[ProjectWithC02] AS [ProjectWithC02],
		H.[QHSESCampaigns] AS [QHSESCampaigns],
		H.[QHSESCampaignTopic] AS [QHSESCampaignTopic],
		H.[QHSESendDate] AS [QHSESendDate],
		H.[QHSEStartDate] AS [QHSEStartDate],
		H.[QHSEStatus] AS [QHSEStatus],
		H.[StartDate] AS [StartDate]
	FROM @ProjectsAX H

	SELECT @NrOfRows = @@ROWCOUNT
	EXEC ETL.SPR_LogEndRunDetail @ETLRunDetailsId = @ETLRunDetailsId, @NrOfIn = @NrOfRows
END TRY
BEGIN CATCH
	SELECT @ErrorMessage=ERROR_MESSAGE()
	EXEC ETL.SPR_LogEndRunDetail @ETLRunDetailsId = @ETLRunDetailsId, @Status = N'Failed', @ErrorMessage = @ErrorMessage;
	THROW 51000, @ErrorMessage, 1
END CATCH
END
````
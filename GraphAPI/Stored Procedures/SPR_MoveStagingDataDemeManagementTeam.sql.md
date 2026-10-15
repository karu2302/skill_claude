# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataDemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataDemeManagementTeam.sql`
- SHA-256 of original file: `e4d3537ba22e3265b52b4b537df932584ba7e2badb38757c1e12cf8a86c59283`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataDemeManagementTeam] @DemeManagementTeam [GraphAPI].[DemeManagementTeam] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI DemeManagementTeam'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'DemeManagementTeam',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[DemeManagementTeam] --WITH (TABLOCK)
		([ActiveMember],
		[Campus],
		[CDWE],
		[Country],
		[DemeOrganisationalStructureId],
		[Email],
		[FullName],
		[QHSESEndDate],
		[QHSESStartDate],
		[Senior],
		[SupportingService],
		[TargetQHSESVisit],
		[TargetVesselVisit])
	SELECT 
		CASE WHEN H.[ActiveMember]='' THEN NULL ELSE H.[ActiveMember] END AS [ActiveMember],
		CASE WHEN H.[Campus]='' THEN NULL ELSE H.[Campus] END AS [Campus],
		CASE WHEN H.[CDWE]='' THEN NULL ELSE H.[CDWE] END AS [CDWE],
		CASE WHEN H.[Country]='' THEN NULL ELSE H.[Country] END AS [Country],
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		CASE WHEN H.[Email]='' THEN NULL ELSE H.[Email] END AS [Email],
		CASE WHEN H.[FullName]='' THEN NULL ELSE H.[FullName] END AS [FullName],
		CASE WHEN H.[QHSESEndDate]='' THEN NULL ELSE H.[QHSESEndDate] END AS [QHSESEndDate],
		CASE WHEN H.[QHSESStartDate]='' THEN NULL ELSE H.[QHSESStartDate] END AS [QHSESStartDate],
		CASE WHEN H.[Senior]='' THEN NULL ELSE H.[Senior] END AS [Senior],
		CASE WHEN H.[SupportingService]='' THEN NULL ELSE H.[SupportingService] END AS [SupportingService],
		CASE WHEN H.[TargetQHSESVisit]='' THEN NULL ELSE H.[TargetQHSESVisit] END AS [TargetQHSESVisit],
		CASE WHEN H.[TargetVesselVisit]='' THEN NULL ELSE H.[TargetVesselVisit] END AS [TargetVesselVisit]
	FROM @DemeManagementTeam H

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
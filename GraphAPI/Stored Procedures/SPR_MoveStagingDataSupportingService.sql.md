# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataSupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataSupportingService.sql`
- SHA-256 of original file: `d128d80846dd1fe3fae271cb0c0aeb291aa0afb6de260c8a9caae637e4cf94d4`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataSupportingService] @SupportingService [GraphAPI].[SupportingService] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI SupportingService'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'SupportingService',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[SupportingService] --WITH (TABLOCK)
		([DemeOrganisationalStructureId],
		[Exclude],
		[InactiveSince],
		[QHSESCampaigns],
		[QHSESCampaignTopic],
		[QHSESEndDate],
		[SharepointId],
		[SupportingServiceCode],
		[SupportingServiceId],
		[SupportingServiceName],
		[TIBCOIdentifier])
	SELECT 
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		H.[Exclude] AS [Exclude],
		H.[InactiveSince] AS [InactiveSince],
		H.[QHSESCampaigns] AS [QHSESCampaigns],
		H.[QHSESCampaignTopic] AS [QHSESCampaignTopic],
		H.[QHSESEndDate] AS [QHSESEndDate],
		H.[SharepointId] AS [SharepointId],
		H.[SupportingServiceCode] AS [SupportingServiceCode],
		H.[SupportingServiceId] AS [SupportingServiceId],
		H.[SupportingServiceName] AS [SupportingServiceName],
		H.[TIBCOIdentifier] AS [TIBCOIdentifier]
	FROM @SupportingService H

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
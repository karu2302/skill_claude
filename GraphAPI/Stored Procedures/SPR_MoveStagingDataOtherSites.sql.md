# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataOtherSites.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataOtherSites.sql`
- SHA-256 of original file: `a0fbf0e61c376b4c12da56af24c28e831d0d9e7b8bb2e70c17d7248b3bc14259`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataOtherSites] @OtherSites [GraphAPI].[OtherSites] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI OtherSites'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'OtherSites',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[OtherSites] --WITH (TABLOCK)
		([CountryId],
		[DemeOrganisationalStructureId],
		[Exclude],
		[OtherSiteId],
		[OtherSiteName],
		[QHSESCampaigns],
		[QHSESCampaignTopic],
		[QHSESEndDate],
		[QHSESStartDate],
		[SharepointId])
	SELECT 
		H.[CountryId] AS [CountryId],
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		H.[Exclude] AS [Exclude],
		H.[OtherSiteId] AS [OtherSiteId],
		H.[OtherSiteName] AS [OtherSiteName],
		H.[QHSESCampaigns] AS [QHSESCampaigns],
		H.[QHSESCampaignTopic] AS [QHSESCampaignTopic],
		H.[QHSESEndDate] AS [QHSESEndDate],
		H.[QHSESStartDate] AS [QHSESStartDate],
		H.[SharepointId] AS [SharepointId]
	FROM @OtherSites H

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
# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql`
- SHA-256 of original file: `70278d7183e84b3fd1e8d60e64787c078652f741030b9a3b3ba20d686d43c95c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataQHSESCampaignTopics] @QHSESCampaignTopics [GraphAPI].[QHSESCampaignTopics] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI QHSESCampaignTopics'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'QHSESCampaignTopics',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[QHSESCampaignTopics] --WITH (TABLOCK)
		([EventTopic],
		[Title])
	SELECT 
		H.[EventTopic] AS [EventTopic],
		H.[Title] AS [Title]
	FROM @QHSESCampaignTopics H

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
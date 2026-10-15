# Source: `DBs/AzureSingleDB/Fixed/Stored Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/Fixed/Stored Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql`
- SHA-256 of original file: `34de30cb8e1bf035ae3ca31a682512e6740aa337916117507864eb30ea5bb955`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [Fixed].[SPR_MoveStagingDataTypeOfWorkingHour] @TypeOfWorkingHour [Fixed].[TypeOfWorkingHour] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage Fixed TypeOfWorkingHour'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'Fixed',
	@SchemaName = NULL,
	@TableName = 'TypeOfWorkingHour',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingQHSE].[TypeOfWorkingHour] --WITH (TABLOCK)
		([TypeOfWorkingHour])
	SELECT 
		H.[TypeOfWorkingHour] AS [TypeOfWorkingHour]
	FROM @TypeOfWorkingHour H

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
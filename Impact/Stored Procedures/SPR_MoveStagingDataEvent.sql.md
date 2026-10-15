# Source: `DBs/AzureSingleDB/Impact/Stored Procedures/SPR_MoveStagingDataEvent.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/Impact/Stored Procedures/SPR_MoveStagingDataEvent.sql`
- SHA-256 of original file: `0e5769207765a00fe395c0b4abb382ee36b09e7f01840a88a8c286c5cde28094`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [Impact].[SPR_MoveStagingDataEvent] @Event [Impact].[Event] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage Impact Event'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'Impact',
	@SchemaName = NULL,
	@TableName = 'Event',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingImpact].[Event] --WITH (TABLOCK)
		([Date],
		[EventType],
		[Project],
		[QHSESEventID],
		[ResponsibleDepartment],
		[StatusId],
		[TotalParticipants],
		[Vessel])
	SELECT 
		H.[AU_AUDITDT] AS [Date],
		CASE WHEN H.[UDF_QHSE_EVENT_TYPE_DS]='' THEN NULL ELSE H.[UDF_QHSE_EVENT_TYPE_DS] END AS [EventType],
		CASE WHEN H.[PROJECTNAME]='' THEN NULL ELSE H.[PROJECTNAME] END AS [Project],
		CASE WHEN H.[AUDITHEADID]='' THEN NULL ELSE H.[AUDITHEADID] END AS [QHSESEventID],
		CASE WHEN H.[DEPARTMENTID]='' THEN NULL ELSE H.[DEPARTMENTID] END AS [ResponsibleDepartment],
		CASE WHEN H.[AU_STATUSID]='' THEN NULL ELSE H.[AU_STATUSID] END AS [StatusId],
		CASE WHEN H.[UDF_AU_QHSEE_ATTENDEE_CNT]='' THEN NULL ELSE H.[UDF_AU_QHSEE_ATTENDEE_CNT] END AS [TotalParticipants],
		CASE WHEN H.[UDF_VESSEL_DS]='' THEN NULL ELSE H.[UDF_VESSEL_DS] END AS [Vessel]
	FROM @Event H

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
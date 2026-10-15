# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataVessels.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataVessels.sql`
- SHA-256 of original file: `45d6efd8eb17a1e534b2241adf889fc49e8e3f08f2a5fa8bdd3c34453a30802c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataVessels] @Vessels [GraphAPI].[Vessels] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI Vessels'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'Vessels',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[Vessels] --WITH (TABLOCK)
		([ClassificationSociety],
		[CSRD],
		[DemeOrganisationalStructureId],
		[Exclude],
		[FuelType],
		[GT],
		[ISM],
		[ManagementVisitScope],
		[QHSESCampaigns],
		[QHSESCampaignTopic],
		[QHSESEndDate],
		[QHSESStartDate],
		[RMPE],
		[VesselActive],
		[VesselId],
		[VesselLifecycleStatus],
		[VesselName],
		[VesselUnitName],
		[VMSType])
	SELECT 
		H.[ClassificationSociety] AS [ClassificationSociety],
		H.[CSRD] AS [CSRD],
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		H.[Exclude] AS [Exclude],
		H.[FuelType] AS [FuelType],
		H.[GT] AS [GT],
		H.[ISM] AS [ISM],
		H.[ManagementVisitScope] AS [ManagementVisitScope],
		H.[QHSESCampaigns] AS [QHSESCampaigns],
		H.[QHSESCampaignTopic] AS [QHSESCampaignTopic],
		H.[QHSESEndDate] AS [QHSESEndDate],
		H.[QHSESStartDate] AS [QHSESStartDate],
		H.[RMPE] AS [RMPE],
		H.[VesselActive] AS [VesselActive],
		H.[VesselId] AS [VesselId],
		H.[VesselLifecycleStatus] AS [VesselLifecycleStatus],
		H.[VesselName] AS [VesselName],
		H.[VesselUnitName] AS [VesselUnitName],
		H.[VMSType] AS [VMSType]
	FROM @Vessels H

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
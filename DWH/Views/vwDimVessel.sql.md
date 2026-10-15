# Source: `DBs/AzureSingleDB/DWH/Views/vwDimVessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimVessel.sql`
- SHA-256 of original file: `e0e29643b06a24bc6ebff5698ba5513e96ca8c22aedc73adcd81f0b04ca1b4cf`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE   VIEW [DWH].[vwDimVessel] AS
SELECT
	  [VesselId]
	, DEME
	, [ActivityLineId]
	, ActivityLine
	, BusinessUnitId
	, DivisionId
    , BusinessGroupId
	, [CountryId]
	, [VesselName]
	, [VesselUnitName]
	--, [VesselCategory]
	, [VesselType]
	, [ClassificationSociety]
	, [Exclude]
	, QHSESCampaignTopic
	, [FuelType]
	, [GT]
	, [ISM]
	, [QHSESCampaign]
    --, ImpactConversionDetail
	, [RMPE]
	, [VesselActive]
	, [CharteredVessel]
    , [DimQHSESStartDateId]
    , [DimQHSESEndDateId]
	, [QHSESStartDate]
    , [QHSESEndDate]
	, GIRequired
	, [GITargetStartDate]
    , [GITargetEndDate]
	, VesselLifecycleStatus
	, ManagementVisitScope
	, CSRD
	, VMSType
FROM DataStore2.Vessel
````
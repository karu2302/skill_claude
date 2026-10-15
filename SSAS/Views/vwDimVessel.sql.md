# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimVessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimVessel.sql`
- SHA-256 of original file: `4484b62fd551e078dad7c276807c3a4ef5171e5541cacff1fc4ad98f2e82713e`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql















CREATE   VIEW [SSAS].[vwDimVessel] AS
SELECT
	  [DimVesselId]
	, [DimDEMEHierarchyId]
	, [VesselId]
	, [VesselName]
	, [VesselUnitName]
	--, [VesselCategory]
	, [VesselType]
	, ActivityLine
	, [ClassificationSociety]
--	, [Exclude]
	, [FuelType]
	, [GT]
	, [ISM]
--	, [QHSESCampaign]
--	, QHSESCampaignTopic
	, [RMPE]
	, [VesselActive]
	, [CharteredVessel]
--	, QHSESStartDate
--	, QHSESEndDate
	, VesselLifecycleStatus
	, ManagementVisitScope
FROM DWH.DimVessel
````
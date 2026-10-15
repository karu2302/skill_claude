# Source: `DBs/AzureSingleDB/DWH/Views/vwDimProject.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimProject.sql`
- SHA-256 of original file: `d555f73086bc0b3896c6bd8ccca8702288ae929b9bb688eb89c48808f589f42e`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql













CREATE   VIEW [DWH].[vwDimProject] AS
SELECT
	  [ProjectId]
	, DEME
	, [ActivityLineId]
	, ActivityLine
	, BusinessUnitId
	, DivisionId
	, [CountryId]
    , BusinessGroupId
	, [ProjectName]
	, [ProjectId_Name]
	, [StartDate]
	, [EndDate]
	, [ProjectWithC02]
	--, [Boundary]
	, [BudgetClosed]
	, [QHSEStatus]
	, [DimQHSEStartDateId]
	, [DimQHSESEndDateId]
	, [QHSESCampaigns]
	, [Exclude]
	, QHSESCampaignTopic
	, DEMETurnover
	, BudgetEuro
	, QHSEStartDate
	, QHSESEndDate
	, GIRequired
	, GITargetStartDate
	, GITargetEndDate
	, JointVenture
FROM DataStore2.Project
````
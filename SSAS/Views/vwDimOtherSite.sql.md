# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimOtherSite.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimOtherSite.sql`
- SHA-256 of original file: `0de1d6fc4d276fc67f780f5c66c02ff85c0966fe7c5d7bc85516aaa5b21e97d3`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







CREATE   VIEW [SSAS].[vwDimOtherSite] AS
SELECT
	  [DimOtherSiteId]
	, [DimDEMEHierarchyId]
	, [OtherSiteId]
	, [OtherSiteName]
	, ActivityLine
--	, QHSESCampaignTopic
--	, [QHSESCampaigns]
--	, [Exclude]
--	, QHSESStartDate
--	, QHSESEndDate
FROM DWH.DimOtherSite
````
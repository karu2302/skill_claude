# Source: `DBs/AzureSingleDB/DWH/Views/vwDimOtherSite.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimOtherSite.sql`
- SHA-256 of original file: `5e8b450f872c5b5566ca9270105d85ed2dd011aa3700091aaa53c305662b483c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE   VIEW [DWH].[vwDimOtherSite] AS
SELECT
	  [OtherSiteId]
	, DEME
	, [ActivityLineId]
	, ActivityLine
	, BusinessUnitId
	, DivisionId
    , BusinessGroupId
	, [CountryId]
	, [OtherSiteName]
	, [QHSESCampaigns]
	, [Exclude]
	, QHSESCampaignTopic
    , [DimQHSESStartDateId]
    , [DimQHSESEndDateId]
    , [QHSESStartDate]
    , [QHSESEndDate]
	, GIRequired
	, [GITargetStartDate]
    , [GITargetEndDate]
FROM DataStore2.OtherSite
````
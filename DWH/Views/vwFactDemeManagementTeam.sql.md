# Source: `DBs/AzureSingleDB/DWH/Views/vwFactDemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactDemeManagementTeam.sql`
- SHA-256 of original file: `346e703406f728632bc15cd8acf56661d58417b63e1eccb9b479fbfdd81af127`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE VIEW [DWH].[vwFactDemeManagementTeam] AS 
SELECT 
	  Email
	, FullName
	, DEME
	, ActivityLineId
--	, ActivityLineName
	, BusinessGroupId
--	, BusinessGroupName
	, BusinessUnitId
--	, AreaBUName
	, DivisionId
--	, RegionDivisionName
	, CountryId
--	, CountryName
	, QHSESEndDate
	, QHSESStartDate
	, SupportingService
	, TargetQHSESVisit
	, TargetVesselVisit
	, Senior
	, ActiveMember
--  FROM DataStore3.DemeManagementTeam
	, CDWE
	, Campus
FROM DataStore2.DemeManagementTeam
````
# Source: `DBs/AzureSingleDB/DWH/Views/vwDimSupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimSupportingService.sql`
- SHA-256 of original file: `0a58e7d9d123c51448a27edb896575ce746306ec1deea1f3921e79177b2aeebe`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql











/****** Script for SelectTopNRows command from SSMS  ******/
CREATE VIEW [DWH].[vwDimSupportingService] AS 
SELECT 
	  TibcoIdentifier
	, SupportingServiceId
    , SupportingServiceCode
    , SupportingServiceName
	, DEME
    , ActivityLineId
	, BusinessGroupId
	, BusinessUnitId
	, DivisionId
	, CountryId
    , Exclude
    , QHSESCampaigns
	, QHSESCampaignTopic
	--, DimQHSESStartDateId
    , DimQHSESEndDateId
	--, QHSESStartDate
	, QHSESEndDate
	, GIRequired
	, GITargetEndDate
	, GITargetStartDate
	, InactiveSince
	, Management
	, OrganisedType
	, Parent
	, SupportingServiceNameTibco
	, InTibco
	, Active
  FROM DataStore2.SupportingService
````
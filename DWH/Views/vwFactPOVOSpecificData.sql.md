# Source: `DBs/AzureSingleDB/DWH/Views/vwFactPOVOSpecificData.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactPOVOSpecificData.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `6e9732f21fa47d18313c518d4603fa9a669a7ba0ad78feed54c3f8bd8a845e08`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql















/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DWH].[vwFactPOVOSpecificData] AS 

SELECT 
	  PSDId
    , ProjectId
    --, OfficeId
    --, LegalEntityId
    , VesselId
    , OtherSiteId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
	, SupportingServiceTibcoIdentifier
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
    , ProcessCloser
    , ProcessUrlId
	, ProcessCustomId
    , DimPSDDate
    , NumberOfSuperintendentUpToProjectDirector
    , NumberOfMasterAndChiefEngineer
	, NumberOfISMVesselPresent
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, VesselLocationCode
	, NumberCharteredVessels

  FROM DataStore3.POVOSpecificData
``
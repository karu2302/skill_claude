# Source: `DBs/AzureSingleDB/DataStore2/Views/vwOtherSite.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwOtherSite.sql`
- SHA-256 of original file: `81c5ab0a405cf49c294769a736b4952ffeab4ebe3188f8145b9152218df509b9`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







/****** Script for SelectTopNRows command from SSMS  ******/


CREATE VIEW [DataStore2].[vwOtherSite] AS
SELECT 
    --BUSINESS KEY
	  OtherSiteId
	, OS.SharepointId																								AS SharepointId

    --FOREIGN KEYS
	, ISNULL(DH.DEME , '_N/A')																						AS DEME
	, ISNULL(DH.ActivityLineId , '_N/A')																			AS ActivityLineId
	, ISNULL(DH.ActivityLineNameShort , '_N/A')																		AS ActivityLine
    , ISNULL(DH.BusinessUnitId, '_N/A')																				AS BusinessUnitId             --No Area/Business Unit specified
    , ISNULL(DH.BusinessGroupId, '_N/A')																			AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')																					AS DivisionId     --No RegionDivision specified
    , ISNULL(C.CountryId, '_N/A')																					AS CountryId
	
	, '_N/A' AS BusinessUnitName
	, ISNULL(C.CountryName, '_N/A') AS CountryName
	, '_N/A' AS DivisionName

     --ATTRIBUTES
	--, ISNULL(OS.ImpactConversionDetail, '_N/A')    AS ImpactConversionDetail 
    , ISNULL(OtherSiteName, '_N/A')             AS OtherSiteName
    , ISNULL(QHSESCampaigns, '_N/A')            AS QHSESCampaigns
	, CONVERT(NVARCHAR(4000), ISNULL(REPLACE(REPLACE(REPLACE(QHSESCampaignTopic, '["',''),'","',', '), '"]',''), '_N/A'))		AS QHSESCampaignTopic
    , CONVERT(NVARCHAR(4000),ISNULL(REPLACE(REPLACE(REPLACE(Exclude, '["',''),'","',', '), '"]',''), '_N/A'))	                   AS Exclude
	, ISNULL(DS.DimDateId,'19000101')			AS DimQHSESStartDateId
	, ISNULL(DE.DimDateId,'99990101')			AS DimQHSESEndDateId
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, OS.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS QHSESStartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, OS.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '9999-01-01'))								AS QHSESEndDate
	, CONVERT(BIT, 0)							AS GIRequired
	, CONVERT(DATE, '1900-01-01')				AS GITargetStartDate 
	, CONVERT(DATE, '1900-01-01')				AS GITargetEndDate 

FROM StagingGraphAPI.OtherSites AS OS

	LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
		ON DOS.SharepointId = OS.DemeOrganisationalStructureId

	LEFT JOIN DataStore1.DEMEHierarchy DH
		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId

	
	--LEFT JOIN StagingGraphAPI.BusinessGroups BG
	--	ON BG.SharepointId = OS.BusinessGroupId

	--LEFT JOIN StagingGraphAPI.AreasBusinessUnits ABU
	--	ON ABU.SharepointId = OS.AreaBUId

	--LEFT JOIN StagingGraphAPI.RegionsDivisions RD
	--	ON RD.SharepointId = OS.RegionDivisionId

    -- Join with StagingGraphAPI.Countrues to find corresponding CountryId (via Sharepoint Id)
	LEFT JOIN StagingGraphAPI.Countries AS C
  		ON C.SharepointId  = OS.CountryId
	-- Join with date to prevent dimdateId's not available in DimDate
	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, OS.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DS.DimDateId
	LEFT JOIN ETL.Date DE 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, OS.QHSESendDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DE.DimDateId
````
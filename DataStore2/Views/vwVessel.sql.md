# Source: `DBs/AzureSingleDB/DataStore2/Views/vwVessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwVessel.sql`
- SHA-256 of original file: `dda582e5fe6a4d01054861558b474a7782c4c4acf5632cb338a6b3b186639e08`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE VIEW [DataStore2].[vwVessel] AS

SELECT 
	--BUSINESS KEY
	  ISNULL(V.VesselId, '_N/A')									AS VesselId

	--FOREIGN KEYS
	, ISNULL(DH.DEME , '_N/A')										AS DEME
	, ISNULL(DH.ActivityLineId, '_N/A')								AS ActivityLineId
	, ISNULL(DH.ActivityLineNameShort , '_N/A')						AS ActivityLine
    , ISNULL(DH.BusinessUnitId, '_N/A')								AS BusinessUnitId             --No Area/Business Unit specified
    , ISNULL(DH.BusinessGroupId, '_N/A')							AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')									AS DivisionId         -- No Region/Division specified for Vessel
	, '_N/A'														AS CountryId
		
	, ISNULL(DH.BusinessUnitNameShort, '_N/A')						AS BusinessUnitName
	, '_N/A'														AS CountryName
	, '_N/A'														AS DivisionName

	--ATTRIBUTES
	, ISNULL(V.VesselName   , '_N/A')								AS VesselName
    , ISNULL(V.VesselUnitName, '_N/A')								AS VesselUnitName
	, ISNULL(VPV.vesselType_ , '_N/A')								AS VesselType
    , ISNULL(V.ClassificationSociety, '_N/A')						AS ClassificationSociety
    , CONVERT(NVARCHAR(4000),ISNULL(REPLACE(REPLACE(REPLACE(V.Exclude, '["',''),'","',', '), '"]',''), '_N/A'))								AS Exclude
	, CONVERT(NVARCHAR(4000), ISNULL(REPLACE(REPLACE(REPLACE(V.QHSESCampaignTopic, '["',''),'","',', '), '"]',''), '_N/A'))		AS QHSESCampaignTopic
    , ISNULL(V.FuelType, '_N/A')									AS FuelType
    , ISNULL(V.GT, '0' )											AS GT						-- Default value? cannot convert to int ',' vs '.'    
	, ISNULL(V.ISM, '_N/A')											AS ISM
    , CONVERT(NVARCHAR(5), V.QHSESCampaigns)						AS QHSESCampaign
    , ISNULL(V.RMPE, '_N/A')										AS RMPE
    , ISNULL(CONVERT(BIT, V.VesselActive), 0)						AS VesselActive				
	, CONVERT(BIT, 0)												AS CharteredVessel			
	, ISNULL(DS.DimDateId,'19000101')								AS DimQHSESStartDateId
	, ISNULL(DE.DimDateId,'99990101')								AS DimQHSESEndDateId
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, V.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS QHSESStartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, V.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '9999-01-01'))								AS QHSESEndDate
	, CONVERT(BIT, 0)												AS GIRequired
	, CONVERT(DATE, '1900-01-01')									AS GITargetStartDate 
	, CONVERT(DATE, '1900-01-01')									AS GITargetEndDate 
	, ISNULL(NULLIF(VesselLifecycleStatus, 'n/a'), '_N/A')			AS VesselLifecycleStatus
	, CONVERT(BIT, CASE WHEN V.ManagementVisitScope = 'true' THEN 1 ELSE 0 END) AS ManagementVisitScope
	, ISNULL(CSRD, '_N/A')											AS CSRD
	, ISNULL(VMSType, '_N/A')										AS VMSType

FROM StagingGraphAPI.Vessels AS V

LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
		ON DOS.SharepointId = V.DemeOrganisationalStructureId

	LEFT JOIN DataStore1.DEMEHierarchy DH
		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId

	LEFT JOIN StagingDataMarket.VesselPassport_Vessel VPV
		ON V.VesselId = VPV.unitCode
		AND VPV.sourceSystem_ = 'AUTO'

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, V.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DS.DimDateId
	LEFT JOIN ETL.Date DE 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, V.QHSESendDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DE.DimDateId
````
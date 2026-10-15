# Source: `DBs/AzureSingleDB/DataStore2/Views/vwSupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwSupportingService.sql`
- SHA-256 of original file: `b64e62a444150d4de014b2b38f44efa8edd41c1ba558d37840960809927c56e6`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql








/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DataStore2].[vwSupportingService] AS 

SELECT
	  ISNULL(CONVERT(uniqueidentifier, SS.TIBCOIdentifier), '00000000-0000-0000-0000-000000000000')						AS TibcoIdentifier
    , SS.SupportingServiceCode
    , ISNULL(SupportingServiceId,'_N/A')																				AS SupportingServiceId
    , SS.SupportingServiceName	
	, ISNULL(DH.DEME , '_N/A')																							AS DEME
	, ISNULL(DH.ActivityLineId, '_N/A')																					AS ActivityLineId
	, ISNULL(DH.BusinessUnitId, '_N/A')																					AS BusinessUnitId            
    , ISNULL(DH.BusinessGroupId, '_N/A')																				AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')																						AS DivisionId
	, '_N/A'																											AS CountryId
    , ISNULL(Exclude, '_N/A')																							AS Exclude
    , ISNULL(QHSESCampaigns, '_N/A')																					AS QHSESCampaigns
	, ISNULL(QHSESCampaignTopic, '_N/A')																				AS QHSESCampaignTopic
	--, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, SS.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101') AS DimQHSESStartDateId
	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, SS.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'99990101')	AS DimQHSESEndDateId
	--, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, SS.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS QHSESStartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, ss.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS QHSESEndDate
	, CONVERT(BIT, 0)																									AS GIRequired
	, CONVERT(DATE, '1900-01-01')																						AS GITargetStartDate 
	, CONVERT(DATE, '1900-01-01')																						AS GITargetEndDate
	, ISNULL(CONVERT(DATE, SSDM.InactiveSince), '9999-01-01')															AS InactiveSince
	, ISNULL(SSDM.Managment, '_N/A')																					AS Management
	, ISNULL(SSDM.organsisedType00, '_N/A')																				AS OrganisedType
	, ISNULL(SSDM.Parent_, '_N/A')																						AS Parent
	, ISNULL(SSDM.SupportingService, '_N/A')																			AS SupportingServiceNameTibco
	, CONVERT(BIT,
	  CASE 
		WHEN SSDM.Abbreviation IS NULL
		THEN 0
		ELSE 1
	  END)																												AS InTibco
	,  CONVERT(BIT, CASE WHEN SS.InActiveSince IS NULL THEN 1 ELSE 0 END)												AS Active
		

FROM StagingGraphAPI.SupportingService SS		

	LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
		ON DOS.SharepointId = SS.DemeOrganisationalStructureId

	LEFT JOIN DataStore1.DEMEHierarchy DH
		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId

	LEFT JOIN StagingDataMarket.SupportingServices SSDM
		ON SS.TIBCOIdentifier = SSDM.tibcoidentifier

	--LEFT JOIN ETL.Date DSO 
	--	ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, SS.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DSO.DimDateId
	LEFT JOIN ETL.Date DEO 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, SS.QHSESendDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DEO.DimDateId

WHERE SS.SupportingServiceCode IS NOT NULL AND SS.SupportingServiceId IS NOT NULL AND SS.TIBCOIdentifier IS NOT NULL
````
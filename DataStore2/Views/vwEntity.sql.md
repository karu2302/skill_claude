# Source: `DBs/AzureSingleDB/DataStore2/Views/vwEntity.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwEntity.sql`
- SHA-256 of original file: `673747428b12f7e8aabf5a550cb692b0bc5fde598f94e4b7355e733c89c8b7ea`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql











/****** Object:  View [DataStore2].[vwOffice]    Script Date: 1/03/2022 10:36:49 ******/

CREATE VIEW [DataStore2].[vwEntity] AS
SELECT 
	--BUSINESS KEY
	  ISNULL(CONVERT(uniqueidentifier, EB.TibcoIdentifier), '00000000-0000-0000-0000-000000000000')						AS TibcoIdentifier
	, EB.SharepointId																									AS SharepointId
    , ISNULL(EB.EntityBranchId, '_N/A')																					AS EntityId
	  
	--FOREIGN KEYS
	, ISNULL(DH.DEME, '_N/A')																							AS DEME
	, ISNULL(DH.ActivityLineId, '_N/A')																					AS ActivityLineId
	, ISNULL(DH.BusinessUnitId, '_N/A')																					AS BusinessUnitId            
    , ISNULL(DH.BusinessGroupId, '_N/A')																				AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')																						AS DivisionId
	, ISNULL(C.CountryCode2		, '_N/A')																				AS CountryId
	--ATTRIBUTES
	, ISNULL(AddressLine1, '_N/A')																						AS AddressLine
	, ISNULL(CONVERT(NVARCHAR(50), PostalCode), '_N/A')																	AS PostalCode
   -- , ETL.F_QHSEConvertDecimal(Boundary)																				AS Boundary
    , ISNULL(EB.EntityBranchName, '_N/A')																				AS EntityName
   -- , ISNULL(EB.EntityBranchOldCode, '_N/A')																			AS EntityBranchOldCode
	, ISNULL(EntityType, '_N/A')																						AS EntityType
    , CONVERT(NVARCHAR(4000),ISNULL(REPLACE(REPLACE(REPLACE(EB.Exclude, '["',''),'","',', '), '"]',''), '_N/A'))	    AS Exclude
	, CONVERT(NVARCHAR(10), ISNULL(QHSEScampaigns, '_N/A'))																		AS QHSESCampaigns
	, CONVERT(NVARCHAR(4000), ISNULL(REPLACE(REPLACE(REPLACE(EB.QHSESCampaignTopic, '["',''),'","',', '), '"]',''), '_N/A'))	AS QHSESCampaignTopic
    , ISNULL(EB.Place, '_N/A')																							AS Place
	, ISNULL(DSEB.DimDateId,'19000101')																					AS DimQHSESEntityStartDateId
	, ISNULL(DEEB.DimDateId,'99990101')																					AS DimQHSESEntityEndDateId
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, EB.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))		AS QHSESEntityStartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, EB.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '9999-01-01'))		AS QHSESEntityEndDate
	--, ISNULL(CONVERT(NVARCHAR(10), Certified), '_N/A')																	AS Certified
	--, CONVERT(NVARCHAR(10), ISNULL(NULLIF(CertifiedByALocalNotifiedBody, 'NA'), '_N/A'))								AS CertifiedByALocalNotifiedBody
	, ISNULL(CompanyLegalForm, '_N/A')																					AS CompanyLegalForm
	, ISNULL(CompanyStatus, '_N/A')																						AS CompanyStatus
	--, ISNULL(Substatus, '_N/A')																							AS Substatus
	, CONVERT(NVARCHAR(10),ISNULL(GIDPBW, '_N/A'))																		AS GIDPBW
	--, ISNULL(ImpactConversionDetail, '_N/A')																			AS ImpactConversionDetail
	, CONVERT(NVARCHAR(10),
	  CASE 
		WHEN Lead = 'True' THEN 'Yes'
		ELSE 'No'
	  END)																												AS Lead
	--, ISNULL(Management, '_N/A')																						AS Management
	--, ISNULL(ManagementExternal, '_N/A')																				AS ManagementExternal
	--, CONVERT(NVARCHAR(10),ISNULL(PartOfDEMEIntegratedMS, '_N/A'))														AS PartOfDEMEIntegratedMS
	--, CONVERT(NVARCHAR(10),ISNULL(PartOfDEMEMultisiteContract, '_N/A'))													AS PartOfDEMEMultisiteContract
	, CONVERT(BIT, 0)																									AS GIRequired
	, CONVERT(DATE, '1900-01-01')																						AS GITargetStartDate 
	, CONVERT(DATE, '1900-01-01')																						AS GITargetEndDate
	, CONVERT(BIT, CASE WHEN EB.EntityBranchActive = 'True' THEN 1 ELSE 0 END)							                AS Active

FROM StagingGraphAPI.EntitiesBranches EB


	LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
		ON DOS.SharepointId = EB.DemeOrganisationalStructureId

	LEFT JOIN DataStore1.DEMEHierarchy DH
		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId

    LEFT JOIN DataStore1.Country AS C
       ON EB.CountryCodeAlpha3 = C.CountryCode3

-- Join with date to prevent dimdateId's not available in DimDate
	LEFT JOIN ETL.Date DSEB 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, EB.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DSEB.DimDateId
	LEFT JOIN ETL.Date DEEB 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, EB.QHSESendDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DEEB.DimDateId
````
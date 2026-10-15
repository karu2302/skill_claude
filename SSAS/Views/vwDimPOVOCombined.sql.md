# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql`
- SHA-256 of original file: `65df9e3119b1ff9f19ab4c21c0f591ddea05ac12b08cd28d42053a3989c6d702`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql




CREATE VIEW [SSAS].[vwDimPOVOCombined] AS 

SELECT
      COALESCE('P_'+CONVERT(NVARCHAR(10),P.DimProjectId),          'O_'+CONVERT(NVARCHAR(10),E.DimEntityId),                  'V_'+CONVERT(NVARCHAR(10),V.DimVesselId),          'OS_'+CONVERT(NVARCHAR(10),OS.DimOtherSiteId), 'SS_'+CONVERT(NVARCHAR(10),SS.DimSupportingServiceId))      AS DimPOVOId
    , COALESCE(P.DimProjectId, -2)				AS DimProjectId
    , COALESCE(E.DimEntityId, -2)				AS DimEntityId  
    , COALESCE(V.DimVesselId, -2)				AS DimVesselId  
    , COALESCE(OS.DimOtherSiteId, -2)			AS DimOtherSiteId
	, COALESCE(SS.DimSupportingServiceId, -2)	AS DimSupportingServiceId
    , CONCAT(ISNULL(P.DimProjectId,-1),'_',ISNULL(E.DimEntityId,-1),'_',ISNULL(V.DimVesselId,-1),'_',ISNULL(OS.DimOtherSiteId,-1),'_',ISNULL(SS.DimSupportingServiceId,-1)) AS ConcatPOVO                                                                       
    , COALESCE(P.DimDEMEHierarchyId,    E.DimDEMEHierarchyId,           V.DimDEMEHierarchyId,   OS.DimDEMEHierarchyId,	SS.DimDEMEHierarchyId)  AS DimPOVODEMEHierarchyId
    , COALESCE(P.ProjectId,             E.EntityId,                     V.VesselId,             OS.OtherSiteId,		SS.SupportingServiceCode)         AS POVOId
    , COALESCE(P.ProjectName,           E.EntityName,                   V.VesselName,           OS.OtherSiteName,	SS.SupportingServiceName)       AS POVOName
	, COALESCE(P.QHSEStartDate,    E.QHSESEntityStartDate,    V.QHSESStartDate,  OS.QHSESStartDate,		'1900-01-01' ) AS POVOStartDate
	, COALESCE(P.QHSESEndDate,     E.QHSESEntityEndDate,      V.QHSESEndDate,    OS.QHSESEndDate,		SS.QHSESEndDate)   AS POVOEndDate
    , COALESCE(P.Exclude,               E.Exclude,                      V.Exclude,              OS.Exclude,			SS.Exclude)             AS POVOExclude
    , COALESCE(P.QHSESCampaigns,        E.QHSESCampaigns, V.QHSESCampaign ,OS.QHSESCampaigns, SS.QHSESCampaigns)      AS POVOQHSESCampaigns
	, COALESCE(P.QHSESCampaignTopic,        E.QHSESCampaignTopic, V.QHSESCampaignTopic ,OS.QHSESCampaignTopic, SS.QHSESCampaignTopic)      AS POVOQHSESCampaignTopic
    , CONCAT(COALESCE(P.ProjectId,E.EntityId,V.VesselId,OS.OtherSiteId, SS.SupportingServiceCode), ' - ', COALESCE(P.ProjectName,E.EntityName,V.VesselName,OS.OtherSiteName,SS.SupportingServiceName)) AS POVOId_Name
    , CASE
        WHEN P.DimProjectId     IS NOT NULL THEN 'Project'
        WHEN E.DimEntityId      IS NOT NULL THEN 'Entity'
        WHEN V.DimVesselId      IS NOT NULL THEN 'Vessel'
        WHEN OS.DimOtherSiteId  IS NOT NULL THEN 'Other Site'
		WHEN SS.DimSupportingServiceId  IS NOT NULL THEN 'Supporting Service'END POVOType
	, COALESCE(P.GIRequired,    E.GIRequired,    V.GIRequired,  OS.GIRequired, SS.GIRequired) AS GIRequired
	, COALESCE(P.GITargetStartDate,    E.GITargetStartDate,    V.GITargetStartDate,  OS.GITargetStartDate, SS.GITargetStartDate) AS GITargetStartDate
	, COALESCE(P.GITargetEndDate,    E.GITargetEndDate,    V.GITargetEndDate,  OS.GITargetEndDate, SS.GITargetEndDate) AS GITargetEndDate
	, CONVERT(BIT,
	  CASE 
		WHEN P.ProjectId LIKE 'MR%' OR P.ProjectId LIKE 'M6%' OR p.ProjectId LIKE 'IR%' OR P.ProjectId like 'FIT%'
		THEN 1
		ELSE 0
	  END	)														AS MR
	, COALESCE(SS.InactiveSince, '1900-01-01')						AS InactiveSince
	, CONVERT(BIT,
	  CASE 
		WHEN P.DimProjectId     IS NOT NULL THEN P.JointVenture
		
		ELSE 0
	  END	)														AS JointVenture
FROM DWH.DimProject P
    FULL OUTER JOIN DWH.DimEntity E
        ON 0 = 1
    FULL OUTER JOIN DWH.DimVessel V
        ON 0 = 1 
    FULL OUTER JOIN DWH.DimOtherSite OS
        ON 0 = 1 
	FULL OUTER JOIN DWH.DimSupportingService SS
		ON 0 = 1
````
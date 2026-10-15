# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombinedEE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombinedEE.sql`
- SHA-256 of original file: `50b90593a6f4d43caee2a68687628e8b7bc867bac2ffecf9ba5b332b48c7bb70`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql



CREATE VIEW [SSAS].[vwDimPOVOCombinedEE] AS 

SELECT
      COALESCE('P_'+CONVERT(NVARCHAR(10),P.DimProjectId),          'O_'+CONVERT(NVARCHAR(10),E.DimEntityId),                  'V_'+CONVERT(NVARCHAR(10),V.DimVesselId),          'OS_'+CONVERT(NVARCHAR(10),OS.DimOtherSiteId))      AS DimPOVOId
    , COALESCE(P.DimProjectId, -2)				AS DimProjectId
    , COALESCE(E.DimEntityId, -2)				AS DimEntityId  
    , COALESCE(V.DimVesselId, -2)				AS DimVesselId  
    , COALESCE(OS.DimOtherSiteId, -2)			AS DimOtherSiteId
    , CONCAT(ISNULL(P.DimProjectId,-1),'_',ISNULL(E.DimEntityId,-1),'_',ISNULL(V.DimVesselId,-1),'_',ISNULL(OS.DimOtherSiteId,-1)) AS ConcatPOVO                                                                       
    , COALESCE(P.DimDEMEHierarchyId,    E.DimDEMEHierarchyId,           V.DimDEMEHierarchyId,   OS.DimDEMEHierarchyId)  AS DimPOVODEMEHierarchyId
    , COALESCE(P.ProjectId,             E.EntityId,                     V.VesselId,             OS.OtherSiteId)         AS POVOId
    , COALESCE(P.ProjectName,           E.EntityName,                   V.VesselName,           OS.OtherSiteName)       AS POVOName
	, COALESCE(P.QHSEStartDate,    E.QHSESEntityStartDate,    V.QHSESStartDate,  OS.QHSESStartDate) AS POVOStartDate
	, COALESCE(P.QHSESEndDate,     E.QHSESEntityEndDate,      V.QHSESEndDate,    OS.QHSESEndDate)   AS POVOEndDate
    , COALESCE(P.Exclude,               E.Exclude,                      V.Exclude,              OS.Exclude)             AS POVOExclude
    , COALESCE(P.QHSESCampaigns,        E.QHSESCampaigns, V.QHSESCampaign ,OS.QHSESCampaigns)      AS POVOQHSESCampaigns
	, COALESCE(P.QHSESCampaignTopic,        E.QHSESCampaignTopic, V.QHSESCampaignTopic ,OS.QHSESCampaignTopic)      AS POVOQHSESCampaignTopic
    , CONCAT(COALESCE(P.ProjectId,E.EntityId,V.VesselId,OS.OtherSiteId), ' - ', COALESCE(P.ProjectName,E.EntityName,V.VesselName,OS.OtherSiteName)) AS POVOId_Name
    , CASE
        WHEN P.DimProjectId     IS NOT NULL THEN 'Project'
        WHEN E.DimEntityId      IS NOT NULL THEN 'Entity'
        WHEN V.DimVesselId      IS NOT NULL THEN 'Vessel'
        WHEN OS.DimOtherSiteId  IS NOT NULL THEN 'Other Site'
	  END POVOType
	, COALESCE(P.GIRequired,    E.GIRequired,    V.GIRequired,  OS.GIRequired) AS GIRequired
	, COALESCE(P.GITargetStartDate,    E.GITargetStartDate,    V.GITargetStartDate,  OS.GITargetStartDate) AS GITargetStartDate
	, COALESCE(P.GITargetEndDate,    E.GITargetEndDate,    V.GITargetEndDate,  OS.GITargetEndDate) AS GITargetEndDate
	, CONVERT(BIT,
	  CASE 
		WHEN P.ProjectId LIKE 'MR%' OR P.ProjectId LIKE 'M6%' OR P.ProjectId like 'FIT%'
		THEN 1
		ELSE 0
	  END	)														AS MR
	, ISNULL(V.CSRD, '_N/A')										AS CSRD
	, ISNULL(V.VMSType, '_N/A')										AS VMSType
FROM DWH.DimProject P
    FULL OUTER JOIN DWH.DimEntity E
        ON 0 = 1
    FULL OUTER JOIN DWH.DimVessel V
        ON 0 = 1 
    FULL OUTER JOIN DWH.DimOtherSite OS
        ON 0 = 1
````
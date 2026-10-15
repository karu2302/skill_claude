# Source: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql`
- SHA-256 of original file: `e6c89210655bfaef3c34939afe247204bb681cafbc8e77e9cc81bd606dc7c0b5`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql








CREATE VIEW [SSAS].[vwBridgePOVOFactsQHSE] AS

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactEvent

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactIncident

UNION

SELECT 
--      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', '-1','_', '-1','_', '-1', '_','-1') AS ConcatPOVOLocation
--    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId) AS ConcatPOVO
--    , CONCAT('-1','_', '-1','_', '-1', '_','-1') AS ConcatLocation
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactWorkingHour

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactObservation

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactInspection

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactGreenInitiative

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', '-1','_', '-1','_', '-1', '_','-1') AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT('-1','_', '-1','_', '-1', '_','-1') AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , -1 AS DimProjectLocationId
    , -1 AS DimOfficeLocationId
    , -1 AS DimVesselLocationId
    , -1 AS DimOtherSiteLocationId
FROM DWH.FactAction

UNION

SELECT 
--      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', '-1','_', '-1','_', '-1', '_','-1') AS ConcatPOVOLocation
--    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId) AS ConcatPOVO
--    , CONCAT('-1','_', '-1','_', '-1', '_','-1') AS ConcatLocation
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactPOVOSpecificData

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactAuditTarget

UNION

SELECT 
      CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimSupportingServiceId,'_', DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
    , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId, '_', DimSupportingServiceId) AS ConcatPOVO
    , CONCAT(DimProjectLocationId,'_', DimEntityLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
    , DimProjectId
    , DimEntityId
    , DimVesselId
    , DimOtherSiteId
	, DimSupportingServiceId
    , DimProjectLocationId
    , DimEntityLocationId
    , DimVesselLocationId
    , DimOtherSiteLocationId
FROM DWH.FactSuccessStory

-- UNION

-- SELECT
--       CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId,'_', DimProjectLocationId,'_', DimOfficeLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatPOVOLocation
--     , CONCAT(DimProjectId,'_',DimEntityId,'_',DimVesselId,'_',DimOtherSiteId) AS ConcatPOVO
--     , CONCAT(DimProjectLocationId,'_', DimOfficeLocationId,'_', DimVesselLocationId,'_', DimOtherSiteLocationId) AS ConcatLocation
--     , DimProjectId
--     , DimEntityId
--     , DimVesselId
--     , DimOtherSiteId
--     , DimProjectLocationId
--     , DimOfficeLocationId
--     , DimVesselLocationId
--     , DimOtherSiteLocationId
-- FROM (  SELECT
--               COALESCE(O.DimEntityId, OL.DimEntityId, -1)                  AS DimEntityId
--             , COALESCE(OS.DimOtherSiteId, OSL.DimOtherSiteId, -1)             AS DimOtherSiteId
--             , COALESCE(P.DimProjectId,PL.DimProjectId, -1)                 AS DimProjectId
--             , COALESCE(V.DimVesselId, VL.DimVesselId,-1)                  AS DimVesselId
--             , ISNULL(PL.DimProjectLocationId, -1)       AS DimProjectLocationId
--             , ISNULL(OL.DimOfficeLocationId, -1)        AS DimOfficeLocationId
--             , ISNULL(VL.DimVesselLocationId, -1)        AS DimVesselLocationId
--             , ISNULL(OSL.DimOtherSiteLocationId, -1)    AS DimOtherSiteLocationId
--         FROM DWH.DimProject P
--             FULL OUTER JOIN DWH.DimOffice O
--                 ON 0 = 1
--             FULL OUTER JOIN DWH.DimVessel V
--                 ON 0 = 1 
--             FULL OUTER JOIN DWH.DimOtherSite OS
--                 ON 0 = 1 
--             FULL OUTER JOIN DWH.DimProjectLocation PL
--                 ON 0 = 1
--             FULL OUTER JOIN DWH.DimOfficeLocation OL
--                 ON 0 = 1
--             FULL OUTER JOIN DWH.DimVesselLocation VL
--                 ON 0 = 1
--             FULL OUTER JOIN DWH.DimOtherSiteLocation OSL
--                 ON 0 = 1 ) AS POVOLocation
````
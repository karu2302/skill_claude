# Source: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql`
- SHA-256 of original file: `ee3509f181b1c60d689106e073ee8def1160f419c01127eb3672c5e0b2ab6da8`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql






CREATE VIEW [SSAS].[vwBridgePOVOLocationFactsQHSE] AS

SELECT
      B.ConcatPOVO
    , B.ConcatPOVOLocation
    , B.ConcatLocation
FROM (  SELECT DISTINCT
              ConcatPOVOFacts AS ConcatPOVO
            , ConcatPOVOLocation
            , CASE
                WHEN ConcatLocation = '-1_-1_-1_-1' THEN NULL
                WHEN [value] = DimProjectLocationId AND DimProjectId <> -1 THEN CONCAT(SS.[value],'_-1_-1_-1')
                WHEN [value] = DimEntityLocationId AND DimEntityId <> -1 THEN CONCAT('-1_',SS.[value],'_-1_-1')
                WHEN [value] = DimVesselLocationId AND DimVesselId <> -1  THEN CONCAT('-1_-1_',SS.[value],'_-1')
                WHEN [value] = DimOtherSiteLocationId AND DimOtherSiteId <> -1  THEN CONCAT('-1_-1_-1_',SS.[value])
                -- ELSE '-1'
              END ConcatLocation
            , ConcatLocation AS ConcatLocationOrgin
        FROM (  SELECT
                      P.DimProjectId
                    , P.DimEntityId
                    , P.DimVesselId
                    , P.DimOtherSiteId
                    , P.ConcatPOVOFacts
                    , F.ConcatLocation
                    , F.ConcatPOVOLocation
                    , F.DimProjectLocationId
                    , F.DimEntityLocationId
                    , F.DimVesselLocationId
                    , F.DimOtherSiteLocationId
                FROM SSAS.vwBridgePOVOQHSE P
                    LEFT JOIN SSAS.vwBridgePOVOFactsQHSE F
                        ON P.ConcatPOVOFacts = F.ConcatPOVO ) B
            CROSS APPLY string_split(ConcatLocation, '_') SS
        WHERE [value] <> -1 OR ConcatLocation = '-1_-1_-1_-1' ) B
-- WHERE B.ConcatLocation <> '-1'     
````
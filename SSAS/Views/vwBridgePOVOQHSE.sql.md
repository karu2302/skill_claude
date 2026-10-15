# Source: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql`
- SHA-256 of original file: `cc8800f78ca0d8a5b60465eb9dc86e12b34a321d4ce5c5cfc5f407675c69ba91`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







CREATE VIEW [SSAS].[vwBridgePOVOQHSE] AS
SELECT DISTINCT
      CASE
        WHEN ordinal = 1 THEN CONCAT(SS.[value],'_-1_-1_-1_-1')
        WHEN ordinal = 2 THEN CONCAT('-1_',SS.[value],'_-1_-1_-1')
        WHEN ordinal = 3 THEN CONCAT('-1_-1_',SS.[value],'_-1_-1')
        WHEN ordinal = 4 THEN CONCAT('-1_-1_-1_',SS.[value], '_-1')
		WHEN ordinal = 5 THEN CONCAT('-1_-1_-1_-1_',SS.[value])
      END ConcatPOVO
    , IIF(ordinal = 1, DimProjectId, -1) AS DimProjectId
    , IIF(ordinal = 2, DimEntityId, -1) AS DimEntityId
    , IIF(ordinal = 3, DimVesselId, -1) AS DimVesselId
    , IIF(ordinal = 4, DimOtherSiteId, -1) AS DimOtherSiteId
	, IIF(ordinal = 5, DimSupportingServiceId, -1) AS DimSupportingServiceId
    
    , ConcatPOVO AS ConcatPOVOFacts
FROM (  SELECT 

              ConcatPOVO
            , DimProjectId
            , DimEntityId
            , DimVesselId
            , DimOtherSiteId
			, DimSupportingServiceId
        FROM SSAS.vwBridgePOVOFactsQHSE
	) BF
    CROSS APPLY string_split(ConcatPOVO,'_', 1) SS
WHERE [value] <> -1 OR ConcatPOVO = '-1_-1_-1_-1_-1'
````
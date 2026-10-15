# Source: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql`
- SHA-256 of original file: `4658a92b9ec12c05a458b615e8284a212fdff7362a9ebc1efac5f9f8cfcf3cbd`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE VIEW SSAS.vwBridgePOVOQHSESCampaignTopic AS
SELECT 
	  ConcatPOVO
	, DimQHSESCampaignTopicId

FROM SSAS.vwDimPOVOCombined

CROSS APPLY string_split(POVOQHSESCampaignTopic, ',') SS

LEFT JOIN DWH.DimQHSESCampaignTopic C
	ON C.CampaignTopic = TRIM(SS.value)
````
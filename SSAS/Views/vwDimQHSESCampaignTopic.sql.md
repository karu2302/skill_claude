# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql`
- SHA-256 of original file: `145550d4b8617de27adbe8839d9db3776a2295ab29b36e97199a206226eebb64`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE VIEW SSAS.vwDimQHSESCampaignTopic AS
SELECT 
	  DimQHSESCampaignTopicId
    , CampaignTopic

FROM DWH.DimQHSESCampaignTopic
````
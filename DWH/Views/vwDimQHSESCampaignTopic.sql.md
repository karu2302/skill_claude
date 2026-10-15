# Source: `DBs/AzureSingleDB/DWH/Views/vwDimQHSESCampaignTopic.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimQHSESCampaignTopic.sql`
- SHA-256 of original file: `35eec69f975c31b42efb12db8d5ecc4d1f00f7755b920064ec9115ee5cdd9387`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE VIEW DWH.vwDimQHSESCampaignTopic AS 
SELECT 
	   CampaignTopic

FROM DataStore1.QHSESCampaignTopic
````
# Source: `DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql`
- SHA-256 of original file: `bf237d47ea692b6a93e2909040b61459f19650567809ab1aa1b56ba394b80135`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql



CREATE VIEW [DataStore1].[vwQHSESCampaignTopic] AS 
SELECT DISTINCT
	  ISNULL(Title, '_N/A') AS CampaignTopic

FROM StagingGraphAPI.QHSESCampaignTopics
WHERE EventTopic = 'True'
````
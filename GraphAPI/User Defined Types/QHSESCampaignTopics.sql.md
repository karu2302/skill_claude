# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/QHSESCampaignTopics.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/QHSESCampaignTopics.sql`
- SHA-256 of original file: `cd37719ce6c94effc09474491f68dfeb11f0bdebd022d19b5fa4e42f6c86f8bd`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[QHSESCampaignTopics] AS TABLE (
    [EventTopic] NVARCHAR (255) NULL,
    [Title]      NVARCHAR (255) NULL);




````
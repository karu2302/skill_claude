# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql`
- SHA-256 of original file: `b3d47af5d0af55b8c468af43790e0aeba998c7df28cefa8ab7f595750d5a203a`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[QHSESCampaignTopics] (
    [EventTopic] NVARCHAR (255) NULL,
    [Title]      NVARCHAR (255) NULL
);




GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Title', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'QHSESCampaignTopics', @level2type = N'COLUMN', @level2name = N'Title';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EventTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'QHSESCampaignTopics', @level2type = N'COLUMN', @level2name = N'EventTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_Publication', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'QHSESCampaignTopics';


````
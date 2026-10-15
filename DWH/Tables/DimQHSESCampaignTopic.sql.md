# Source: `DBs/AzureSingleDB/DWH/Tables/DimQHSESCampaignTopic.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimQHSESCampaignTopic.sql`
- SHA-256 of original file: `5d01bb6d412766eeadba35495a20c7ad09da21571eeaf59e9c6ddc0430230170`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimQHSESCampaignTopic] (
    [DimQHSESCampaignTopicId] INT            IDENTITY (1, 1) NOT NULL,
    [CampaignTopic]           NVARCHAR (255) NOT NULL,
    [CreatedETLRunId]         INT            NOT NULL,
    [ModifiedETLRunId]        INT            NULL,
    CONSTRAINT [PK_DWH_DimQHSESCampaignTopic] PRIMARY KEY CLUSTERED ([DimQHSESCampaignTopicId] ASC)
);


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimQHSESCampaignTopic]
    ON [DWH].[DimQHSESCampaignTopic]([CampaignTopic] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimQHSESCampaignTopic', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimQHSESCampaignTopic', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimQHSESCampaignTopic', @level2type = N'COLUMN', @level2name = N'CampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimQHSESCampaignTopic', @level2type = N'COLUMN', @level2name = N'DimQHSESCampaignTopicId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimQHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimQHSESCampaignTopic';


````
# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/OtherSites.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/OtherSites.sql`
- SHA-256 of original file: `d2f61b147e9faa209b66ea3bebb0b997ae0e5860e0be6c4c2e41abee8b654d7e`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[OtherSites] (
    [CountryId]                     NVARCHAR (10)   NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [Exclude]                       NVARCHAR (255)  NULL,
    [OtherSiteId]                   NVARCHAR (255)  NULL,
    [OtherSiteName]                 NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [SharepointId]                  INT             NULL
);










GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SharepointId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'SharepointId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESStartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaigns', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'OtherSiteName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'OtherSiteId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'OtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Exclude', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CountryId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'CountryId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_OtherSites', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'OtherSites', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


````
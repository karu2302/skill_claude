# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/EntitiesBranches.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/EntitiesBranches.sql`
- SHA-256 of original file: `774e6d8b2439f6f77a88b60b9f1b900cd30f65090e2208b71da05ed2594c85f7`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[EntitiesBranches] (
    [AddressLine1]                  NVARCHAR (255)  NULL,
    [CompanyLegalForm]              NVARCHAR (255)  NULL,
    [CompanyStatus]                 NVARCHAR (255)  NULL,
    [CountryCodeAlpha3]             NVARCHAR (255)  NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [EntityBranchActive]            NVARCHAR (255)  NULL,
    [EntityBranchId]                NVARCHAR (255)  NULL,
    [EntityBranchName]              NVARCHAR (255)  NULL,
    [EntityType]                    NVARCHAR (255)  NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [GIDPBW]                        NVARCHAR (255)  NULL,
    [Lead]                          NVARCHAR (255)  NULL,
    [Place]                         NVARCHAR (255)  NULL,
    [PostalCode]                    NVARCHAR (255)  NULL,
    [QHSEScampaigns]                NVARCHAR (255)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [SharepointId]                  INT             NULL,
    [TibcoIdentifier]               NVARCHAR (255)  NULL
);
















GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SharepointId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'SharepointId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESStartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PostalCode', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'PostalCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Place', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'Place';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityBranchId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'Exclude';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityBranchName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'EntityBranchName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityBranchId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'EntityBranchId';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'AddressLine1', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'AddressLine1';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_EntitiesBranches', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TibcoIdentifier', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'TibcoIdentifier';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSEScampaigns', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'QHSEScampaigns';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Lead', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'Lead';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'GIDPBW', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'GIDPBW';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityType', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'EntityType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CountryCodeAlpha3', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'CountryCodeAlpha3';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CompanyStatus', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'CompanyStatus';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CompanyLegalForm', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'CompanyLegalForm';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityBranchActive', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'EntitiesBranches', @level2type = N'COLUMN', @level2name = N'EntityBranchActive';


````
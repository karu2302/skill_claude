# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/SupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/SupportingService.sql`
- SHA-256 of original file: `de84a8abec58ae636d9557bffe5eac2ac8fb38fb8f3df536ff6c59fc0728c1cd`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[SupportingService] (
    [DemeOrganisationalStructureId] NVARCHAR (10)  NULL,
    [Exclude]                       NVARCHAR (10)  NULL,
    [InactiveSince]                 NVARCHAR (255) NULL,
    [QHSESCampaigns]                NVARCHAR (10)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (MAX) NULL,
    [QHSESEndDate]                  NVARCHAR (255) NULL,
    [SharepointId]                  INT            NULL,
    [SupportingServiceCode]         NVARCHAR (255) NULL,
    [SupportingServiceId]           NVARCHAR (10)  NULL,
    [SupportingServiceName]         NVARCHAR (255) NULL,
    [TIBCOIdentifier]               NVARCHAR (255) NULL
);














GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingServiceName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingServiceId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingServiceCode', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SharepointId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'SharepointId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaigns', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingServiceId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'Exclude';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_SupportingService', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InactiveSince', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'InactiveSince';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TIBCOIdentifier', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'SupportingService', @level2type = N'COLUMN', @level2name = N'TIBCOIdentifier';


````
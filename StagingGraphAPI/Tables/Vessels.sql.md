# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/Vessels.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/Vessels.sql`
- SHA-256 of original file: `d39df2f22d442e9507c643a0a6bab2ca8fff867727291f876ef918f2a091079c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[Vessels] (
    [ClassificationSociety]         NVARCHAR (255)  NULL,
    [CSRD]                          NVARCHAR (255)  NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [FuelType]                      NVARCHAR (255)  NULL,
    [GT]                            NVARCHAR (255)  NULL,
    [ISM]                           NVARCHAR (255)  NULL,
    [ManagementVisitScope]          NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (255)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [RMPE]                          NVARCHAR (255)  NULL,
    [VesselActive]                  NVARCHAR (10)   NULL,
    [VesselId]                      NVARCHAR (255)  NULL,
    [VesselLifecycleStatus]         NVARCHAR (255)  NULL,
    [VesselName]                    NVARCHAR (255)  NULL,
    [VesselUnitName]                NVARCHAR (255)  NULL,
    [VMSType]                       NVARCHAR (255)  NULL
);
















GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselUnitName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VesselUnitName';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselLifecycleStatus', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VesselLifecycleStatus';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VesselId';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselActive', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VesselActive';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'RMPE', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'RMPE';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESStartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaigns', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ISM', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'ISM';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'GT', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'GT';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'FuelType', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'FuelType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Exclude', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ClassificationSociety', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'ClassificationSociety';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_Vessels', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ManagementVisitScope', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'ManagementVisitScope';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VMSType', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'VMSType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CSRD', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'Vessels', @level2type = N'COLUMN', @level2name = N'CSRD';


````
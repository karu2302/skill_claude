# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/ProjectsAX.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/ProjectsAX.sql`
- SHA-256 of original file: `cb5d293b62882127c0e44db87c56ad706453627b575b9d1b05077b5e9b9f2e91`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[ProjectsAX] (
    [BudgetClosed]                  NVARCHAR (255)  NULL,
    [BudgetEuro]                    NVARCHAR (255)  NULL,
    [Country]                       NVARCHAR (10)   NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [DEMETurnover]                  NVARCHAR (255)  NULL,
    [EndDate]                       NVARCHAR (50)   NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [ImpactConversionProjectNumber] NVARCHAR (255)  NULL,
    [JointVenture]                  NVARCHAR (10)   NULL,
    [ProjectId]                     NVARCHAR (255)  NULL,
    [ProjectName]                   NVARCHAR (255)  NULL,
    [ProjectTitle]                  NVARCHAR (255)  NULL,
    [ProjectWithC02]                NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESendDate]                  NVARCHAR (255)  NULL,
    [QHSEStartDate]                 NVARCHAR (255)  NULL,
    [QHSEStatus]                    NVARCHAR (255)  NULL,
    [StartDate]                     NVARCHAR (255)  NULL
);










GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'StartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'StartDate';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSEStatus', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'QHSEStatus';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSEStartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'QHSEStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESendDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'QHSESendDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaignTopic', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESCampaigns', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectWithC02', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'ProjectWithC02';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectTitle', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'ProjectTitle';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'ProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ImpactConversionProjectNumber', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'ImpactConversionProjectNumber';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Exclude', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'EndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DEMETurnover', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'DEMETurnover';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Country', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'Country';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'BudgetEuro', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'BudgetEuro';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'BudgetClosed', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'BudgetClosed';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_ProjectsAX', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'JointVenture', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'ProjectsAX', @level2type = N'COLUMN', @level2name = N'JointVenture';


````
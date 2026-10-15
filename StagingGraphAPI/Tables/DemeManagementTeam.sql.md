# Source: `DBs/AzureSingleDB/StagingGraphAPI/Tables/DemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingGraphAPI/Tables/DemeManagementTeam.sql`
- SHA-256 of original file: `0c51ee65b259507408e5314c716e357cd78def7f4a0eda94df32c0ed035ef240`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingGraphAPI].[DemeManagementTeam] (
    [ActiveMember]                  NVARCHAR (255) NULL,
    [Campus]                        NVARCHAR (255) NULL,
    [CDWE]                          NVARCHAR (255) NULL,
    [Country]                       NVARCHAR (255) NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)  NULL,
    [Email]                         NVARCHAR (255) NULL,
    [FullName]                      NVARCHAR (255) NULL,
    [QHSESEndDate]                  NVARCHAR (255) NULL,
    [QHSESStartDate]                NVARCHAR (255) NULL,
    [Senior]                        NVARCHAR (255) NULL,
    [SupportingService]             NVARCHAR (255) NULL,
    [TargetQHSESVisit]              NVARCHAR (255) NULL,
    [TargetVesselVisit]             NVARCHAR (255) NULL
);










GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TargetVesselVisit', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'TargetVesselVisit';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TargetQHSESVisit', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'TargetQHSESVisit';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingService', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'SupportingService';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Senior', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Senior';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESStartDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEndDate', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'FullName', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'FullName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Email', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Email';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Country', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Country';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ActiveMember', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'ActiveMember';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LST_DemeManagementTeam', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DemeOrganisationalStructureId', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'DemeOrganisationalStructureId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CDWE', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'CDWE';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Campus', @level0type = N'SCHEMA', @level0name = N'StagingGraphAPI', @level1type = N'TABLE', @level1name = N'DemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Campus';


````
# Source: `DBs/AzureSingleDB/StagingImpact/Tables/GreenInitiative.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingImpact/Tables/GreenInitiative.sql`
- SHA-256 of original file: `1cceb62ad369d0b008e79cfaed6f492ecf4f37086b376e66fffc5f7d5f62ac33`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingImpact].[GreenInitiative] (
    [Date]                  NVARCHAR (255) NULL,
    [GreenInitiativeId]     NVARCHAR (255) NULL,
    [PlanCategory]          NVARCHAR (255) NULL,
    [Project]               NVARCHAR (255) NULL,
    [ResponsibleDepartment] NVARCHAR (255) NULL,
    [StatusId]              INT            NULL,
    [Vessel]                NVARCHAR (255) NULL
);




GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Vessel', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'Vessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Status', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'StatusId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ResponsibleDepartment', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'ResponsibleDepartment';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Project', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'Project';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PlanCategory', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'PlanCategory';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEventID', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'GreenInitiativeId';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Date', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative', @level2type = N'COLUMN', @level2name = N'Date';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'GreenInitiative', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'GreenInitiative';


````
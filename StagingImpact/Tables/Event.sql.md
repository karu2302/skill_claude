# Source: `DBs/AzureSingleDB/StagingImpact/Tables/Event.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingImpact/Tables/Event.sql`
- SHA-256 of original file: `dc31b907e261dc9483a09369c7c0c2976b8cedb64d2a076ecf5902e907827f10`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingImpact].[Event] (
    [Date]                  NVARCHAR (255) NULL,
    [EventType]             NVARCHAR (255) NULL,
    [Project]               NVARCHAR (255) NULL,
    [QHSESEventID]          NVARCHAR (255) NULL,
    [ResponsibleDepartment] NVARCHAR (255) NULL,
    [StatusId]              INT            NULL,
    [TotalParticipants]     INT            NULL,
    [Vessel]                NVARCHAR (255) NULL
);




GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Vessel', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'Vessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TotalParticipants', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'TotalParticipants';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Status', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'StatusId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ResponsibleDepartment', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'ResponsibleDepartment';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESEventID', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'QHSESEventID';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Project', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'Project';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EventType', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'EventType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Date', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event', @level2type = N'COLUMN', @level2name = N'Date';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Event', @level0type = N'SCHEMA', @level0name = N'StagingImpact', @level1type = N'TABLE', @level1name = N'Event';


````
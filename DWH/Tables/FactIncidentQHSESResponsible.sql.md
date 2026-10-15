# Source: `DBs/AzureSingleDB/DWH/Tables/FactIncidentQHSESResponsible.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactIncidentQHSESResponsible.sql`
- SHA-256 of original file: `acd54644a25fef7f2118b93eff4ab7d72d1107713be1cc1e762d9a161878a91c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[FactIncidentQHSESResponsible] (
    [FactIncidentQHSESResponsibleId] INT            IDENTITY (1, 1) NOT NULL,
    [FactIncidentId]                 INT            NOT NULL,
    [Name]                           NVARCHAR (255) NOT NULL,
    [Role]                           VARCHAR (30)   NOT NULL,
    [CreatedETLRunId]                INT            NOT NULL,
    [ModifiedETLRunId]               INT            NULL,
    CONSTRAINT [PK_DWH_FactIncidentQHSESResponsible] PRIMARY KEY CLUSTERED ([FactIncidentQHSESResponsibleId] ASC)
);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'Role';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'Name';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'FactIncidentId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible', @level2type = N'COLUMN', @level2name = N'FactIncidentQHSESResponsibleId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactIncidentQHSESResponsible', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentQHSESResponsible';


````
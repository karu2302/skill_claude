# Source: `DBs/AzureSingleDB/DWH/Tables/FactDemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactDemeManagementTeam.sql`
- SHA-256 of original file: `1bca558e2f43eab614bccb3eecba31dcd3ffc9806887bcd9b8b572a08a9f974f`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[FactDemeManagementTeam] (
    [FactDemeManagementTeamId] INT            IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId]       INT            NOT NULL,
    [Email]                    NVARCHAR (255) NULL,
    [FullName]                 NVARCHAR (255) NULL,
    [DEME]                     NVARCHAR (32)  NOT NULL,
    [ActivityLineId]           NVARCHAR (32)  NOT NULL,
    [BusinessGroupId]          NVARCHAR (32)  NOT NULL,
    [BusinessUnitId]           NVARCHAR (32)  NOT NULL,
    [DivisionId]               NVARCHAR (32)  NOT NULL,
    [CountryId]                NVARCHAR (10)  NOT NULL,
    [QHSESEndDate]             DATETIME       NULL,
    [QHSESStartDate]           DATETIME       NULL,
    [SupportingService]        NVARCHAR (255) NOT NULL,
    [TargetQHSESVisit]         INT            NULL,
    [TargetVesselVisit]        INT            NULL,
    [Senior]                   BIT            NULL,
    [ActiveMember]             BIT            NULL,
    [CDWE]                     BIT            NULL,
    [Campus]                   BIT            NULL,
    [CreatedETLRunId]          INT            NOT NULL,
    [ModifiedETLRunId]         INT            NULL,
    CONSTRAINT [PK_DWH_FactDemeManagementTeam] PRIMARY KEY CLUSTERED ([FactDemeManagementTeamId] ASC),
    CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId])
);


GO
ALTER TABLE [DWH].[FactDemeManagementTeam] NOCHECK CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[FactDemeManagementTeam] NOCHECK CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[FactDemeManagementTeam] NOCHECK CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[FactDemeManagementTeam] NOCHECK CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[FactDemeManagementTeam] NOCHECK CONSTRAINT [FK_DWH_FactDemeManagementTeam_DimDEMEHierarchyId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'ActiveMember';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Senior';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'TargetVesselVisit';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'TargetQHSESVisit';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'SupportingService';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'CountryId';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'BusinessGroupId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'ActivityLineId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'FullName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Email';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'FactDemeManagementTeamId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactDemeMT', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'DivisionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'BusinessUnitId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'DEME';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'CDWE';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactDemeManagementTeam', @level2type = N'COLUMN', @level2name = N'Campus';


````
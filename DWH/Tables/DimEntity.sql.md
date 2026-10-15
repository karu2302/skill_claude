# Source: `DBs/AzureSingleDB/DWH/Tables/DimEntity.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimEntity.sql`
- SHA-256 of original file: `c85e6b2831a28fcf587278a725c746fe41ec0d7d108cb4f16d1ba85e145dffd3`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimEntity] (
    [DimEntityId]               INT              IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId]        INT              NOT NULL,
    [TibcoIdentifier]           UNIQUEIDENTIFIER NOT NULL,
    [EntityId]                  NVARCHAR (255)   NOT NULL,
    [AddressLine]               NVARCHAR (255)   NOT NULL,
    [PostalCode]                NVARCHAR (50)    NOT NULL,
    [EntityName]                NVARCHAR (255)   NOT NULL,
    [EntityType]                NVARCHAR (255)   NOT NULL,
    [Exclude]                   NVARCHAR (4000)  NULL,
    [QHSESCampaigns]            NVARCHAR (10)    NULL,
    [QHSESCampaignTopic]        NVARCHAR (4000)  NULL,
    [Place]                     NVARCHAR (255)   NOT NULL,
    [DimQHSESEntityStartDateId] INT              NOT NULL,
    [DimQHSESEntityEndDateId]   INT              NOT NULL,
    [QHSESEntityStartDate]      DATE             NULL,
    [QHSESEntityEndDate]        DATE             NULL,
    [CompanyLegalForm]          NVARCHAR (255)   NOT NULL,
    [CompanyStatus]             NVARCHAR (255)   NOT NULL,
    [GIDPBW]                    NVARCHAR (10)    NULL,
    [Lead]                      NVARCHAR (10)    NULL,
    [GIRequired]                BIT              NULL,
    [GITargetEndDate]           DATE             NULL,
    [GITargetStartDate]         DATE             NULL,
    [Active]                    BIT              NULL,
    [CreatedETLRunId]           INT              NOT NULL,
    [ModifiedETLRunId]          INT              NULL,
    CONSTRAINT [PK_DWH_DimEntity] PRIMARY KEY CLUSTERED ([DimEntityId] ASC),
    CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId])
);


GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimEntity] NOCHECK CONSTRAINT [FK_DWH_DimEntity_DimDEMEHierarchyId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimEntity]
    ON [DWH].[DimEntity]([EntityId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'GITargetStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'GITargetEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'GIRequired';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'Lead';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'GIDPBW';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'CompanyStatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'CompanyLegalForm';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'QHSESEntityEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'QHSESEntityStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'DimQHSESEntityEndDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'DimQHSESEntityStartDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'Place';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'EntityType';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'EntityName';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'PostalCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'AddressLine';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'EntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'TibcoIdentifier';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimEntity', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimEntity', @level2type = N'COLUMN', @level2name = N'Active';


````
# Source: `DBs/AzureSingleDB/DWH/Tables/FactAuditTarget.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactAuditTarget.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `e5cea12ebbe3abc54edc76af90479ccde65ad93091eab35ed826843f82ad3c5d`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactAuditTarget] (
    [FactAuditTargetId]      INT            IDENTITY (1, 1) NOT NULL,
    [FactAuditId]            INT            NOT NULL,
    [DimSupportingServiceId] INT            NOT NULL,
    [DimDEMEHierarchyId]     INT            NOT NULL,
    [DimEntityId]            INT            NOT NULL,
    [DimProjectId]           INT            NOT NULL,
    [DimVesselId]            INT            NOT NULL,
    [DimOtherSiteId]         INT            NOT NULL,
    [DimProjectLocationId]   INT            NOT NULL,
    [DimEntityLocationId]    INT            NOT NULL,
    [DimOtherSiteLocationId] INT            NOT NULL,
    [DimVesselLocationId]    INT            NOT NULL,
    [AuditId]                NVARCHAR (255) NULL,
    [SupportingServiceCode]  NVARCHAR (255) NULL,
    [VesselId]               NVARCHAR (255) NULL,
    [ProjectId]              NVARCHAR (255) NULL,
    [OtherSiteId]            NVARCHAR (255) NULL,
    [EntityId]               NVARCHAR (255) NULL,
    [LineFrom]               VARCHAR (4)    NOT NULL,
    [CreatedETLRunId]        INT            NOT NULL,
    [ModifiedETLRunId]       INT            NULL,
    CONSTRAINT [PK_DWH_FactAuditTarget] PRIMARY KEY CLUSTERED ([FactAuditTargetId] ASC),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId] FOREIGN KEY ([FactAuditId]) REFERENCES [DWH].[FactAudit] ([FactAuditId])
);


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId];




GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId];




GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId];




GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId];




GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimDEMEHierarchyId];


GO



GO



GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_DimVesselLocationId];


GO
ALTER TABLE [DWH].[FactAuditTarget] NOCHECK CONSTRAINT [FK_DWH_FactAuditTarget_FactAuditId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'LineFrom';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'OtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'ProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'VesselId';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'AuditId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'FactAuditId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'FactAuditTargetId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactAuditTarget', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'EntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAuditTarget', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


``
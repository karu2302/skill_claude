# Source: `DBs/AzureSingleDB/DWH/Tables/DimVessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimVessel.sql`
- SHA-256 of original file: `cf7fa515f22201a6c5e425fe62cf44ee1414391dffe76d5e00fa2e46c2ba0da1`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimVessel] (
    [DimVesselId]           INT             IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId]    INT             NOT NULL,
    [DimQHSESEndDateId]     INT             NOT NULL,
    [DimQHSESStartDateId]   INT             NOT NULL,
    [VesselId]              NVARCHAR (255)  NOT NULL,
    [ActivityLine]          NVARCHAR (255)  NOT NULL,
    [VesselName]            NVARCHAR (255)  NOT NULL,
    [VesselUnitName]        NVARCHAR (255)  NOT NULL,
    [VesselType]            NVARCHAR (255)  NOT NULL,
    [ClassificationSociety] NVARCHAR (255)  NOT NULL,
    [Exclude]               NVARCHAR (4000) NULL,
    [QHSESCampaignTopic]    NVARCHAR (4000) NULL,
    [FuelType]              NVARCHAR (255)  NOT NULL,
    [GT]                    NVARCHAR (255)  NOT NULL,
    [ISM]                   NVARCHAR (255)  NOT NULL,
    [QHSESCampaign]         NVARCHAR (5)    NULL,
    [RMPE]                  NVARCHAR (255)  NOT NULL,
    [VesselActive]          BIT             NOT NULL,
    [CharteredVessel]       BIT             NULL,
    [QHSESStartDate]        DATE            NULL,
    [QHSESEndDate]          DATE            NULL,
    [GIRequired]            BIT             NULL,
    [GITargetStartDate]     DATE            NULL,
    [GITargetEndDate]       DATE            NULL,
    [VesselLifecycleStatus] NVARCHAR (255)  NOT NULL,
    [ManagementVisitScope]  BIT             NULL,
    [CSRD]                  NVARCHAR (255)  NOT NULL,
    [VMSType]               NVARCHAR (255)  NOT NULL,
    [CreatedETLRunId]       INT             NOT NULL,
    [ModifiedETLRunId]      INT             NULL,
    CONSTRAINT [PK_DWH_DimVessel] PRIMARY KEY CLUSTERED ([DimVesselId] ASC),
    CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId]),
    CONSTRAINT [FK_DWH_DimVessel_DimQHSESEndDateId] FOREIGN KEY ([DimQHSESEndDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_DimVessel_DimQHSESStartDateId] FOREIGN KEY ([DimQHSESStartDateId]) REFERENCES [DWH].[DimDate] ([DimDateId])
);


GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimVessel] NOCHECK CONSTRAINT [FK_DWH_DimVessel_DimDEMEHierarchyId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimVessel]
    ON [DWH].[DimVessel]([VesselId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselLifecycleStatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'GITargetEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'GITargetStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'GIRequired';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'CharteredVessel';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselActive';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'RMPE';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'QHSESCampaign';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'ISM';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'GT';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'FuelType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'ClassificationSociety';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselType';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselUnitName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'ActivityLine';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'DimQHSESStartDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'DimQHSESEndDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimVessel', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'ManagementVisitScope';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'VMSType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimVessel', @level2type = N'COLUMN', @level2name = N'CSRD';


````
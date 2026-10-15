# Source: `DBs/AzureSingleDB/DWH/Tables/FactWorkingHour.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactWorkingHour.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `6c2cdd9b70d7a98b6620260a75477d9f9a030e15587212d4d3672ffb59be1a83`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactWorkingHour] (
    [FactWorkingHourId]          INT             IDENTITY (1, 1) NOT NULL,
    [DimSupportingServiceId]     INT             NOT NULL,
    [DimCharteredVesselId]       INT             NOT NULL,
    [DimVesselId]                INT             NOT NULL,
    [DimProjectId]               INT             NOT NULL,
    [DimOtherSiteId]             INT             NOT NULL,
    [DimWorkingHourDateId]       INT             NOT NULL,
    [DimEntityId]                INT             NOT NULL,
    [DimProjectLocationId]       INT             NOT NULL,
    [DimEntityLocationId]        INT             NOT NULL,
    [DimOtherSiteLocationId]     INT             NOT NULL,
    [DimVesselLocationId]        INT             NOT NULL,
    [SupportingServiceCode]      NVARCHAR (255)  NOT NULL,
    [NumberOfEmployeeHours]      NUMERIC (19, 6) NULL,
    [NumberOfJointVentureHours]  NUMERIC (20, 6) NULL,
    [NumberOfSubcontractorHours] NUMERIC (23, 6) NULL,
    [NumberOfTemporaryHours]     NUMERIC (20, 6) NULL,
    [DataSource]                 VARCHAR (7)     NOT NULL,
    [PovoType]                   NVARCHAR (255)  NOT NULL,
    [VesselName]                 NVARCHAR (255)  NOT NULL,
    [ProjectName]                NVARCHAR (255)  NOT NULL,
    [OtherSiteName]              NVARCHAR (255)  NOT NULL,
    [EntityName]                 NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]      NVARCHAR (255)  NOT NULL,
    [CreatedETLRunId]            INT             NOT NULL,
    [ModifiedETLRunId]           INT             NULL,
    CONSTRAINT [PK_DWH_FactWorkingHour] PRIMARY KEY CLUSTERED ([FactWorkingHourId] ASC),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactWorkingHour_DimWorkingHourDateId] FOREIGN KEY ([DimWorkingHourDateId]) REFERENCES [DWH].[DimDate] ([DimDateId])
);


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselId];


GO
ALTER TABLE [DWH].[FactWorkingHour] NOCHECK CONSTRAINT [FK_DWH_FactWorkingHour_DimVesselLocationId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'PovoType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'NumberOfTemporaryHours';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'NumberOfSubcontractorHours';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'NumberOfJointVentureHours';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'NumberOfEmployeeHours';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimWorkingHourDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'FactWorkingHourId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactWorkingHours', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactWorkingHour', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


``
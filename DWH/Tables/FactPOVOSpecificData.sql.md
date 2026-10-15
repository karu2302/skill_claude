# Source: `DBs/AzureSingleDB/DWH/Tables/FactPOVOSpecificData.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactPOVOSpecificData.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `686fb13ed04cbd55464ef2c4543638d57af221024a817a7131c33311ff558542`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactPOVOSpecificData] (
    [FactPOVOSpecificDataId]                    INT             IDENTITY (1, 1) NOT NULL,
    [DimCharteredVesselId]                      INT             NOT NULL,
    [DimPSDDate]                                INT             NOT NULL,
    [DimProjectId]                              INT             NOT NULL,
    [DimVesselId]                               INT             NOT NULL,
    [DimOtherSiteId]                            INT             NOT NULL,
    [DimSupportingServiceId]                    INT             NOT NULL,
    [DimEntityId]                               INT             NOT NULL,
    [DimProjectLocationId]                      INT             NOT NULL,
    [DimEntityLocationId]                       INT             NOT NULL,
    [DimOtherSiteLocationId]                    INT             NOT NULL,
    [DimVesselLocationId]                       INT             NOT NULL,
    [PSDId]                                     NVARCHAR (255)  NULL,
    [SupportingServiceCode]                     NVARCHAR (255)  NOT NULL,
    [VesselName]                                NVARCHAR (255)  NOT NULL,
    [ProjectName]                               NVARCHAR (255)  NOT NULL,
    [OtherSiteName]                             NVARCHAR (255)  NOT NULL,
    [EntityName]                                NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]                     NVARCHAR (255)  NOT NULL,
    [ProcessCloser]                             NVARCHAR (255)  NOT NULL,
    [ProcessUrlId]                              NVARCHAR (255)  NULL,
    [ProcessCustomId]                           NVARCHAR (255)  NOT NULL,
    [NumberOfSuperintendentUpToProjectDirector] DECIMAL (19, 6) NULL,
    [NumberOfMasterAndChiefEngineer]            DECIMAL (19, 6) NULL,
    [NumberOfISMVesselPresent]                  DECIMAL (19, 6) NULL,
    [NumberCharteredVessels]                    DECIMAL (8, 2)  NULL,
    [CreatedETLRunId]                           INT             NOT NULL,
    [ModifiedETLRunId]                          INT             NULL,
    CONSTRAINT [PK_DWH_FactPOVOSpecificData] PRIMARY KEY CLUSTERED ([FactPOVOSpecificDataId] ASC),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimPSDDate] FOREIGN KEY ([DimPSDDate]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPovoSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPovoSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselId];


GO
ALTER TABLE [DWH].[FactPOVOSpecificData] NOCHECK CONSTRAINT [FK_DWH_FactPOVOSpecificData_DimVesselLocationId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_FactPOVOSpecificData]
    ON [DWH].[FactPOVOSpecificData]([PSDId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'NumberOfISMVesselPresent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'NumberOfMasterAndChiefEngineer';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'NumberOfSuperintendentUpToProjectDirector';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'ProcessUrlId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'PSDId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimPSDDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'FactPOVOSpecificDataId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactPOVOSpecificData', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'ProcessCustomId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPovoSpecificData', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPovoSpecificData', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPovoSpecificData', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPovoSpecificData', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPovoSpecificData', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'NumberCharteredVessels';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactPOVOSpecificData', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


``
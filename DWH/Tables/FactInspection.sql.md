# Source: `DBs/AzureSingleDB/DWH/Tables/FactInspection.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactInspection.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `7d449dda934717f96b0eab1b9d316373fa38b4222e35c08857130a9bc103b8f9`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactInspection] (
    [FactInspectionId]         INT             IDENTITY (1, 1) NOT NULL,
    [DimSupportingServiceId]   INT             NOT NULL,
    [DimCharteredVesselId]     INT             NOT NULL,
    [DimInspectionDateId]      INT             NOT NULL,
    [DimProjectId]             INT             NOT NULL,
    [DimOtherSiteId]           INT             NOT NULL,
    [DimVesselId]              INT             NOT NULL,
    [DimEntityId]              INT             NOT NULL,
    [DimProjectLocationId]     INT             NOT NULL,
    [DimEntityLocationId]      INT             NOT NULL,
    [DimOtherSiteLocationId]   INT             NOT NULL,
    [DimVesselLocationId]      INT             NOT NULL,
    [InspectionId]             NVARCHAR (255)  NULL,
    [CustomInspectionId]       NVARCHAR (255)  NULL,
    [CharteredVesselId]        NVARCHAR (255)  NOT NULL,
    [SupportingServiceCode]    NVARCHAR (255)  NOT NULL,
    [VesselName]               NVARCHAR (255)  NOT NULL,
    [ProjectName]              NVARCHAR (255)  NOT NULL,
    [OtherSiteName]            NVARCHAR (255)  NOT NULL,
    [EntityName]               NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]    NVARCHAR (255)  NOT NULL,
    [ChecklistId]              NVARCHAR (255)  NOT NULL,
    [ExternalInspectorName]    NVARCHAR (255)  NOT NULL,
    [NumberInspectedQuestions] INT             NULL,
    [NumberNOKQuestions]       INT             NULL,
    [ProcessOpenAction]        NVARCHAR (255)  NOT NULL,
    [ProcessTotalAction]       INT             NULL,
    [ProcessOriginator]        NVARCHAR (255)  NOT NULL,
    [ProcessPriority]          NVARCHAR (255)  NOT NULL,
    [Company]                  NVARCHAR (255)  NOT NULL,
    [InspectionDateTime]       DATETIME        NULL,
    [DetailedLocation]         NVARCHAR (255)  NOT NULL,
    [ProcessCloser]            NVARCHAR (255)  NOT NULL,
    [ProcessDescription]       NVARCHAR (MAX)  NOT NULL,
    [ProcessSubject]           NVARCHAR (255)  NOT NULL,
    [Substatus]                NVARCHAR (255)  NOT NULL,
    [ProcessType]              NVARCHAR (255)  NOT NULL,
    [Status]                   NVARCHAR (255)  NOT NULL,
    [ProcessURLId]             NVARCHAR (255)  NULL,
    [DataSource]               VARCHAR (7)     NOT NULL,
    [CheckListName]            NVARCHAR (255)  NOT NULL,
    [CheckListCode]            NVARCHAR (255)  NOT NULL,
    [CheckListStatus]          NVARCHAR (255)  NOT NULL,
    [IncludeStatistics]        INT             NULL,
    [ProcessAssetValue]        NVARCHAR (MAX)  NULL,
    [ProcessAsset]             NVARCHAR (4000) NOT NULL,
    [CreatedETLRunId]          INT             NOT NULL,
    [ModifiedETLRunId]         INT             NULL,
    CONSTRAINT [PK_DWH_FactInspection] PRIMARY KEY CLUSTERED ([FactInspectionId] ASC),
    CONSTRAINT [FK_DWH_FactInspection_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactInspection_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactInspection_DimInspectionDateId] FOREIGN KEY ([DimInspectionDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactInspection_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactInspection_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselId];


GO
ALTER TABLE [DWH].[FactInspection] NOCHECK CONSTRAINT [FK_DWH_FactInspection_DimVesselLocationId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_FactInspection]
    ON [DWH].[FactInspection]([InspectionId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'IncludeStatistics';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CheckListStatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CheckListCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CheckListName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessURLId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'Substatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessSubject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DetailedLocation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'InspectionDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'Company';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessPriority';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessOriginator';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessTotalAction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessOpenAction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'NumberNOKQuestions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'NumberInspectedQuestions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ExternalInspectorName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ChecklistId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CustomInspectionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'InspectionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimInspectionDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'FactInspectionId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactInspection', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessAssetValue';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactInspection', @level2type = N'COLUMN', @level2name = N'ProcessAsset';


``
# Source: `DBs/AzureSingleDB/DWH/Tables/FactObservation.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactObservation.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `90855f284eb829ec93f401af479fcdf129ff4c1ae8ef3c1cb38d98b4e1ff0972`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactObservation] (
    [FactObservationId]                INT             IDENTITY (1, 1) NOT NULL,
    [DimSupportingServiceId]           INT             NOT NULL,
    [DimCharteredVesselId]             INT             NOT NULL,
    [DimVesselId]                      INT             NOT NULL,
    [DimProjectId]                     INT             NOT NULL,
    [DimOtherSiteId]                   INT             NOT NULL,
    [DimEntityId]                      INT             NOT NULL,
    [DimProjectLocationId]             INT             NOT NULL,
    [DimEntityLocationId]              INT             NOT NULL,
    [DimOtherSiteLocationId]           INT             NOT NULL,
    [DimVesselLocationId]              INT             NOT NULL,
    [DimObservationDateId]             INT             NOT NULL,
    [CustomObservationId]              NVARCHAR (255)  NULL,
    [ObservationId]                    NVARCHAR (255)  NULL,
    [CharteredVesselId]                NVARCHAR (255)  NOT NULL,
    [SupportingServiceCode]            NVARCHAR (255)  NOT NULL,
    [ObservationDateTime]              DATETIME        NULL,
    [ProcessCloseDate]                 DATE            NULL,
    [VesselName]                       NVARCHAR (255)  NOT NULL,
    [ProjectName]                      NVARCHAR (255)  NOT NULL,
    [OtherSiteName]                    NVARCHAR (255)  NOT NULL,
    [EntityName]                       NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]            NVARCHAR (255)  NOT NULL,
    [CloseComments]                    NVARCHAR (MAX)  NOT NULL,
    [DescriptionAndProposedAction]     NVARCHAR (MAX)  NOT NULL,
    [DetailedLocation]                 NVARCHAR (255)  NOT NULL,
    [ImmediateActionTakenExplanation]  NVARCHAR (MAX)  NOT NULL,
    [ImmediateActionTaken]             BIT             NULL,
    [TotalActions]                     INT             NULL,
    [ObservationWillBeAssignedTo]      NVARCHAR (255)  NOT NULL,
    [ProcessCloser]                    NVARCHAR (255)  NOT NULL,
    [ProcessOriginator]                NVARCHAR (255)  NOT NULL,
    [ProcessPriority]                  NVARCHAR (255)  NOT NULL,
    [Substatus]                        NVARCHAR (255)  NOT NULL,
    [ProcessType]                      NVARCHAR (255)  NOT NULL,
    [ProcessURLId]                     NVARCHAR (255)  NULL,
    [ReportedAnonymously]              BIT             NULL,
    [ResponsibleOffice]                NVARCHAR (255)  NOT NULL,
    [ResponsibleOtherSite]             NVARCHAR (255)  NOT NULL,
    [ResponsibleProject]               NVARCHAR (255)  NOT NULL,
    [ResponsibleVessel]                NVARCHAR (255)  NOT NULL,
    [Status]                           NVARCHAR (255)  NOT NULL,
    [Title]                            NVARCHAR (4000) NOT NULL,
    [DataSource]                       NVARCHAR (255)  NULL,
    [TrendCategories]                  NVARCHAR (255)  NOT NULL,
    [TrendCategoriesDescription]       NVARCHAR (MAX)  NULL,
    [HighRiskTask]                     NVARCHAR (255)  NULL,
    [ActivitiesBlock4]                 NVARCHAR (255)  NULL,
    [SecondaryFactor]                  NVARCHAR (255)  NULL,
    [ReportedBehalfOf]                 NVARCHAR (MAX)  NOT NULL,
    [ReportedBehalfOfDEME]             NVARCHAR (255)  NOT NULL,
    [TypeOfObservation]                NVARCHAR (255)  NOT NULL,
    [HighRiskTaskLevel2]               NVARCHAR (255)  NOT NULL,
    [TypeOfOperation]                  NVARCHAR (255)  NOT NULL,
    [SpecifyOtherHighRiskTask]         NVARCHAR (255)  NOT NULL,
    [SpecifyOtherSecondaryFactor]      NVARCHAR (255)  NOT NULL,
    [SpecifyOtherActivityAndTechnique] NVARCHAR (255)  NOT NULL,
    [CreatedETLRunId]                  INT             NOT NULL,
    [ModifiedETLRunId]                 INT             NULL,
    CONSTRAINT [PK_DWH_FactObservation] PRIMARY KEY CLUSTERED ([FactObservationId] ASC),
    CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactObservation_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactObservation_DimObservationDateId] FOREIGN KEY ([DimObservationDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactObservation_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactObservation_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselId];


GO
ALTER TABLE [DWH].[FactObservation] NOCHECK CONSTRAINT [FK_DWH_FactObservation_DimVesselLocationId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SecondaryFactor';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ActivitiesBlock4';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'HighRiskTask';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'TrendCategoriesDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'TrendCategories';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'Title';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ResponsibleVessel';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ResponsibleProject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ResponsibleOtherSite';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ResponsibleOffice';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ReportedAnonymously';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessURLId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'Substatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessPriority';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessOriginator';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ObservationWillBeAssignedTo';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'TotalActions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ImmediateActionTaken';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ImmediateActionTakenExplanation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DetailedLocation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DescriptionAndProposedAction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'CloseComments';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ObservationDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ObservationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'CustomObservationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimObservationDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'FactObservationId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactObservation', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ReportedBehalfOf';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProcessCloseDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ReportedBehalfOfDEME';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'TypeOfOperation';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'HighRiskTaskLevel2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'TypeOfObservation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SpecifyOtherSecondaryFactor';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SpecifyOtherHighRiskTask';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactObservation', @level2type = N'COLUMN', @level2name = N'SpecifyOtherActivityAndTechnique';


``
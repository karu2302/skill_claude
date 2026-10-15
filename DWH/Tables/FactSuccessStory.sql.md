# Source: `DBs/AzureSingleDB/DWH/Tables/FactSuccessStory.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactSuccessStory.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `44651f22c263ca3b650a3b364d6bb6073001a72b4013003abba4b09e653a86e4`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactSuccessStory] (
    [FactSuccessStoryId]     INT             IDENTITY (1, 1) NOT NULL,
    [DimCharteredVesselId]   INT             NOT NULL,
    [DimDateId]              INT             NOT NULL,
    [DimEntityId]            INT             NOT NULL,
    [DimOtherSiteId]         INT             NOT NULL,
    [DimProjectId]           INT             NOT NULL,
    [DimProjectLocationId]   INT             NOT NULL,
    [DimEntityLocationId]    INT             NOT NULL,
    [DimOtherSiteLocationId] INT             NOT NULL,
    [DimVesselLocationId]    INT             NOT NULL,
    [DimSupportingServiceId] INT             NOT NULL,
    [DimVesselId]            INT             NOT NULL,
    [SuccessStoryId]         NVARCHAR (255)  NULL,
    [CustomSuccessStoryId]   NVARCHAR (255)  NOT NULL,
    [CharteredVesselId]      NVARCHAR (255)  NOT NULL,
    [SupportingServiceCode]  NVARCHAR (10)   NULL,
    [VesselName]             NVARCHAR (255)  NOT NULL,
    [ProjectName]            NVARCHAR (255)  NOT NULL,
    [OtherSiteName]          NVARCHAR (255)  NOT NULL,
    [EntityName]             NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]  NVARCHAR (255)  NOT NULL,
    [SuccessStoryDateTime]   DATETIME        NULL,
    [Subject]                NVARCHAR (MAX)  NOT NULL,
    [Description]            NVARCHAR (MAX)  NOT NULL,
    [Feedback]               NVARCHAR (MAX)  NOT NULL,
    [FeedbackRespondent]     NVARCHAR (255)  NOT NULL,
    [Activity]               NVARCHAR (255)  NOT NULL,
    [HRT]                    NVARCHAR (255)  NOT NULL,
    [HRT2]                   NVARCHAR (255)  NOT NULL,
    [Originator]             NVARCHAR (255)  NOT NULL,
    [SecondaryFactor]        NVARCHAR (255)  NOT NULL,
    [Results]                NVARCHAR (MAX)  NOT NULL,
    [TotalLikes]             INT             NOT NULL,
    [AverageScore]           INT             NOT NULL,
    [FeedbackImpact]         NVARCHAR (255)  NOT NULL,
    [ImpactScore]            DECIMAL (18, 2) NOT NULL,
    [FeedbackEffort]         NVARCHAR (255)  NOT NULL,
    [EffortScore]            DECIMAL (18, 2) NOT NULL,
    [FeedbackApplicability]  NVARCHAR (255)  NOT NULL,
    [ApplicabilityScore]     DECIMAL (18, 2) NOT NULL,
    [FeedbackOriginality]    NVARCHAR (255)  NOT NULL,
    [OriginalityScore]       DECIMAL (18, 2) NOT NULL,
    [FinalScore]             DECIMAL (18, 2) NOT NULL,
    [ProcessDescription]     NVARCHAR (MAX)  NULL,
    [status]                 NVARCHAR (255)  NOT NULL,
    [CompletedBy]            NVARCHAR (255)  NOT NULL,
    [CompletedDate]          NVARCHAR (255)  NOT NULL,
    [CreatedETLRunId]        INT             NOT NULL,
    [ModifiedETLRunId]       INT             NULL,
    CONSTRAINT [PK_DWH_FactSuccessStory] PRIMARY KEY CLUSTERED ([FactSuccessStoryId] ASC),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimDateId] FOREIGN KEY ([DimDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselId];


GO
ALTER TABLE [DWH].[FactSuccessStory] NOCHECK CONSTRAINT [FK_DWH_FactSuccessStory_DimVesselLocationId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'AverageScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'TotalLikes';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Results';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'SecondaryFactor';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Originator';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'HRT2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'HRT';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Activity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FeedbackRespondent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Feedback';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Description';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'SuccessStoryDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'CustomSuccessStoryId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'SuccessStoryId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FactSuccessStoryId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactSuccessStory', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'OriginalityScore';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'ImpactScore';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FinalScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'EffortScore';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'ApplicabilityScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'Subject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FeedbackOriginality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FeedbackImpact';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FeedbackEffort';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'FeedbackApplicability';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'ProcessDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'CompletedDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactSuccessStory', @level2type = N'COLUMN', @level2name = N'CompletedBy';


``
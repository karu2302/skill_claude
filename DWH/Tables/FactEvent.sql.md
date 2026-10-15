# Source: `DBs/AzureSingleDB/DWH/Tables/FactEvent.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactEvent.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `d762e64d83a9b105851c30a8df08f2ba910375df17ee651b1b69e8ed4411130b`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactEvent] (
    [FactEventId]                 INT            IDENTITY (1, 1) NOT NULL,
    [DimSupportingServiceId]      INT            NOT NULL,
    [DimProjectId]                INT            NOT NULL,
    [DimVesselId]                 INT            NOT NULL,
    [DimOtherSiteId]              INT            NOT NULL,
    [DimCharteredVesselId]        INT            NOT NULL,
    [DimEventDateId]              INT            NOT NULL,
    [DimEntityId]                 INT            NOT NULL,
    [DimProjectLocationId]        INT            NOT NULL,
    [DimEntityLocationId]         INT            NOT NULL,
    [DimOtherSiteLocationId]      INT            NOT NULL,
    [DimVesselLocationId]         INT            NOT NULL,
    [EventId]                     NVARCHAR (255) NULL,
    [CustomEventId]               NVARCHAR (255) NULL,
    [ProjectId]                   NVARCHAR (255) NULL,
    [VesselId]                    NVARCHAR (255) NULL,
    [OtherSiteId]                 NVARCHAR (255) NULL,
    [EntityId]                    NVARCHAR (255) NULL,
    [CharteredVesselId]           NVARCHAR (255) NOT NULL,
    [SupportingServiceCode]       NVARCHAR (255) NOT NULL,
    [VesselName]                  NVARCHAR (255) NOT NULL,
    [ProjectName]                 NVARCHAR (255) NOT NULL,
    [OtherSiteName]               NVARCHAR (255) NOT NULL,
    [EntityName]                  NVARCHAR (255) NOT NULL,
    [SupportingServiceName]       NVARCHAR (255) NOT NULL,
    [EventDateTime]               DATETIME       NULL,
    [EventCloseDate]              DATETIME       NULL,
    [DetailedDescriptionLocation] NVARCHAR (255) NOT NULL,
    [ProcessCloser]               NVARCHAR (255) NOT NULL,
    [LeadName]                    NVARCHAR (255) NOT NULL,
    [ExternalLead]                NVARCHAR (255) NOT NULL,
    [ExternalName]                NVARCHAR (255) NOT NULL,
    [InternalName]                NVARCHAR (255) NOT NULL,
    [ReportedBy]                  NVARCHAR (255) NOT NULL,
    [AttendanceList]              NVARCHAR (255) NOT NULL,
    [Campaign]                    NVARCHAR (255) NOT NULL,
    [CampaignRelated]             INT            NULL,
    [Company]                     NVARCHAR (255) NOT NULL,
    [DPDrillType]                 NVARCHAR (255) NOT NULL,
    [DrillEvaluation]             NVARCHAR (MAX) NOT NULL,
    [DrillType]                   NVARCHAR (255) NOT NULL,
    [EventName]                   NVARCHAR (255) NOT NULL,
    [EventDescription]            NVARCHAR (MAX) NOT NULL,
    [EventPriority]               NVARCHAR (255) NOT NULL,
    [Status]                      NVARCHAR (255) NOT NULL,
    [Substatus]                   NVARCHAR (255) NOT NULL,
    [EventType]                   NVARCHAR (255) NULL,
    [ProcessURLId]                NVARCHAR (255) NULL,
    [Function]                    NVARCHAR (255) NOT NULL,
    [Log]                         NVARCHAR (MAX) NOT NULL,
    [MeetingType]                 NVARCHAR (255) NOT NULL,
    [MeetingTypeGUID]             NVARCHAR (255) NOT NULL,
    [MeetingTypeGroup]            NVARCHAR (255) NOT NULL,
    [MeetingTypeStatus]           NVARCHAR (255) NOT NULL,
    [ScenarioPlannedActivities]   NVARCHAR (MAX) NOT NULL,
    [SpecifyOther]                NVARCHAR (MAX) NOT NULL,
    [TotalActions]                INT            NULL,
    [TotalParticipants]           INT            NULL,
    [DataSource]                  VARCHAR (7)    NOT NULL,
    [ParticipatedPMWM]            NVARCHAR (255) NOT NULL,
    [DurationHours]               INT            NULL,
    [DurationMinutes]             INT            NULL,
    [TotalDEME]                   INT            NULL,
    [TotalExternal]               INT            NULL,
    [SubtypeEventGUID]            NVARCHAR (MAX) NOT NULL,
    [InternalExternal]            NVARCHAR (255) NOT NULL,
    [CreatedETLRunId]             INT            NOT NULL,
    [ModifiedETLRunId]            INT            NULL,
    CONSTRAINT [PK_DWH_FactEvent] PRIMARY KEY CLUSTERED ([FactEventId] ASC),
    CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactEvent_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactEvent_DimEventDateId] FOREIGN KEY ([DimEventDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactEvent_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactEvent_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselId];


GO
ALTER TABLE [DWH].[FactEvent] NOCHECK CONSTRAINT [FK_DWH_FactEvent_DimVesselLocationId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_FactEvent]
    ON [DWH].[FactEvent]([EventId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ParticipatedPMWM';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'TotalParticipants';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'TotalActions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'SpecifyOther';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ScenarioPlannedActivities';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'MeetingType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Log';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Function';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ProcessURLId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Substatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventPriority';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DrillType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DrillEvaluation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DPDrillType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Company';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'CampaignRelated';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'Campaign';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'AttendanceList';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ReportedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'InternalName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ExternalName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ExternalLead';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'LeadName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DetailedDescriptionLocation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventCloseDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'OtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'VesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'CustomEventId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EventId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimEventDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'FactEventId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactEvent', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'TotalExternal';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'TotalDEME';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DurationMinutes';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DurationHours';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'InternalExternal';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'SubtypeEventGUID';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'MeetingTypeStatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'MeetingTypeGUID';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactEvent', @level2type = N'COLUMN', @level2name = N'MeetingTypeGroup';


``
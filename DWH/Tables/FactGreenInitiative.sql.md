# Source: `DBs/AzureSingleDB/DWH/Tables/FactGreenInitiative.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactGreenInitiative.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `5dbd0027e8e53b47d7760ad51d813520e2a7c27705af60b44418d49d1e33996c`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactGreenInitiative] (
    [FactGreenInitiativeId]                  INT             IDENTITY (1, 1) NOT NULL,
    [DimCharteredVesselId]                   INT             NOT NULL,
    [DimProjectId]                           INT             NOT NULL,
    [DimVesselId]                            INT             NOT NULL,
    [DimOtherSiteId]                         INT             NOT NULL,
    [DimSupportingServiceId]                 INT             NOT NULL,
    [DimGreenInitiativeDateId]               INT             NOT NULL,
    [DimEntityId]                            INT             NOT NULL,
    [DimProjectLocationId]                   INT             NOT NULL,
    [DimEntityLocationId]                    INT             NOT NULL,
    [DimOtherSiteLocationId]                 INT             NOT NULL,
    [DimVesselLocationId]                    INT             NOT NULL,
    [GreenInitiativeId]                      NVARCHAR (255)  NULL,
    [CustomGreenInitiativeId]                NVARCHAR (255)  NULL,
    [CharteredVesselId]                      NVARCHAR (255)  NOT NULL,
    [SupportingServiceCode]                  NVARCHAR (255)  NOT NULL,
    [VesselName]                             NVARCHAR (255)  NOT NULL,
    [ProjectName]                            NVARCHAR (255)  NOT NULL,
    [OtherSiteName]                          NVARCHAR (255)  NOT NULL,
    [EntityName]                             NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]                  NVARCHAR (255)  NOT NULL,
    [GreenInitiativeDate]                    DATETIME        NULL,
    [GreenInitiativeClosedDate]              DATETIME        NULL,
    [DetailedDescriptionLocation]            NVARCHAR (255)  NOT NULL,
    [ProcessCloser]                          NVARCHAR (255)  NOT NULL,
    [GIOriginator]                           NVARCHAR (255)  NOT NULL,
    [GIApprovedBy]                           NVARCHAR (255)  NOT NULL,
    [GIUser]                                 NVARCHAR (255)  NOT NULL,
    [GISubject]                              NVARCHAR (255)  NOT NULL,
    [GIDescription]                          NVARCHAR (MAX)  NOT NULL,
    [Status]                                 NVARCHAR (255)  NOT NULL,
    [GIType]                                 NVARCHAR (255)  NOT NULL,
    [ProcessURLId]                           NVARCHAR (255)  NULL,
    [GIScore]                                INT             NULL,
    [MaterialsReused]                        NVARCHAR (255)  NOT NULL,
    [IdeaSuggestion]                         NVARCHAR (255)  NOT NULL,
    [GIEnvironmentAspect]                    NVARCHAR (255)  NOT NULL,
    [GIFollowUpCommentsSummary]              NVARCHAR (MAX)  NOT NULL,
    [GIImpact]                               NVARCHAR (MAX)  NOT NULL,
    [GIProcess]                              NVARCHAR (MAX)  NOT NULL,
    [GIRejectedOrApproved]                   NVARCHAR (255)  NULL,
    [GIResult]                               NVARCHAR (MAX)  NOT NULL,
    [DataSource]                             VARCHAR (7)     NOT NULL,
    [ProcessActivity]                        NVARCHAR (255)  NOT NULL,
    [ProcessActivityOther]                   NVARCHAR (255)  NOT NULL,
    [ImpactInlineButtons]                    NVARCHAR (255)  NOT NULL,
    [EffortInlineButtons]                    NVARCHAR (255)  NOT NULL,
    [EmissionReductionMethodOfOperations]    NVARCHAR (255)  NOT NULL,
    [EmissionReductionTechnicalIntervention] NVARCHAR (255)  NOT NULL,
    [OtherEmissionReduction]                 NVARCHAR (255)  NOT NULL,
    [ApprovalStatus]                         NVARCHAR (255)  NOT NULL,
    [FeedbackEffort]                         NVARCHAR (255)  NOT NULL,
    [EffortScore]                            DECIMAL (18, 2) NOT NULL,
    [FeedbackImpact]                         NVARCHAR (255)  NOT NULL,
    [ImpactScore]                            DECIMAL (18, 2) NOT NULL,
    [FeedbackApplicability]                  NVARCHAR (255)  NOT NULL,
    [ApplicabilityScore]                     DECIMAL (18, 2) NOT NULL,
    [FeedbackOriginality]                    NVARCHAR (255)  NOT NULL,
    [OriginalityScore]                       DECIMAL (18, 2) NOT NULL,
    [FinalScore]                             DECIMAL (18, 2) NOT NULL,
    [WorldCleanupCampaign]                   BIT             NULL,
    [CompletedBy]                            NVARCHAR (255)  NOT NULL,
    [CompletedDate]                          NVARCHAR (255)  NOT NULL,
    [FeedbackRespondent]                     NVARCHAR (MAX)  NOT NULL,
    [AmountSaving]                           NVARCHAR (255)  NOT NULL,
    [UnitSaving]                             NVARCHAR (255)  NOT NULL,
    CONSTRAINT [PK_DWH_FactGreenInitiative] PRIMARY KEY CLUSTERED ([FactGreenInitiativeId] ASC),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimGreenInitiativeDateId] FOREIGN KEY ([DimGreenInitiativeDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimEntityId];


GO



GO



GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];




GO



GO



GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselId];


GO
ALTER TABLE [DWH].[FactGreenInitiative] NOCHECK CONSTRAINT [FK_DWH_FactGreenInitiative_DimVesselLocationId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_FactGreenInitiative]
    ON [DWH].[FactGreenInitiative]([GreenInitiativeId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ProcessActivityOther';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ProcessActivity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIResult';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIRejectedOrApproved';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIProcess';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIImpact';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIFollowUpCommentsSummary';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIEnvironmentAspect';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ProcessURLId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GISubject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIUser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIApprovedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GIOriginator';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DetailedDescriptionLocation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GreenInitiativeClosedDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GreenInitiativeDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'CustomGreenInitiativeId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'GreenInitiativeId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimGreenInitiativeDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FactGreenInitiativeId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactGreenInitiative', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ImpactInlineButtons';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'EffortInlineButtons';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'MaterialsReused';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'IdeaSuggestion';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'OtherEmissionReduction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'OriginalityScore';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FinalScore';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'EmissionReductionTechnicalIntervention';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'EmissionReductionMethodOfOperations';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ApprovalStatus';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ImpactScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FeedbackOriginality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FeedbackImpact';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FeedbackEffort';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FeedbackApplicability';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'EffortScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'ApplicabilityScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'WorldCleanupCampaign';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'FeedbackRespondent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'CompletedDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'CompletedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'UnitSaving';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactGreenInitiative', @level2type = N'COLUMN', @level2name = N'AmountSaving';


``
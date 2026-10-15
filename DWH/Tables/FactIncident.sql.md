# Source: `DBs/AzureSingleDB/DWH/Tables/FactIncident.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactIncident.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `0cfbcc103b7812fae5ee49d5d71c1891dbed676bd282844ce8b0dbbc5c3feb31`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactIncident] (
    [FactIncidentId]                                            INT             IDENTITY (1, 1) NOT NULL,
    [DimSupportingServiceId]                                    INT             NOT NULL,
    [DimCharteredVesselId]                                      INT             NOT NULL,
    [DimVesselId]                                               INT             NOT NULL,
    [DimProjectId]                                              INT             NOT NULL,
    [DimOtherSiteId]                                            INT             NOT NULL,
    [DimLeadActivityLineId]                                     INT             NOT NULL,
    [DimIncidentOccuredDateId]                                  INT             NOT NULL,
    [DimEntityId]                                               INT             NOT NULL,
    [DimProjectLocationId]                                      INT             NOT NULL,
    [DimEntityLocationId]                                       INT             NOT NULL,
    [DimOtherSiteLocationId]                                    INT             NOT NULL,
    [DimVesselLocationId]                                       INT             NOT NULL,
    [IncidentId]                                                NVARCHAR (255)  NULL,
    [CustomIncidentId]                                          NVARCHAR (255)  NULL,
    [CharteredVesselId]                                         NVARCHAR (255)  NOT NULL,
    [SupportingServiceCode]                                     NVARCHAR (255)  NOT NULL,
    [VesselName]                                                NVARCHAR (255)  NOT NULL,
    [ProjectName]                                               NVARCHAR (255)  NOT NULL,
    [OtherSiteName]                                             NVARCHAR (255)  NOT NULL,
    [EntityName]                                                NVARCHAR (255)  NOT NULL,
    [SupportingServiceName]                                     NVARCHAR (255)  NOT NULL,
    [IncidentType]                                              NVARCHAR (512)  NULL,
    [IncidentTitle]                                             NVARCHAR (255)  NOT NULL,
    [IncidentNotificationContains4LevelPictures]                INT             NULL,
    [IncidentRelatedTo]                                         NVARCHAR (255)  NOT NULL,
    [IncidentReportTitle]                                       NVARCHAR (255)  NOT NULL,
    [ActionsTakenNL]                                            NVARCHAR (MAX)  NOT NULL,
    [ExplainProposedActions]                                    NVARCHAR (MAX)  NOT NULL,
    [ImmediateActionsTaken]                                     NVARCHAR (MAX)  NOT NULL,
    [Min2SMARTActionsProposed]                                  NVARCHAR (255)  NOT NULL,
    [ProcessOpenActions]                                        NVARCHAR (255)  NOT NULL,
    [ProcessTotalActions]                                       INT             NULL,
    [ActivitiesBlock4PerformedIncidentTime]                     NVARCHAR (255)  NOT NULL,
    [ActivityDetails]                                           NVARCHAR (MAX)  NOT NULL,
    [DateAccepted]                                              DATETIME        NULL,
    [DateReported]                                              DATETIME        NULL,
    [IncidentDateTime]                                          DATETIME        NULL,
    [IncidentAcceptedBy]                                        NVARCHAR (255)  NOT NULL,
    [ProcessCloser]                                             NVARCHAR (255)  NOT NULL,
    [QualityCheckPerformedBy]                                   NVARCHAR (255)  NOT NULL,
    [ReportedBy]                                                NVARCHAR (255)  NOT NULL,
    [ReportedByUser]                                            NVARCHAR (255)  NOT NULL,
    [ResponsibleManager]                                        NVARCHAR (255)  NOT NULL,
    [DetailedDescriptionLocation]                               NVARCHAR (MAX)  NOT NULL,
    [LocationNL]                                                NVARCHAR (MAX)  NOT NULL,
    [Assets]                                                    NVARCHAR (255)  NOT NULL,
    [People]                                                    NVARCHAR (255)  NOT NULL,
    [Environment]                                               NVARCHAR (255)  NOT NULL,
    [Quality]                                                   NVARCHAR (255)  NOT NULL,
    [QualityCategory]                                           NVARCHAR (255)  NOT NULL,
    [Reputation]                                                NVARCHAR (255)  NOT NULL,
    [Security]                                                  NVARCHAR (255)  NOT NULL,
    [DescribeDamage]                                            NVARCHAR (MAX)  NOT NULL,
    [PotentialRiskScore]                                        NVARCHAR (255)  NOT NULL,
    [PotentialRiskScore2]                                       INT             NULL,
    [PotentialSeverity]                                         NVARCHAR (255)  NOT NULL,
    [Probability]                                               NVARCHAR (255)  NOT NULL,
    [EnvironmentalAspects]                                      NVARCHAR (4000) NOT NULL,
    [SpecifyOtherEnvironmental]                                 NVARCHAR (255)  NOT NULL,
    [SpecifyOtherQuality]                                       NVARCHAR (255)  NOT NULL,
    [SpecifyOtherSecurity]                                      NVARCHAR (255)  NULL,
    [ActualDEMECostsEntered]                                    NUMERIC (19, 2) NULL,
    [TotalCost]                                                 NUMERIC (19, 2) NULL,
    [HicoDEME]                                                  NVARCHAR (255)  NULL,
    [HicoOverall]                                               NVARCHAR (255)  NOT NULL,
    [DescriptionOfInjuryInCaseOfLTI]                            NVARCHAR (MAX)  NULL,
    [Fatality]                                                  BIT             NULL,
    [FirstAid]                                                  BIT             NULL,
    [PotentialLTI]                                              BIT             NULL,
    [HIPO]                                                      BIT             NULL,
    [ReasonChangeHIPOClassification]                            NVARCHAR (MAX)  NOT NULL,
    [ExtraHIPOCategory]                                         NVARCHAR (255)  NOT NULL,
    [SpecifyOtherHIPOCategory]                                  NVARCHAR (255)  NOT NULL,
    [ReviewDamage]                                              NVARCHAR (MAX)  NOT NULL,
    [ReviewDamageNL]                                            NVARCHAR (MAX)  NOT NULL,
    [ReviewDescription]                                         NVARCHAR (MAX)  NOT NULL,
    [ReviewDescriptionNL]                                       NVARCHAR (MAX)  NOT NULL,
    [ReviewActionsTaken]                                        NVARCHAR (MAX)  NOT NULL,
    [CausedByThirdParty]                                        BIT             NULL,
    [InvestigationCarriedOutByMultidisciplinaryTeam]            NVARCHAR (255)  NOT NULL,
    [InvestigationLeader]                                       NVARCHAR (255)  NOT NULL,
    [InvestigationReportContainsTimeline]                       NVARCHAR (255)  NOT NULL,
    [InvestigationReportDate]                                   DATETIME        NULL,
    [Investigation]                                             BIT             NULL,
    [InvestigationReportIsSignedOffOrApprovedByLocalManagement] NVARCHAR (255)  NOT NULL,
    [InvestigationUploaded]                                     BIT             NULL,
    [InvolvedPartiesOfInvestigation]                            NVARCHAR (255)  NOT NULL,
    [InvestigationHQReview]                                     NVARCHAR (255)  NOT NULL,
    [ProcessDescription]                                        NVARCHAR (MAX)  NOT NULL,
    [ProcessError]                                              NVARCHAR (255)  NOT NULL,
    [ProcessSubject]                                            NVARCHAR (255)  NOT NULL,
    [Status]                                                    NVARCHAR (255)  NOT NULL,
    [Substatus]                                                 NVARCHAR (255)  NOT NULL,
    [ProcessType]                                               NVARCHAR (255)  NOT NULL,
    [ProcessURLID]                                              NVARCHAR (255)  NULL,
    [SWAUsed]                                                   NVARCHAR (255)  NOT NULL,
    [AdditionalInformation]                                     NVARCHAR (MAX)  NOT NULL,
    [CommentsClassFlag]                                         NVARCHAR (MAX)  NOT NULL,
    [CommentsFirstNotification]                                 NVARCHAR (MAX)  NOT NULL,
    [ConstatationsNL]                                           NVARCHAR (MAX)  NOT NULL,
    [DeclarationAvailable]                                      BIT             NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident]                 NVARCHAR (255)  NOT NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident2]                NVARCHAR (255)  NOT NULL,
    [HRTReasonNA]                                               NVARCHAR (255)  NOT NULL,
    [CommutingRelatedIncident]                                  BIT             NULL,
    [NonWorkRelatedIncident]                                    BIT             NULL,
    [LostTimeIncident]                                          BIT             NULL,
    [LTITypeWorldwide]                                          VARCHAR (35)    NOT NULL,
    [NumberCausedByTP]                                          NVARCHAR (255)  NOT NULL,
    [ReasonForCancellingRejecting]                              NVARCHAR (MAX)  NOT NULL,
    [ReasonPictureLevel1NA]                                     NVARCHAR (MAX)  NOT NULL,
    [ReasonPictureLevel2NA]                                     NVARCHAR (MAX)  NOT NULL,
    [ReasonPictureLevel3NA]                                     NVARCHAR (MAX)  NOT NULL,
    [ReasonPictureLevel4NA]                                     NVARCHAR (MAX)  NOT NULL,
    [ReOpenComments]                                            NVARCHAR (MAX)  NOT NULL,
    [ReportableToAuthorities]                                   INT             NULL,
    [ReportableToClassAndFlagstate]                             INT             NULL,
    [ReportedOnBehalfOfDEMEEmployee]                            NVARCHAR (255)  NOT NULL,
    [ReportedOnBehalfOfThirdParty]                              BIT             NULL,
    [ReportInYourOwnName]                                       INT             NULL,
    [RestrictedWork]                                            INT             NULL,
    [RootCausesAnalysisHasDefinedMin2RootCauses]                NVARCHAR (255)  NOT NULL,
    [StatusLevel1Picture]                                       NVARCHAR (255)  NOT NULL,
    [StatusLevel2Picture]                                       NVARCHAR (255)  NOT NULL,
    [StatusLevel3Picture]                                       NVARCHAR (255)  NOT NULL,
    [StatusLevel4Picture]                                       NVARCHAR (255)  NOT NULL,
    [TDfleetHQZwijndrecht]                                      NVARCHAR (255)  NOT NULL,
    [TheftOf]                                                   NVARCHAR (255)  NOT NULL,
    [DataSource]                                                VARCHAR (7)     NOT NULL,
    [QCSelected]                                                BIT             NULL,
    [EIncidents]                                                BIT             NULL,
    [QIncidents]                                                BIT             NULL,
    [RedIncidents]                                              BIT             NULL,
    [HIPORed]                                                   VARCHAR (8)     NOT NULL,
    [EIncidentRed]                                              VARCHAR (14)    NOT NULL,
    [EstimatedCost]                                             INT             NULL,
    [ReportedInTime]                                            INT             NULL,
    [TypeCommutingIncident]                                     NVARCHAR (255)  NOT NULL,
    [LifeSavingRules]                                           NVARCHAR (255)  NOT NULL,
    [HRTCombinationALE]                                         NVARCHAR (255)  NOT NULL,
    [WorldwideEquivalent]                                       BIT             NOT NULL,
    [InvestigationThirdParty]                                   BIT             NULL,
    [InterventionTeam5555Involved]                              BIT             NULL,
    [INC_RedIncidentsHICO]                                      INT             NOT NULL,
    [INC_RedIncidentsHIPO]                                      INT             NOT NULL,
    [INC_MajorIncidentsHICO]                                    INT             NOT NULL,
    [CriticalJob]                                               NVARCHAR (255)  NOT NULL,
    [ProjectLifecycle]                                          NVARCHAR (255)  NOT NULL,
    [QualityIncidentRelatedTo]                                  NVARCHAR (255)  NOT NULL,
    [RelatedToSuppliedMaterialsPartsAndActivities]              NVARCHAR (255)  NOT NULL,
    [SuppliedMaterialsPartsAndActivities]                       NVARCHAR (255)  NOT NULL,
    [RelatedProcessOrActivity]                                  NVARCHAR (255)  NOT NULL,
    [TypeOfDeviation]                                           NVARCHAR (255)  NOT NULL,
    [CSRD_Fatality_Own_Workforce]                               INT             NOT NULL,
    [CSRD_LTI_Own_Workforce]                                    INT             NOT NULL,
    [CSRD_RWC_Own_Workforce]                                    INT             NOT NULL,
    [INC_RedIncidentsLTI]                                       INT             NOT NULL,
    [CSRD_MT_Own_Workforce]                                     INT             NOT NULL,
    [INC_MajorIncidentsTotal]                                   INT             NOT NULL,
    [CreatedETLRunId]                                           INT             NOT NULL,
    [ModifiedETLRunId]                                          INT             NULL,
    [DWH_INC_MajorIncidentsEnvironmental]                           INT             NOT NULL,
    [DWH_INC_RedIncidentsEnvironmental]                             INT             NOT NULL,
    [DWH_TRIN]                                                      INT             NOT NULL,
    CONSTRAINT [PK_DWH_FactIncident] PRIMARY KEY CLUSTERED ([FactIncidentId] ASC),
    CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId] FOREIGN KEY ([DimCharteredVesselId]) REFERENCES [DWH].[DimCharteredVessel] ([DimCharteredVesselId]),
    CONSTRAINT [FK_DWH_FactIncident_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId] FOREIGN KEY ([DimEntityLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactIncident_DimIncidentOccuredDateId] FOREIGN KEY ([DimIncidentOccuredDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId] FOREIGN KEY ([DimLeadActivityLineId]) REFERENCES [DWH].[DimActivityLine] ([DimActivityLineId]),
    CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId] FOREIGN KEY ([DimOtherSiteLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactIncident_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId] FOREIGN KEY ([DimProjectLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId]),
    CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactIncident_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId]),
    CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId] FOREIGN KEY ([DimVesselLocationId]) REFERENCES [DWH].[DimPOVOLocation] ([DimPOVOLocationId])
);


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimCharteredVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimEntityId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO



GO



GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO



GO



GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO



GO



GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO



GO



GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];




GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimLeadActivityLineId];


GO



GO



GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimOtherSiteLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimProjectLocationId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselId];


GO
ALTER TABLE [DWH].[FactIncident] NOCHECK CONSTRAINT [FK_DWH_FactIncident_DimVesselLocationId];


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportedInTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'EstimatedCost';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'EIncidentRed';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HIPORed';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'RedIncidents';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'EIncidents';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'QCSelected';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'TheftOf';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'TDfleetHQZwijndrecht';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'StatusLevel4Picture';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'StatusLevel3Picture';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'StatusLevel2Picture';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'StatusLevel1Picture';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'RootCausesAnalysisHasDefinedMin2RootCauses';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'RestrictedWork';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportInYourOwnName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportedOnBehalfOfThirdParty';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportedOnBehalfOfDEMEEmployee';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportableToClassAndFlagstate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportableToAuthorities';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReOpenComments';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel4NA';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel3NA';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel2NA';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel1NA';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonForCancellingRejecting';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'NumberCausedByTP';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'LTITypeWorldwide';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'LostTimeIncident';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HRTReasonNA';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HighRiskTasksPerformedAtTheTimeOfIncident2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HighRiskTasksPerformedAtTheTimeOfIncident';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DeclarationAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ConstatationsNL';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CommentsFirstNotification';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CommentsClassFlag';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'AdditionalInformation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessURLID';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Substatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessSubject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessError';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvolvedPartiesOfInvestigation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationUploaded';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationReportIsSignedOffOrApprovedByLocalManagement';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Investigation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationReportDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationReportContainsTimeline';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationLeader';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationCarriedOutByMultidisciplinaryTeam';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CausedByThirdParty';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReviewActionsTaken';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReviewDescriptionNL';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReviewDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReviewDamageNL';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReviewDamage';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherHIPOCategory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ExtraHIPOCategory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReasonChangeHIPOClassification';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HIPO';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'PotentialLTI';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'FirstAid';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Fatality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DescriptionOfInjuryInCaseOfLTI';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HicoOverall';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HicoDEME';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'TotalCost';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ActualDEMECostsEntered';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherSecurity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherQuality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherEnvironmental';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'EnvironmentalAspects';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Probability';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'PotentialSeverity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'PotentialRiskScore2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'PotentialRiskScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DescribeDamage';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Security';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Reputation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Quality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Environment';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'People';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Assets';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'LocationNL';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DetailedDescriptionLocation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ResponsibleManager';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportedByUser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ReportedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'QualityCheckPerformedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentAcceptedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DateReported';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DateAccepted';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ActivityDetails';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ActivitiesBlock4PerformedIncidentTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessTotalActions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProcessOpenActions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'Min2SMARTActionsProposed';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ImmediateActionsTaken';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ExplainProposedActions';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ActionsTakenNL';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentReportTitle';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentRelatedTo';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentNotificationContains4LevelPictures';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentTitle';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CustomIncidentId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'IncidentId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimIncidentOccuredDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimVesselLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimOtherSiteLocationId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimProjectLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimLeadActivityLineId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'FactIncidentId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactIncident', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationHQReview';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'QualityCategory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimEntityLocationId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SWAUsed';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'TypeCommutingIncident';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'LifeSavingRules';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'NonWorkRelatedIncident';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CommutingRelatedIncident';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'QIncidents';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'HRTCombinationALE';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DimCharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CharteredVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'VesselName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'EntityName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'WorldwideEquivalent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InvestigationThirdParty';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'InterventionTeam5555Involved';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'TypeOfDeviation';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'SuppliedMaterialsPartsAndActivities';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'RelatedToSuppliedMaterialsPartsAndActivities';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'RelatedProcessOrActivity';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'QualityIncidentRelatedTo';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'ProjectLifecycle';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'INC_RedIncidentsLTI';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'INC_RedIncidentsHIPO';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'INC_RedIncidentsHICO';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'INC_MajorIncidentsTotal';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'INC_MajorIncidentsHICO';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CSRD_RWC_Own_Workforce';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CSRD_MT_Own_Workforce';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CSRD_LTI_Own_Workforce';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CSRD_Fatality_Own_Workforce';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'CriticalJob';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DWH_INC_MajorIncidentsEnvironmental';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DWH_INC_RedIncidentsEnvironmental';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncident', @level2type = N'COLUMN', @level2name = N'DWH_TRIN';


``
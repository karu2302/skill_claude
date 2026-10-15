# Source: `DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql`
- SHA-256 of original file: `4eb6321b3451214396d6f3ab11cec615064147de3ed27d49067a3895ddd7484b`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingApprise].[Incident] (
    [ActionsTakenNL]                                            NVARCHAR (MAX) NULL,
    [ActivitiesBlock4PerformedIncidentTime]                     NVARCHAR (255) NULL,
    [ActivityDetails]                                           NVARCHAR (MAX) NULL,
    [ActualDEMEcostsentered]                                    NVARCHAR (255) NULL,
    [AdditionalInformation]                                     NVARCHAR (MAX) NULL,
    [Assets]                                                    NVARCHAR (255) NULL,
    [CausedByThirdParty]                                        NVARCHAR (255) NULL,
    [CommentsClassFlag]                                         NVARCHAR (MAX) NULL,
    [CommentsFirstNotification]                                 NVARCHAR (MAX) NULL,
    [CommutingOrOtherNonWorkRelatedIncident]                    NVARCHAR (255) NULL,
    [ConstatationsNL]                                           NVARCHAR (MAX) NULL,
    [CriticalJob]                                               NVARCHAR (255) NULL,
    [CustomProcessID]                                           NVARCHAR (255) NULL,
    [DateAccepted]                                              NVARCHAR (255) NULL,
    [DateReported]                                              NVARCHAR (50)  NULL,
    [DeclarationAvailable]                                      NVARCHAR (5)   NULL,
    [DescribeDamage]                                            NVARCHAR (MAX) NULL,
    [DescriptionOfInjuryInCaseOfLTI]                            NVARCHAR (MAX) NULL,
    [DetailedDescriptionLocation]                               NVARCHAR (MAX) NULL,
    [EntityCode]                                                NVARCHAR (255) NULL,
    [Environment]                                               NVARCHAR (255) NULL,
    [EnvironmentalImpact]                                       NVARCHAR (255) NULL,
    [Explainproposedactions]                                    NVARCHAR (MAX) NULL,
    [ExtraHIPOCategory]                                         NVARCHAR (255) NULL,
    [Fatality]                                                  NVARCHAR (5)   NULL,
    [FirstAid]                                                  NVARCHAR (5)   NULL,
    [HicoDEME]                                                  NVARCHAR (255) NULL,
    [HicoOverall]                                               NVARCHAR (255) NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident]                 NVARCHAR (255) NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident2]                NVARCHAR (255) NULL,
    [HIPO]                                                      NVARCHAR (255) NULL,
    [HRTReasonNA]                                               NVARCHAR (255) NULL,
    [ImmediateActionsTaken]                                     NVARCHAR (MAX) NULL,
    [INC_YN_InvestigationThirdParties]                          NVARCHAR (255) NULL,
    [INC_YN_SWAUsed]                                            NVARCHAR (255) NULL,
    [IncidentAcceptedBy]                                        NVARCHAR (255) NULL,
    [IncidentId]                                                NVARCHAR (255) NULL,
    [IncidentNotificationContains4LevelPictures]                NVARCHAR (50)  NULL,
    [IncidentRelatedTo]                                         NVARCHAR (255) NULL,
    [IncidentReportTitle]                                       NVARCHAR (255) NULL,
    [IncidentTitle]                                             NVARCHAR (255) NULL,
    [IncidentType]                                              NVARCHAR (255) NULL,
    [InvestigationCarriedOutByMultidisciplinaryTeam]            NVARCHAR (5)   NULL,
    [InvestigationHQReview]                                     NVARCHAR (255) NULL,
    [InvestigationLeader]                                       NVARCHAR (255) NULL,
    [InvestigationReportContainsTimeline]                       NVARCHAR (5)   NULL,
    [InvestigationReportDate]                                   NVARCHAR (255) NULL,
    [InvestigationReportIsSignedOffOrApprovedByLocalManagement] NVARCHAR (255) NULL,
    [InvestigationUploaded]                                     NVARCHAR (255) NULL,
    [InvolvedPartiesOfInvestigation]                            NVARCHAR (5)   NULL,
    [Involvement5555]                                           NVARCHAR (255) NULL,
    [LeadActivityLine]                                          NVARCHAR (255) NULL,
    [LifeSavingRules]                                           NVARCHAR (255) NULL,
    [LocationNL]                                                NVARCHAR (MAX) NULL,
    [LostTimeIncident]                                          NVARCHAR (5)   NULL,
    [Min2SMARTActionsProposed]                                  NVARCHAR (5)   NULL,
    [NonWorkRelated]                                            NVARCHAR (255) NULL,
    [NumberCausedByTP]                                          NVARCHAR (255) NULL,
    [NumberOfInjuredPersons]                                    INT            NULL,
    [OfficeLocation]                                            NVARCHAR (255) NULL,
    [OtherSiteLocation]                                         NVARCHAR (255) NULL,
    [People]                                                    NVARCHAR (255) NULL,
    [PotentialLTI]                                              NVARCHAR (5)   NULL,
    [PotentialRiskScore]                                        NVARCHAR (255) NULL,
    [PotentialRiskScore2]                                       NVARCHAR (50)  NULL,
    [PotentialSeverity]                                         NVARCHAR (255) NULL,
    [Probability]                                               NVARCHAR (255) NULL,
    [processCharteredVesselCode]                                NVARCHAR (255) NULL,
    [ProcessCloser]                                             NVARCHAR (255) NULL,
    [ProcessDate]                                               NVARCHAR (255) NULL,
    [ProcessDescription]                                        NVARCHAR (MAX) NULL,
    [ProcessDetailedLocation]                                   NVARCHAR (MAX) NULL,
    [ProcessError]                                              NVARCHAR (255) NULL,
    [ProcessOpenActions]                                        NVARCHAR (255) NULL,
    [ProcessOtherSiteCode]                                      NVARCHAR (255) NULL,
    [ProcessProjectcode]                                        NVARCHAR (255) NULL,
    [ProcessSubject]                                            NVARCHAR (255) NULL,
    [ProcessSubstatus]                                          NVARCHAR (255) NULL,
    [ProcessTotalActions]                                       NVARCHAR (255) NULL,
    [ProcessType]                                               NVARCHAR (255) NULL,
    [ProcessUrlID]                                              NVARCHAR (255) NULL,
    [ProcessVesselCode]                                         NVARCHAR (255) NULL,
    [ProcessVesselLocation]                                     NVARCHAR (255) NULL,
    [ProjectLifecycle]                                          NVARCHAR (255) NULL,
    [ProjectLocation]                                           NVARCHAR (255) NULL,
    [QHSESResponsibleHQ]                                        NVARCHAR (255) NULL,
    [QHSESResponsibleHQOffice]                                  NVARCHAR (255) NULL,
    [QHSESResponsibleHQOtherSite]                               NVARCHAR (255) NULL,
    [QHSESResponsibleHQProject]                                 NVARCHAR (255) NULL,
    [QHSESResponsibleHQVessel]                                  NVARCHAR (255) NULL,
    [QHSESResponsiblelocal]                                     NVARCHAR (255) NULL,
    [QHSESResponsiblelocalOffice]                               NVARCHAR (255) NULL,
    [QHSESResponsiblelocalOtherSite]                            NVARCHAR (255) NULL,
    [QHSESResponsiblelocalProject]                              NVARCHAR (255) NULL,
    [QHSESResponsiblelocalVessel]                               NVARCHAR (255) NULL,
    [Quality]                                                   NVARCHAR (255) NULL,
    [QualityCategory]                                           NVARCHAR (255) NULL,
    [QualityCheckPerformedBy]                                   NVARCHAR (255) NULL,
    [QualityIncidentRelatedTo]                                  NVARCHAR (255) NULL,
    [ReasonchangeofHIPOclassification]                          NVARCHAR (MAX) NULL,
    [ReasonForCancellingRejecting]                              NVARCHAR (MAX) NULL,
    [ReasonPictureLevel1NA]                                     NVARCHAR (MAX) NULL,
    [ReasonPictureLevel2NA]                                     NVARCHAR (MAX) NULL,
    [ReasonPictureLevel3NA]                                     NVARCHAR (MAX) NULL,
    [ReasonPictureLevel4NA]                                     NVARCHAR (MAX) NULL,
    [RelatedProcessOrActivity]                                  NVARCHAR (255) NULL,
    [RelatedToSuppliedMaterialsPartsAndActivities]              NVARCHAR (255) NULL,
    [ReOpenComments]                                            NVARCHAR (MAX) NULL,
    [ReportableToAuthorities]                                   NVARCHAR (5)   NULL,
    [ReportableToClassAndFlagstate]                             NVARCHAR (5)   NULL,
    [ReportedBy]                                                NVARCHAR (255) NULL,
    [ReportedByUser]                                            NVARCHAR (255) NULL,
    [ReportedOnBehalfOfDEMEEmployee]                            NVARCHAR (255) NULL,
    [ReportedOnBehalfOfThirdParty]                              NVARCHAR (255) NULL,
    [ReportInYourOwnName]                                       NVARCHAR (5)   NULL,
    [Reputation]                                                NVARCHAR (255) NULL,
    [ResponsibleManager]                                        NVARCHAR (255) NULL,
    [RestrictedWork]                                            NVARCHAR (5)   NULL,
    [ReviewActionsTaken]                                        NVARCHAR (MAX) NULL,
    [ReviewDamage]                                              NVARCHAR (MAX) NULL,
    [ReviewdamageNL]                                            NVARCHAR (MAX) NULL,
    [ReviewDescription]                                         NVARCHAR (MAX) NULL,
    [ReviewDescriptionNL]                                       NVARCHAR (MAX) NULL,
    [RootCausesAnalysisHasDefinedMin2RootCauses]                NVARCHAR (5)   NULL,
    [Security]                                                  NVARCHAR (255) NULL,
    [SpecifyOtherEnvironmental]                                 NVARCHAR (255) NULL,
    [SpecifyOtherHIPOCategory]                                  NVARCHAR (255) NULL,
    [SpecifyOtherQuality]                                       NVARCHAR (255) NULL,
    [SpecifyOtherSecurity]                                      NVARCHAR (255) NULL,
    [Status]                                                    NVARCHAR (255) NULL,
    [StatusLevel1Picture]                                       NVARCHAR (255) NULL,
    [StatusLevel2Picture]                                       NVARCHAR (255) NULL,
    [StatusLevel3Picture]                                       NVARCHAR (255) NULL,
    [StatusLevel4Picture]                                       NVARCHAR (255) NULL,
    [SuppliedMaterialsPartsAndActivities]                       NVARCHAR (255) NULL,
    [SupportingServiceCode]                                     NVARCHAR (255) NULL,
    [TDfleetHQZwijndrecht]                                      NVARCHAR (255) NULL,
    [TheftOf]                                                   NVARCHAR (255) NULL,
    [TotalCost]                                                 NVARCHAR (50)  NULL,
    [TypeCommutingIncident]                                     NVARCHAR (255) NULL,
    [TypeOfDeviation]                                           NVARCHAR (255) NULL,
    [Vessel]                                                    NVARCHAR (255) NULL,
    [VesselLocation]                                            NVARCHAR (255) NULL
);








































GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'VesselLocation';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TotalCost', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'TotalCost';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TheftOf', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'TheftOf';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TD/fleet/HQ Zwijndrecht', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'TDfleetHQZwijndrecht';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SupportingServiceCode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'StatusLevel4Picture', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'StatusLevel4Picture';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'StatusLevel3Picture', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'StatusLevel3Picture';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'StatusLevel2Picture', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'StatusLevel2Picture';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'StatusLevel1Picture', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'StatusLevel1Picture';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Status', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SpecifyOtherSecurity', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherSecurity';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SpecifyOtherQuality', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherQuality';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SpecifyOtherHIPOCategory', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherHIPOCategory';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SpecifyOtherEnvironmental', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SpecifyOtherEnvironmental';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Security', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Security';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'RootCausesAnalysisHasDefinedMin2RootCauses', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'RootCausesAnalysisHasDefinedMin2RootCauses';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReviewDescriptionNL', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReviewDescriptionNL';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReviewDescription', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReviewDescription';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReviewdamageNL', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReviewdamageNL';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReviewDamage', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReviewDamage';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReviewActionsTaken', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReviewActionsTaken';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'RestrictedWork', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'RestrictedWork';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ResponsibleManager', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ResponsibleManager';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Reputation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Reputation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportInYourOwnName', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportInYourOwnName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportedOnbehalfOfThirdParty', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportedOnBehalfOfThirdParty';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportedOnbehalfOfDEMEEmployee', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportedOnBehalfOfDEMEEmployee';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportedBy', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportedByUser';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportedBy', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportedBy';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportableToClassAndFlagstate', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportableToClassAndFlagstate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReportableToAuthorities', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReportableToAuthorities';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReOpenComments', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReOpenComments';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReasonpictureLevel4NA', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel4NA';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReasonpictureLevel3NA', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel3NA';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReasonpictureLevel2NA', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel2NA';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReasonpictureLevel1NA', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonPictureLevel1NA';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Reasonforcancelling/rejecting', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonForCancellingRejecting';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ReasonchangeofHIPOclassification', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ReasonchangeofHIPOclassification';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QualityCheckPerformedBy', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QualityCheckPerformedBy';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QualityCategory', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QualityCategory';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Quality', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Quality';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(local)Vessel', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsiblelocalVessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(local)Project', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsiblelocalProject';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(local)OtherSite', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsiblelocalOtherSite';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(local)Office', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsiblelocalOffice';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(local)', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsiblelocal';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(HQ)Vessel', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsibleHQVessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(HQ)Project', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsibleHQProject';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(HQ)OtherSite', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsibleHQOtherSite';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(HQ)Office', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsibleHQOffice';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSESResponsible(HQ)', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QHSESResponsibleHQ';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProjectLocation';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessVesselCode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessVesselCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessUrlID', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessUrlID';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessType', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessTotalActions', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessTotalActions';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessSubstatus', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessSubstatus';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessSubject', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessSubject';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessProjectcode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessProjectcode';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessOtherSiteCode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessOtherSiteCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessOpenActions', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessOpenActions';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessError', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessError';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessDescription', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessDescription';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessCloser', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Probability', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Probability';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PotentialSeverity', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'PotentialSeverity';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PotentialRiskScore', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'PotentialRiskScore2';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PotentialRiskScore', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'PotentialRiskScore';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'PotentialLTI', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'PotentialLTI';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'People', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'People';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'OtherSiteLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'OtherSiteLocation';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'OfficeLocationCode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'OfficeLocation';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NumberOfInjuredPersons', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'NumberOfInjuredPersons';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NumbercausedbyTP', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'NumberCausedByTP';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Min2SMARTActionsProposed', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Min2SMARTActionsProposed';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LostTimeIncident', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'LostTimeIncident';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LocationNL', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'LocationNL';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LeadActivityLine', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'LeadActivityLine';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvolvedPartiesOfInvestigation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvolvedPartiesOfInvestigation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Investigationuploaded', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationUploaded';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationReportIsSignedOffOrApprovedByLocalManagement', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationReportIsSignedOffOrApprovedByLocalManagement';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationReportContainsTimeline', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationReportContainsTimeline';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationLeader', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationLeader';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationCarriedOutByMultidisciplinaryTeam', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationCarriedOutByMultidisciplinaryTeam';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'IncidentType', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'IncidentTitle', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentTitle';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Incidentreporttitle', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentReportTitle';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Classification', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentRelatedTo';




GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'IncidentNotificationContains4LevelPictures', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentNotificationContains4LevelPictures';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ID', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Incidentacceptedby', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'IncidentAcceptedBy';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ImmediateActionsTaken', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ImmediateActionsTaken';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HRTReasonNA', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HRTReasonNA';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HIPO', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HIPO';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HighRiskTasksPerformedAtTheTimeOfIncident2', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HighRiskTasksPerformedAtTheTimeOfIncident2';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HighRiskTasksPerformedAtTheTimeOfIncident', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HighRiskTasksPerformedAtTheTimeOfIncident';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HicoOverall', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HicoOverall';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'HicoDEME', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'HicoDEME';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'FirstAid', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'FirstAid';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Fatality', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Fatality';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ExtraHIPOCategory', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ExtraHIPOCategory';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Explain proposed actions', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Explainproposedactions';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EnvironmentalImpact', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'EnvironmentalImpact';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Environment', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Environment';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'EntityCode', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'EntityCode';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DetailedDescriptionLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DetailedDescriptionLocation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DescriptionOfInjuryInCaseOfLTI', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DescriptionOfInjuryInCaseOfLTI';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Describedamage', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DescribeDamage';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DeclarationAvailable', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DeclarationAvailable';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CustomProcessID', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CustomProcessID';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ConstatationsNL', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ConstatationsNL';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Isthisacommutingorothernonworkrelatedincident?', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CommutingOrOtherNonWorkRelatedIncident';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CommentsFirstNotification', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CommentsFirstNotification';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Comments', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CommentsClassFlag';


GO





GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Causedbythirdparty', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CausedByThirdParty';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Assets', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Assets';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'AdditionalInformation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'AdditionalInformation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ActualDEMEcostsentered', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ActualDEMEcostsentered';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ActivityDetails', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ActivityDetails';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ActivitiesBlock4PerformedIncidentTime', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ActivitiesBlock4PerformedIncidentTime';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ActionsTakenNL', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ActionsTakenNL';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Incident', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationHQReview', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationHQReview';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'INC_YN_SWAUsed', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'INC_YN_SWAUsed';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TypeCommutingIncident', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'TypeCommutingIncident';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'LifeSavingRules', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'LifeSavingRules';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Isthisacommutingorothernonworkrelatedincident?', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'NonWorkRelated';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessCharteredVessel', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'processCharteredVesselCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessDate', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessDate';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'InvestigationReportDate', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'InvestigationReportDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DateReported', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DateReported';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'DateAccepted', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'DateAccepted';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'INC_YN_InvestigationThirdParties', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'INC_YN_InvestigationThirdParties';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Involvement5555', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Involvement5555';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Vessel', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'Vessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessVesselLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessVesselLocation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProcessDetailedLocation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProcessDetailedLocation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TypeOfDeviation', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'TypeOfDeviation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'SuppliedMaterialsPartsAndActivities', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'SuppliedMaterialsPartsAndActivities';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'RelatedToSuppliedMaterialsPartsAndActivities', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'RelatedToSuppliedMaterialsPartsAndActivities';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'RelatedProcessOrActivity', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'RelatedProcessOrActivity';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QualityIncidentRelatedTo', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'QualityIncidentRelatedTo';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'ProjectLifecycle', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'ProjectLifecycle';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'CriticalJob', @level0type = N'SCHEMA', @level0name = N'StagingApprise', @level1type = N'TABLE', @level1name = N'Incident', @level2type = N'COLUMN', @level2name = N'CriticalJob';


````
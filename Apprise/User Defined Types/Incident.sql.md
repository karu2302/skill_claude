# Source: `DBs/AzureSingleDB/Apprise/User Defined Types/Incident.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/Apprise/User Defined Types/Incident.sql`
- SHA-256 of original file: `50f707486d2bb03e54c1ee5783981d40e4510d71b95cc672cd63c175f3b5b464`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [Apprise].[Incident] AS TABLE (
    [Status]                                                    NVARCHAR (255)  NULL,
    [IncidentId]                                                NVARCHAR (255)  NULL,
    [DateAccepted]                                              NVARCHAR (255)  NULL,
    [InvestigationReportDate]                                   NVARCHAR (255)  NULL,
    [DateReported]                                              NVARCHAR (50)   NULL,
    [EnvironmentalImpact]                                       NVARCHAR (255)  NULL,
    [TheftOf]                                                   NVARCHAR (255)  NULL,
    [Assets]                                                    NVARCHAR (255)  NULL,
    [Environment]                                               NVARCHAR (255)  NULL,
    [People]                                                    NVARCHAR (255)  NULL,
    [Quality]                                                   NVARCHAR (255)  NULL,
    [Reputation]                                                NVARCHAR (255)  NULL,
    [Security]                                                  NVARCHAR (255)  NULL,
    [HicoDEME]                                                  NVARCHAR (255)  NULL,
    [ExtraHIPOCategory]                                         NVARCHAR (255)  NULL,
    [HicoOverall]                                               NVARCHAR (255)  NULL,
    [PotentialRiskScore]                                        NVARCHAR (255)  NULL,
    [QualityCategory]                                           NVARCHAR (255)  NULL,
    [RelatedProcessOrActivity]                                  NVARCHAR (255)  NULL,
    [ProjectLifecycle]                                          NVARCHAR (255)  NULL,
    [QualityIncidentRelatedTo]                                  NVARCHAR (255)  NULL,
    [Probability]                                               NVARCHAR (255)  NULL,
    [PotentialSeverity]                                         NVARCHAR (255)  NULL,
    [StatusLevel1Picture]                                       NVARCHAR (255)  NULL,
    [StatusLevel2Picture]                                       NVARCHAR (255)  NULL,
    [StatusLevel3Picture]                                       NVARCHAR (255)  NULL,
    [StatusLevel4Picture]                                       NVARCHAR (255)  NULL,
    [TDfleetHQZwijndrecht]                                      NVARCHAR (255)  NULL,
    [TypeCommutingIncident]                                     NVARCHAR (255)  NULL,
    [IncidentType]                                              NVARCHAR (255)  NULL,
    [ActivitiesBlock4PerformedIncidentTime]                     NVARCHAR (255)  NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident]                 NVARCHAR (255)  NULL,
    [HighRiskTasksPerformedAtTheTimeOfIncident2]                NVARCHAR (255)  NULL,
    [LifeSavingRules]                                           NVARCHAR (255)  NULL,
    [SuppliedMaterialsPartsAndActivities]                       NVARCHAR (255)  NULL,
    [TypeOfDeviation]                                           NVARCHAR (255)  NULL,
    [NumberCausedByTP]                                          NVARCHAR (255)  NULL,
    [NumberOfInjuredPersons]                                    INT             NULL,
    [PotentialRiskScore2]                                       NVARCHAR (50)   NULL,
    [TotalCost]                                                 NVARCHAR (50)   NULL,
    [ActualDEMEcostsentered]                                    NVARCHAR (255)  NULL,
    [ActionsTakenNL]                                            NVARCHAR (MAX)  NULL,
    [ActivityDetails]                                           NVARCHAR (MAX)  NULL,
    [AdditionalInformation]                                     NVARCHAR (MAX)  NULL,
    [CommentsClassFlag]                                         NVARCHAR (MAX)  NULL,
    [CommentsFirstNotification]                                 NVARCHAR (MAX)  NULL,
    [ConstatationsNL]                                           NVARCHAR (MAX)  NULL,
    [DescribeDamage]                                            NVARCHAR (MAX)  NULL,
    [DetailedDescriptionLocation]                               NVARCHAR (MAX)  NULL,
    [ImmediateActionsTaken]                                     NVARCHAR (MAX)  NULL,
    [LocationNL]                                                NVARCHAR (MAX)  NULL,
    [DescriptionOfInjuryInCaseOfLTI]                            NVARCHAR (MAX)  NULL,
    [ReasonchangeofHIPOclassification]                          NVARCHAR (MAX)  NULL,
    [ReasonPictureLevel1NA]                                     NVARCHAR (MAX)  NULL,
    [ReasonPictureLevel2NA]                                     NVARCHAR (MAX)  NULL,
    [ReasonPictureLevel3NA]                                     NVARCHAR (MAX)  NULL,
    [ReasonPictureLevel4NA]                                     NVARCHAR (MAX)  NULL,
    [ReasonForCancellingRejecting]                              NVARCHAR (MAX)  NULL,
    [ReOpenComments]                                            NVARCHAR (MAX)  NULL,
    [Explainproposedactions]                                    NVARCHAR (MAX)  NULL,
    [ReviewActionsTaken]                                        NVARCHAR (MAX)  NULL,
    [ReviewDescription]                                         NVARCHAR (MAX)  NULL,
    [ReviewDamage]                                              NVARCHAR (MAX)  NULL,
    [ReviewdamageNL]                                            NVARCHAR (MAX)  NULL,
    [ReviewDescriptionNL]                                       NVARCHAR (MAX)  NULL,
    [HRTReasonNA]                                               NVARCHAR (255)  NULL,
    [IncidentRelatedTo]                                         NVARCHAR (255)  NULL,
    [SpecifyOtherEnvironmental]                                 NVARCHAR (255)  NULL,
    [HIPO]                                                      NVARCHAR (255)  NULL,
    [SpecifyOtherHIPOCategory]                                  NVARCHAR (255)  NULL,
    [IncidentReportTitle]                                       NVARCHAR (255)  NULL,
    [LeadActivityLine]                                          NVARCHAR (255)  NULL,
    [SpecifyOtherQuality]                                       NVARCHAR (255)  NULL,
    [ReportedOnBehalfOfThirdParty]                              NVARCHAR (255)  NULL,
    [SpecifyOtherSecurity]                                      NVARCHAR (255)  NULL,
    [IncidentTitle]                                             NVARCHAR (255)  NULL,
    [IncidentAcceptedBy]                                        NVARCHAR (255)  NULL,
    [InvestigationLeader]                                       NVARCHAR (255)  NULL,
    [QHSESResponsibleHQ]                                        NVARCHAR (255)  NULL,
    [QHSESResponsiblelocal]                                     NVARCHAR (255)  NULL,
    [QHSESResponsibleHQOffice]                                  NVARCHAR (255)  NULL,
    [QHSESResponsiblelocalOffice]                               NVARCHAR (255)  NULL,
    [QHSESResponsibleHQOtherSite]                               NVARCHAR (255)  NULL,
    [QHSESResponsiblelocalOtherSite]                            NVARCHAR (255)  NULL,
    [QHSESResponsibleHQProject]                                 NVARCHAR (255)  NULL,
    [QHSESResponsiblelocalProject]                              NVARCHAR (255)  NULL,
    [QHSESResponsibleHQVessel]                                  NVARCHAR (255)  NULL,
    [QHSESResponsiblelocalVessel]                               NVARCHAR (255)  NULL,
    [QualityCheckPerformedBy]                                   NVARCHAR (255)  NULL,
    [ReportedOnBehalfOfDEMEEmployee]                            NVARCHAR (255)  NULL,
    [ReportedByUser]                                            NVARCHAR (255)  NULL,
    [ResponsibleManager]                                        NVARCHAR (255)  NULL,
    [IncidentNotificationContains4LevelPictures]                NVARCHAR (50)   NULL,
    [ReportableToAuthorities]                                   NVARCHAR (5)    NULL,
    [CausedByThirdParty]                                        NVARCHAR (255)  NULL,
    [ReportableToClassAndFlagstate]                             NVARCHAR (5)    NULL,
    [Fatality]                                                  NVARCHAR (5)    NULL,
    [FirstAid]                                                  NVARCHAR (5)    NULL,
    [LostTimeIncident]                                          NVARCHAR (5)    NULL,
    [RestrictedWork]                                            NVARCHAR (5)    NULL,
    [CommutingOrOtherNonWorkRelatedIncident]                    NVARCHAR (255)  NULL,
    [CriticalJob]                                               NVARCHAR (255)  NULL,
    [InvolvedPartiesOfInvestigation]                            NVARCHAR (5)    NULL,
    [InvestigationReportIsSignedOffOrApprovedByLocalManagement] NVARCHAR (255)  NULL,
    [InvestigationHQReview]                                     NVARCHAR (255)  NULL,
    [INC_YN_InvestigationThirdParties]                          NVARCHAR (255)  NULL,
    [InvestigationUploaded]                                     NVARCHAR (255)  NULL,
    [Involvement5555]                                           NVARCHAR (255)  NULL,
    [PotentialLTI]                                              NVARCHAR (5)    NULL,
    [Min2SMARTActionsProposed]                                  NVARCHAR (5)    NULL,
    [RootCausesAnalysisHasDefinedMin2RootCauses]                NVARCHAR (5)    NULL,
    [InvestigationCarriedOutByMultidisciplinaryTeam]            NVARCHAR (5)    NULL,
    [NonWorkRelated]                                            NVARCHAR (255)  NULL,
    [RelatedToSuppliedMaterialsPartsAndActivities]              NVARCHAR (255)  NULL,
    [ReportInYourOwnName]                                       NVARCHAR (5)    NULL,
    [DeclarationAvailable]                                      NVARCHAR (5)    NULL,
    [INC_YN_SWAUsed]                                            NVARCHAR (255)  NULL,
    [InvestigationReportContainsTimeline]                       NVARCHAR (5)    NULL,
    [processCharteredVesselCode]                                NVARCHAR (255)  NULL,
    [ProcessCloser]                                             NVARCHAR (255)  NULL,
    [CustomProcessID]                                           NVARCHAR (255)  NULL,
    [ProcessDate]                                               NVARCHAR (255)  NULL,
    [ProcessDescription]                                        NVARCHAR (MAX)  NULL,
    [ProcessDetailedLocation]                                   NVARCHAR (MAX)  NULL,
    [EntityCode]                                                NVARCHAR (255)  NULL,
    [ProcessError]                                              NVARCHAR (255)  NULL,
    [OfficeLocation]                                            NVARCHAR (255)  NULL,
    [ProcessOpenActions]                                        NVARCHAR (255)  NULL,
    [ReportedBy]                                                NVARCHAR (255)  NULL,
    [ProcessOtherSiteCode]                                      NVARCHAR (255)  NULL,
    [OtherSiteLocation]                                         NVARCHAR (255)  NULL,
    [ProcessProjectcode]                                        NVARCHAR (255)  NULL,
    [ProjectLocation]                                           NVARCHAR (255)  NULL,
    [ProcessSubject]                                            NVARCHAR (4000) NULL,
    [ProcessSubstatus]                                          NVARCHAR (255)  NULL,
    [SupportingServiceCode]                                     NVARCHAR (255)  NULL,
    [ProcessTotalActions]                                       NVARCHAR (255)  NULL,
    [ProcessType]                                               NVARCHAR (255)  NULL,
    [ProcessUrlID]                                              NVARCHAR (255)  NULL,
    [Vessel]                                                    NVARCHAR (255)  NULL,
    [ProcessVesselCode]                                         NVARCHAR (255)  NULL,
    [ProcessVesselLocation]                                     NVARCHAR (255)  NULL,
    [VesselLocation]                                            NVARCHAR (255)  NULL);












































````
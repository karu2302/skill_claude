# Source: `DBs/AzureSingleDB/DataStore4/Views/vwIncident.sql`

- Original repository path: `DBs/AzureSingleDB/DataStore4/Views/vwIncident.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `36dfaa17fb004dc2dfe2ff062ffa94fbe94e9c60753499f4d8cfae56094c6126`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql






CREATE VIEW [DataStore4].[vwIncident] AS 

SELECT
	  IncidentId
	, CustomIncidentId
	, ProjectId
	, VesselId
	, OtherSiteId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, VesselLocationCode
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
	, LeadActivityLineId
	, IncidentType
	, IncidentTitle
	, IncidentNotificationContains4LevelPictures
	, IncidentRelatedTo
	, IncidentReportTitle
	, ActionsTakenNL
	, ExplainProposedActions
	, ImmediateActionsTaken
	, Min2SMARTActionsProposed
	, ProcessOpenActions
	, ProcessTotalActions
	, ActivitiesBlock4PerformedIncidentTime
	, ActivityDetails
	, DateAccepted
	, DateReported
	, DimIncidentOccuredDateId
	, IncidentDateTime
	, IncidentAcceptedBy
	, ProcessCloser
	, QualityCheckPerformedBy
	, ReportedBy
	, ReportedByUser
	, ResponsibleManager
	, DetailedDescriptionLocation
	, LocationNL
	, Assets
	, People
	, Environment
	, Quality
	, QualityCategory
	, Reputation
	, Security
	, DescribeDamage
	, PotentialRiskScore
	, PotentialRiskScore2
	, PotentialSeverity
	, Probability
	, EnvironmentalAspects
	, SpecifyOtherEnvironmental
	, SpecifyOtherQuality
	, SpecifyOtherSecurity
	, ActualDEMECostsEntered
	, TotalCost
	, HicoDEME
	, HicoOverall
	, DescriptionOfInjuryInCaseOfLTI
	, Fatality
	, FirstAid
	, PotentialLTI
	, HIPO
	, ReasonChangeHIPOClassification
	, ExtraHIPOCategory
	, SpecifyOtherHIPOCategory
	, ReviewDamage
	, ReviewDamageNL
	, ReviewDescription
	, ReviewDescriptionNL
	, ReviewActionsTaken
	, CausedByThirdParty
	, InvestigationCarriedOutByMultidisciplinaryTeam
	, InvestigationLeader
	, InvestigationReportContainsTimeline
	, InvestigationReportDate
	, Investigation
	, InvestigationReportIsSignedOffOrApprovedByLocalManagement
	, InvestigationUploaded
	, InvolvedPartiesOfInvestigation
	, InvestigationHQReview
	, ProcessDescription
	, ProcessError
	, ProcessSubject
	, Status
	, Substatus
	, ProcessType
	, ProcessURLID
	, SWAUsed
	, AdditionalInformation
	, CommentsClassFlag
	, CommentsFirstNotification
	, ConstatationsNL
	, DeclarationAvailable
	, HighRiskTasksPerformedAtTheTimeOfIncident
	, HighRiskTasksPerformedAtTheTimeOfIncident2
	, HRTReasonNA
	, CommutingRelatedIncident
	, NonWorkRelatedIncident
	, LostTimeIncident
	, LTITypeWorldwide
	, NumberCausedByTP
	, ReasonForCancellingRejecting
	, ReasonPictureLevel1NA
	, ReasonPictureLevel2NA
	, ReasonPictureLevel3NA
	, ReasonPictureLevel4NA
	, ReOpenComments
	, ReportableToAuthorities
	, ReportableToClassAndFlagstate
	, ReportedOnBehalfOfDEMEEmployee
	, ReportedOnBehalfOfThirdParty
	, ReportInYourOwnName
	, RestrictedWork
	, RootCausesAnalysisHasDefinedMin2RootCauses
	, StatusLevel1Picture
	, StatusLevel2Picture
	, StatusLevel3Picture
	, StatusLevel4Picture
	, TDfleetHQZwijndrecht
	, TheftOf
	, DataSource
	, QCSelected
	, EIncidents
	, QIncidents
    , RedIncidents
	, HIPORed
    , EIncidentRed
    , EstimatedCost
	, ReportedInTime
	, TypeCommutingIncident
	, LifeSavingRules
	, HRTCombinationALE
	, WorldwideEquivalent
	, SupportingServiceTibcoIdentifier
	, InvestigationThirdParty
	, InterventionTeam5555Involved
	,CriticalJob
	,ProjectLifecycle
	,QualityIncidentRelatedTo
	,RelatedToSuppliedMaterialsPartsAndActivities
	,SuppliedMaterialsPartsAndActivities
	,RelatedProcessOrActivity
	,TypeOfDeviation
	, CASE 
		WHEN [HicoDEME] LIKE '%hico cat 4%'
          OR [HicoDEME] LIKE '%hico cat 5%'
          OR [HicoDEME] LIKE '%hico cat 6%'
        THEN 1
        ELSE 0
    END AS INC_RedIncidentsHICO

	, CASE
        WHEN [HIPO] = 1
         AND [PotentialRiskScore2] > 15
        THEN 1
        ELSE 0
    END AS INC_RedIncidentsHIPO

	, CASE
		WHEN [HicoDEME] LIKE '%hico cat 3%'
		  OR [HicoDEME] LIKE '%hico cat 4%'
          OR [HicoDEME] LIKE '%hico cat 5%'
          OR [HicoDEME] LIKE '%hico cat 6%'
        THEN 1
        ELSE 0
    END AS INC_MajorIncidentsHICO
  FROM DataStore3.Incident
``
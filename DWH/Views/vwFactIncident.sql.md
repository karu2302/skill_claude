# Source: `DBs/AzureSingleDB/DWH/Views/vwFactIncident.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactIncident.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `e168b33638ac8c3a629449a3bfa2c7034ef23d78947e15cc214bede8f966b32c`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql



CREATE VIEW [DWH].[vwFactIncident] AS 

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
	, INC_RedIncidentsHICO
	, INC_RedIncidentsHIPO
	, INC_MajorIncidentsHICO
	,CriticalJob
	,ProjectLifecycle
	,QualityIncidentRelatedTo
	,RelatedToSuppliedMaterialsPartsAndActivities
	,SuppliedMaterialsPartsAndActivities
	,RelatedProcessOrActivity
	,TypeOfDeviation
	       , CASE 
        WHEN CommutingRelatedIncident = 0 
         AND NonWorkRelatedIncident = 0
         AND EXISTS (
                SELECT 1
                FROM DataStore4.IncidentIP ip
                WHERE ip.IncidentId = inc.IncidentId
                  AND ip.ClassificationInjury = 'Fatality'
                  AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                  AND ip.UndertakingsSite = 1
             )
        THEN 1
        ELSE 0
      END AS CSRD_Fatality_Own_Workforce

    , CASE 
        WHEN CommutingRelatedIncident = 0 
         AND NonWorkRelatedIncident = 0
         AND EXISTS (
                SELECT 1
                FROM DataStore4.IncidentIP ip
                WHERE ip.IncidentId = inc.IncidentId
                  AND ip.ClassificationInjury = 'Lost Time Incident'
                  AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                  AND (ip.LTITypeWorldwide <> 'Disapproved' OR ip.LTITypeWorldwide IS NULL)
             )
        THEN 1
        ELSE 0
      END AS CSRD_LTI_Own_Workforce

    , CASE 
        WHEN CommutingRelatedIncident = 0 
         AND NonWorkRelatedIncident = 0
         AND EXISTS (
                SELECT 1
                FROM DataStore4.IncidentIP ip
                WHERE ip.IncidentId = inc.IncidentId
                  AND ip.ClassificationInjury = 'Restricted Work'
                  AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                  AND (ip.LTITypeWorldwide <> 'Disapproved' OR ip.LTITypeWorldwide IS NULL)
             )
        THEN 1
        ELSE 0
      END AS CSRD_RWC_Own_Workforce

    , CASE 
        WHEN CommutingRelatedIncident = 0 
         AND NonWorkRelatedIncident = 0
         AND EXISTS (
                SELECT 1
                FROM DataStore4.IncidentIP ip
                WHERE ip.IncidentId = inc.IncidentId
                  AND ip.ClassificationInjury = 'Lost Time Incident'
                  AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                  AND (ip.LTITypeWorldwide <> 'Disapproved' OR ip.LTITypeWorldwide IS NULL)
                  AND ip.WorldwideEquivalent = 1
             )
        THEN 1
        ELSE 0
      END AS INC_RedIncidentsLTI

    , CASE 
        WHEN CommutingRelatedIncident = 0 
         AND NonWorkRelatedIncident = 0
         AND EXISTS (
                SELECT 1
                FROM DataStore4.IncidentIP ip
                WHERE ip.IncidentId = inc.IncidentId
                  AND ip.ClassificationInjuryCSRD = 'Medical Treatment'
                  AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                  AND (ip.LTITypeWorldwide <> 'Disapproved' OR ip.LTITypeWorldwide IS NULL)
             )
        THEN 1
        ELSE 0
      END AS CSRD_MT_Own_Workforce

    , CASE 
        WHEN HIPO = 1
          OR HicoDEME LIKE '%hico cat 3%'
          OR HicoDEME LIKE '%hico cat 4%'
          OR HicoDEME LIKE '%hico cat 5%'
          OR HicoDEME LIKE '%hico cat 6%'
          OR (HIPO = 1 AND EIncidents = 1)
          OR (HicoDEME = 'HICO Cat 3 (10.000 - 100.000)' AND EIncidents = 1)
          OR (HicoDEME = 'HICO Cat 4 (100.000 - 1.000.000)' AND EIncidents = 1)
          OR (HicoDEME = 'HICO Cat 5 (1.000.000 - 10.000.000)' AND EIncidents = 1)
          OR (HicoDEME = 'HICO Cat 6 (>10.000.000)' AND EIncidents = 1)
          OR (CommutingRelatedIncident = 0 AND NonWorkRelatedIncident = 0
    	AND EXISTS (
           	   SELECT 1
           	   FROM DataStore4.IncidentIP ip
			   WHERE ip.IncidentId = inc.IncidentId
			   AND ip.ClassificationInjury = 'Lost Time Incident'
			   AND ip.EmployeeCategorization LIKE '%Own Workforce%'
			   AND (ip.LTITypeWorldwide <> 'Disapproved' OR ip.LTITypeWorldwide IS NULL)
           )
	   )
        THEN 1
        ELSE 0
      END AS INC_MajorIncidentsTotal

	, CASE
		WHEN EIncidentRed = 'E-HIPO-HICO'
    	THEN 1
    	ELSE 0
  	  END AS DWH_INC_MajorIncidentsEnvironmental
  
    , CASE
    	WHEN EIncidentRed LIKE '%red%'
    	THEN 1
    	ELSE 0
      END AS DWH_INC_RedIncidentsEnvironmental

   ,  CASE
  		WHEN
       (
          CommutingRelatedIncident = 0
          AND NonWorkRelatedIncident = 0
          AND EXISTS (
              SELECT 1
              FROM DataStore4.IncidentIP ip
              WHERE ip.IncidentId = inc.IncidentId
                AND ip.ClassificationInjury = 'Fatality'
                AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                AND ip.UndertakingsSite = 1
          )
       )

    OR

       (
          CommutingRelatedIncident = 0
          AND NonWorkRelatedIncident = 0
          AND EXISTS (
              SELECT 1
              FROM DataStore4.IncidentIP ip
              WHERE ip.IncidentId = inc.IncidentId
                AND ip.ClassificationInjury = 'Lost Time Incident'
                AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                AND (
                      ip.LTITypeWorldwide <> 'Disapproved'
                      OR ip.LTITypeWorldwide IS NULL
                    )
          )
       )

    OR

       (
          CommutingRelatedIncident = 0
          AND NonWorkRelatedIncident = 0
          AND EXISTS (
              SELECT 1
              FROM DataStore4.IncidentIP ip
              WHERE ip.IncidentId = inc.IncidentId
                AND ip.ClassificationInjuryCSRD = 'Medical Treatment'
                AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                AND (
                      ip.LTITypeWorldwide <> 'Disapproved'
                      OR ip.LTITypeWorldwide IS NULL
                    )
          )
       )

    OR

       (
          CommutingRelatedIncident = 0
          AND NonWorkRelatedIncident = 0
          AND EXISTS (
              SELECT 1
              FROM DataStore4.IncidentIP ip
              WHERE ip.IncidentId = inc.IncidentId
                AND ip.ClassificationInjury = 'Restricted Work'
                AND ip.EmployeeCategorization LIKE '%Own Workforce%'
                AND (
                      ip.LTITypeWorldwide <> 'Disapproved'
                      OR ip.LTITypeWorldwide IS NULL
                    )
          )
       )

  THEN 1
  ELSE 0
END AS DWH_TRIN

  FROM DataStore4.Incident inc
``
# Source: `DBs/AzureSingleDB/DWH/Views/vwFactGreenInitiative.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactGreenInitiative.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `8527d3f239a5bdd40ac12587fc16a6c53a5adb9340491541f3d585215e093366`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql







CREATE VIEW [DWH].[vwFactGreenInitiative] AS

SELECT
	--BUSINESS KEYS
	  GreenInitiativeId
	, CustomGreenInitiativeId   
	
    --FOREIGN KEYS                  
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
	, SupportingServiceTibcoIdentifier

	--ATTRIBUTES
	  --Date Attributes
	, DimGreenInitiativeDateId
    , GreenInitiativeDate
    , GreenInitiativeClosedDate 

      --Location Attributes
	
	, DetailedDescriptionLocation

	  --Employee Attributes                                 
	, ProcessCloser
	, GIOriginator
    , GIApprovedBy
    , GIUser

	  --GI Attributes                                    
	, GISubject
    , GIDescription
    , [Status]	
	, GIType  
	, ProcessURLId
	, GIScore
	, MaterialsReused
	, IdeaSuggestion

	, GIEnvironmentAspect
	, GIFollowUpCommentsSummary
	, GIImpact
	, GIProcess
	, GIRejectedOrApproved
	, GIResult
	, DataSource
	, ProcessActivity
	, ProcessActivityOther
	, ImpactInlineButtons
	, EffortInlineButtons
	
	, EmissionReductionMethodOfOperations
	, EmissionReductionTechnicalIntervention
	, OtherEmissionReduction
	, ApprovalStatus
	, FeedbackEffort
	, EffortScore
	, FeedbackImpact
	, ImpactScore
	, FeedbackApplicability
	, ApplicabilityScore
	, FeedbackOriginality
	, OriginalityScore
	, FinalScore
	, WorldCleanupCampaign
    ,[CompletedBy]
    ,[CompletedDate]
    ,[FeedbackRespondent]   
	,[AmountSaving]
	,[UnitSaving]
FROM DataStore3.GreenInitiative
``
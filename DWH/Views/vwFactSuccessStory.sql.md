# Source: `DBs/AzureSingleDB/DWH/Views/vwFactSuccessStory.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactSuccessStory.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `e1be0a9d762c3eeea2cc557f09ce69f80784a2b29b776f4ba3ce4e8e3217e907`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE VIEW [DWH].[vwFactSuccessStory] AS
SELECT 
	  SuccessStoryId
    , CustomSuccessStoryId
    , VesselId
    , ProjectId
    --, OfficeId
    , OtherSiteId
    --, EntityBranchId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
	, SupportingServiceTibcoIdentifier
    , VesselLocationCode
    , ProjectLocationCode
    , EntityLocationCode
    , OtherSiteLocationCode
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
    , DimDateId
    , SuccessStoryDateTime
    , Subject
    , Description
    , Feedback
    , FeedbackRespondent
    , Activity
    , HRT
    , HRT2
    , Originator
    , SecondaryFactor
    , Results
    , TotalLikes
    , AverageScore
	, FeedbackImpact
	, ImpactScore
	, FeedbackEffort
	, EffortScore
	, FeedbackApplicability
	, ApplicabilityScore
	, FeedbackOriginality
	, OriginalityScore
	, FinalScore
	, ProcessDescription
	, [status]
    , [CompletedBy]
    , [CompletedDate]
FROM DataStore2.SuccessStory
``
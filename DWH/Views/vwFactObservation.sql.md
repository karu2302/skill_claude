# Source: `DBs/AzureSingleDB/DWH/Views/vwFactObservation.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactObservation.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `b98159d7e76f848736b7e2ae3357716a0ce5a6efdb70c7f1e288d5923e3edc04`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql


CREATE VIEW [DWH].[vwFactObservation] AS 
SELECT 
	CustomObservationId
    , ObservationId
	--, OfficeId
	, OtherSiteId
	, ProjectId
	, VesselId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
	, SupportingServiceTibcoIdentifier
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, VesselLocationCode
	, DimObservationDateId
	, ObservationDateTime
	, ProcessCloseDate
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
	, CloseComments
	, DescriptionAndProposedAction
	, DetailedLocation
	, ImmediateActionTakenExplanation
	, ImmediateActionTaken
	, TotalActions
	, ObservationWillBeAssignedTo
	, ProcessCloser
	, ProcessOriginator
	, ProcessPriority
	, Substatus
	, ProcessType
	, ProcessURLId
	, ReportedAnonymously
	, ResponsibleOffice
	, ResponsibleOtherSite
	, ResponsibleProject
	, ResponsibleVessel
	, [Status]
	, Title
	, DataSource
	--, LegalEntityId
	, TrendCategories
	, TrendCategoriesDescription
	, HighRiskTask
	, ActivitiesBlock4
	, SecondaryFactor
	, ReportedBehalfOf
	, ReportedBehalfOfDEME
	, TypeOfObservation
	, HighRiskTaskLevel2
	, TypeOfOperation
	, SpecifyOtherHighRiskTask
	, SpecifyOtherSecondaryFactor
	, SpecifyOtherActivityAndTechnique

  FROM DataStore3.Observation
``
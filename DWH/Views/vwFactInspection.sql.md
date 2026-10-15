# Source: `DBs/AzureSingleDB/DWH/Views/vwFactInspection.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactInspection.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `1f2f76ee80d6f4d5a8382d3a30a26f769783fc5357b9808efb7b17c35d147de7`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql




/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DWH].[vwFactInspection] AS 

SELECT 
	  InspectionId
	, CustomInspectionId
	, ProjectId
	, VesselId
	--, OfficeId
	, OtherSiteId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
	, SupportingServiceTibcoIdentifier
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, VesselLocationCode
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
	, ChecklistId
	, ExternalInspectorName
	, NumberInspectedQuestions
	, NumberNOKQuestions
	, ProcessOpenAction
	, ProcessTotalAction
	, ProcessOriginator
	, ProcessPriority
	, Company
	, DimInspectionDateId
	, InspectionDateTime
	, DetailedLocation
	, ProcessCloser
	, ProcessDescription
	, ProcessSubject
	, Substatus
	, ProcessType
	, Status
	, ProcessURLId
	, DataSource
	--, LegalEntityId
	, CheckListName
	, CheckListCode
	, CheckListStatus
	, IncludeStatistics
	, ProcessAssetValue
	, ProcessAsset
  FROM DataStore5.Inspection
``
# Source: `DBs/AzureSingleDB/DataStore4/Views/vwAction.sql`

- Original repository path: `DBs/AzureSingleDB/DataStore4/Views/vwAction.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `4a203bd5ef09e00de9a985223f96ff250c6af00dbb676cde2e7e25c8af8ec8bf`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql















/****** Script for SelectTopNRows command from SSMS  ******/
CREATE VIEW [DataStore4].[vwAction] AS
SELECT  A.ActionId
      , A.CustomProcessID
      , A.ProjectId
      , A.VesselId
      --, A.OfficeId
      --, A.LegalEntityId
	  , A.EntityId
      , A.OtherSiteId
      , A.SupportingServiceCode
	  , A.SupportingServiceTibcoIdentifier
      , A.IncidentId
      , A.EventId
      , A.ObservationId
      , A.InspectionId
	  , A.AuditId
      , A.SourceName
      , A.SourceId
      , A.ProcessURLId
      , A.Duedate
      , A.DateActionCompleted
      , A.DimActionDate
      , A.ActionDateTime
      , A.ActionCompletedBy
      , A.InitiatedBy
      , A.PersonAssignedForHandlingTheAction
      , A.ProcessCloser
      , A.ResponsibleUsers
      , A.ActionTopic
      , A.[Status]
      , A.Substatus
      , A.ActionType
      , A.ActionTakenDescription
      , A.[Group]
      , A.ImmediateActionTaken
      , A.ImmediateActionTaken2
      , A.LessonsLearned
      , A.[Priority]
      , A.ReasonForRejection
      , A.SupportingService
      , A.WhatActionHasToBeTaken
      , A.DataSource
      , A.PlanCategoryDescription
      , A.ResDep
      , A.EventType
	  , A.EventTypeOfMeeting
      , A.StatusPerformance 
	  , ISNULL(COALESCE(EV.POVOSource, INC.POVOSource, OBS.POVOSource, INS.POVOSource, AUD.POVOSource), '_N/A') AS POVOSource
	  , A.SourceItemId
  FROM DataStore3.Action AS A

  LEFT JOIN (SELECT EventId, REPLACE(REPLACE(CONCAT(ProjectId, ' ; ', VesselId, ' ; ', EntityId, ' ; ', OtherSiteId), ' ; _N/A', ''), '_N/A ;', '') AS POVOSource
	FROM DataStore3.Event) AS EV
	ON EV.EventId = A.EventId AND A.SourceName = 'Event'

  LEFT JOIN (SELECT IncidentId,  REPLACE(REPLACE(CONCAT(ProjectId, ' ; ', VesselId, ' ; ', EntityId, ' ; ', OtherSiteId), ' ; _N/A', ''), '_N/A ;', '') AS POVOSource
	FROM DataStore3.Incident) AS INC
	ON INC.IncidentId = A.IncidentId AND A.SourceName = 'Incident'
 
  LEFT JOIN (SELECT ObservationId,  REPLACE(REPLACE(CONCAT(ProjectId, ' ; ', VesselId, ' ; ', EntityId, ' ; ', OtherSiteId), ' ; _N/A', ''), '_N/A ;', '') AS POVOSource
	FROM DataStore3.Observation) AS OBS
	ON OBS.ObservationId = A.ObservationId AND A.SourceName = 'Observation'
 
  LEFT JOIN (SELECT InspectionId,  REPLACE(REPLACE(CONCAT(ProjectId, ' ; ', VesselId, ' ; ', EntityId, ' ; ', OtherSiteId), ' ; _N/A', ''), '_N/A ;', '') AS POVOSource
	FROM DataStore3.Inspection) AS INS
	ON INS.InspectionId = A.InspectionId AND A.SourceName = 'Inspection'
 
  LEFT JOIN (SELECT AuditId, REPLACE(REPLACE(CONCAT(ProjectId, ' ; ', VesselId, ' ; ', EntityId, ' ; ', OtherSiteId), ' ; _N/A', ''), '_N/A ;', '') AS POVOSource
	FROM DataStore3.Audit) AS AUD
	ON AUD.AuditId = A.AuditId AND A.SourceName = 'Audit'
``
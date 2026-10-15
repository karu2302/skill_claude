# Source: `DBs/AzureSingleDB/DWH/Views/vwFactAction.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactAction.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `66b28a00d188d8cbdd83e1b329423f0b86af1f195a9f99689e435b8f3986cfbc`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql












CREATE VIEW [DWH].[vwFactAction] AS

SELECT
      --BUSINESS KEYS
	  ActionId
	, CustomProcessID            -- Do not use as PK, as these are not unique

      --FOREIGN KEYS                
	, ProjectId
    , VesselId
    --, OfficeId
	, OtherSiteId
	, EntityId
	, EventId
	, SupportingServiceCode
	--, LegalEntityId
	, SourceName
	, SourceId
	, ProcessURLId

      --ATTRIBUTES

        --Date Attributes
    , Duedate
    , DateActionCompleted
    , DimActionDate
	, ActionDateTime

        --Employee attributes
    , ActionCompletedBy
    , InitiatedBy
    , PersonAssignedForHandlingTheAction
    , ProcessCloser
    , ResponsibleUsers

        --Action Attributes
    , ActionTopic
    , Status
    , Substatus
    , ActionType
    , ActionTakenDescription
    , [Group]
    , ImmediateActionTaken
    , ImmediateActionTaken2
    , LessonsLearned
    , Priority
    , ReasonForRejection
    , SupportingService
    , WhatActionHasToBeTaken
	, DataSource
	, PlanCategoryDescription
	, EventType
	, EventTypeOfMeeting
	, StatusPerformance
	, POVOSource
	, SourceItemId
	, SupportingServiceTibcoIdentifier

FROM DataStore4.Action
``
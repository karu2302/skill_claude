# Source: `DBs/AzureSingleDB/DWH/Views/vwFactEvent.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactEvent.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `78535023d82c5e78b5d541d46524466d06af88cce874671e9f33bec641be91dd`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql


CREATE VIEW [DWH].[vwFactEvent] AS

SELECT
	--BUSINESS KEYS
	  EventId
	, CustomEventId -- Do not use as PK, as these are not unique

	--FOREIGN KEYS
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

	--ATTRIBUTES

	  --Date Attributes
	, DimEventDateId
	, EventDateTime
	, EventCloseDate 
	  
	  --Location Attributes

	, DetailedDescriptionLocation

	  --Employee Attributes
	, ProcessCloser
	, LeadName
	, ExternalLead
	, ExternalName
	, InternalName
	, ReportedBy

	  --Event Attributes
	, AttendanceList
	, Campaign        
	, CampaignRelated         
	, Company                           
	, DPDrillType          
	, DrillEvaluation          
	, DrillType
	, EventName
	, EventDescription
	, EventPriority
	, Status
	, Substatus 
	, EventType  
	, ProcessURLId
	, [Function]
	, Log
	, MeetingType  
	, MeetingTypeGUID
	, MeetingTypeGroup
	, MeetingTypeStatus
	, ScenarioPlannedActivities    
	, SpecifyOther     

	--FACTS
	, TotalActions 
	, TotalParticipants    
	, DataSource
	, ParticipatedPMWM
	, DurationHours
	, DurationMinutes
	, TotalDEME
	, TotalExternal
	, SubtypeEventGUID
	, InternalExternal
               
FROM DataStore3.Event
``
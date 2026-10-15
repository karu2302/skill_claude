# Source: `DBs/AzureSingleDB/DataStore3/Views/vwAction.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwAction.sql`
- SHA-256 of original file: `a37176bacf8db7e7848fb98b7dde97bf67dd90bb6932d8c8429044961fd9a143`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql





CREATE VIEW [DataStore3].[vwAction] AS

SELECT DISTINCT
      --BUSINESS KEYS
	  ActionId                                                                                                          AS ActionId
    , A.CustomprocessID                                                                                                 AS CustomProcessID            -- Do not use as PK, as these are not unique

      --FOREIGN KEYS                
	, ISNULL(PA1.ProjectId, '_N/A')																						AS ProjectId
    , ISNULL(V1.VesselId, '_N/A')																				        AS VesselId
	--, CASE
--		WHEN SS.SupportingServiceCode IS NULL THEN COALESCE(A.processOfficeCode, O1.OfficeId, O2.OfficeId, EB1.OfficeId,  '_N/A')
		--WHEN SS.SupportingServiceCode IS NULL THEN COALESCE(O1.OfficeId, O2.OfficeId, OEB.OfficeId,  '_N/A')
		--WHEN SS.ActivityLineId = 'ALD' THEN 'O0141-ALD'
		--WHEN SS.ActivityLineId = 'ALO' THEN 'O0141-ALO'
		--WHEN SS.ActivityLineId = 'ALE' THEN 'O0141-ALE'
		--WHEN SS.ActivityLineId = 'ALI' THEN 'O0141-ALI'
		--ELSE 'O0141' END																											AS OfficeId
--  , COALESCE(A.EntityCode, EB1.EntityBranchId, A.Entity, '_N/A')                                                                  AS LegalEntityId
   -- , ISNULL(OEB.EntityBranchId, '_N/A')																							AS LegalEntityId
	, ISNULL(E.EntityId, '_N/A')																									AS EntityId
	, COALESCE(OS1.OtherSiteId, OS2.OtherSiteId, '_N/A')											                                AS OtherSiteId
    , COALESCE(A.SupportingServiceCode, SS.SupportingServiceCode , '_N/A')                                                          AS SupportingServiceCode
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')															AS SupportingServiceTibcoIdentifier
  
	, CASE WHEN Linkedto like '%Incident%' THEN SourceID ELSE '_N/A' END                                                            AS IncidentId
	, CASE WHEN Linkedto = 'Event' THEN SourceID ELSE '_N/A' END                                                                    AS EventId
	, CASE WHEN Linkedto = 'Observation' THEN SourceID ELSE '_N/A' END                                                              AS ObservationId
	, CASE WHEN Linkedto = 'Inspection' THEN SourceID ELSE '_N/A' END                                                               AS InspectionId
	, CASE WHEN Linkedto = 'Audit' THEN SourceID ELSE '_N/A' END																	AS AuditId


	, CASE WHEN Linkedto LIKE '%Incident%' THEN 'Incident' ELSE ISNULL(Linkedto, '_N/A')  END                                       AS SourceName
	, ISNULL(SourceID, '_N/A')                                                                                                      AS SourceId
	, ISNULL(A.processUrlID, '_N/A')                                                                                                AS ProcessURLId 
 
     -- ATTRIBUTES

       -- Date Attributes

 --	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, DueDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))			AS Duedate 
	--, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, Dateactioncompleted,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS DateActionCompleted 
	--, ISNULL(DS.DimDateId,'19000101')																								AS DimActionDate 
	--, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, A.[Date],103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS ActionDateTime

    , CONVERT(DATETIME, ISNULL(DuedateText, '1900-01-01'),103)																		AS Duedate 
	, CONVERT(DATETIME, ISNULL(DateactioncompletedText, '1900-01-01'),103)															AS DateActionCompleted 
	, ISNULL(DS.DimDateId,'19000101')																								AS DimActionDate 
	, CONVERT(DATETIME, ISNULL(A.[ProcessDate], '1900-01-01'), 103)																	AS ActionDateTime

        --Employee attributes
	, ISNULL(Actioncompletedby                 , '_N/A')                                                                            AS ActionCompletedBy
	-- [Laura] hotfix for deploy 23/09/2025: field was removed from staging, but still used in this datastore view
    , ISNULL(Initiatedby                       , '_N/A')                                                                            AS InitiatedBy
    , ISNULL(Personassignedforhandlingtheaction, '_N/A')                                                                            AS PersonAssignedForHandlingTheAction
    , ISNULL(A.processCloser                   , '_N/A')                                                                            AS ProcessCloser
    , ISNULL(Responsibleusers                  , '_N/A')                                                                            AS ResponsibleUsers

        --Action Attributes                                                                     
	, ISNULL(Actiontopic                       , '_N/A')                                                                            AS ActionTopic
    , ISNULL(A.[Status]                        , '_N/A')                                                                            AS [Status]
	, ISNULL(A.processSubstatus                , '_N/A')                                                                            AS Substatus
	-- , ISNULL(processSupportingServiceCode      , '_N/A')                                                                         AS ActionSupportingServiceCode
	, ISNULL(A.processType                     , '_N/A')                                                                            AS ActionType
	, ISNULL(Descriptionofactiontaken          , '_N/A')                                                                            AS ActionTakenDescription
	, ISNULL([Group]                           , '_N/A')                                                                            AS [Group]
	, ISNULL(Immediateactiontaken              , '_N/A')                                                                            AS ImmediateActionTaken
	, ISNULL(Immediateactiontaken2             , '_N/A')                                                                            AS ImmediateActionTaken2
	, ISNULL(Lessonslearned                    , '_N/A')                                                                            AS LessonsLearned
	, ISNULL([Priority]                        , '_N/A')                                                                            AS [Priority]
	, ISNULL(Reasonforrejection                , '_N/A')                                                                            AS ReasonForRejection
	, ISNULL(A.SupportingService               , '_N/A')                                                                            AS SupportingService
	, ISNULL(Whatactionhastobetaken            , '_N/A')                                                                            AS WhatActionHasToBeTaken
	, 'Apprise' AS DataSource
	, '_N/A' AS PlanCategoryDescription
	, '_N/A' AS ResDep
	, ISNULL(EV.ProcessType, '_N/A')																								AS EventType
	, ISNULL(EV.TypeOfMeeting, '_N/A')																								AS EventTypeOfMeeting
	, CASE 
		WHEN DATEDIFF(
						DAY, 
						CONVERT(DATETIME, ISNULL(DateactioncompletedText, '1900-01-01'),103), 
						CONVERT(DATETIME, ISNULL(DuedateText, '1900-01-01'),103)) < 0  THEN 'Over time'
		   WHEN CONVERT(DATETIME, ISNULL(DuedateText, '1900-01-01'),103) < GETUTCDATE() AND A.DateactioncompletedText IS NULL THEN 'Over time'
		   ELSE 'In time' END																										AS StatusPerformance
	, ISNULL(A.SourceitemID, '_N/A')																								AS SourceItemId

FROM StagingApprise.Action AS A

	-- Check What POVOCode is

	LEFT JOIN DataStore2.Vessel AS V1
		ON A.POVOcode = V1.VesselId

	LEFT JOIN DataStore2.Project AS PA1
		ON A.POVOcode = PA1.ProjectId

	LEFT JOIN DataStore2.OtherSite AS OS1
		ON A.POVOcode = OS1.OtherSiteId

	--LEFT JOIN StagingGraphAPI.Offices AS O1
	--	ON A.PovoCode = O1.OfficeName
	--	AND O1.OfficeId not in ('O0141-ALD','O0141-ALO','O0141-ALE','O0141-ALI') -- Exception on HQ office because of multiple AL's: these virtual offices are to be ignored in the facts

	LEFT JOIN DataStore2.SupportingService AS SS
		ON A.POVOcode = SS.SupportingServiceCode


	-- Check other columns

	--LEFT JOIN StagingGraphAPI.Offices AS O2
	--	ON A.Office = O2.OfficeName
	--	AND O2.OfficeId not in ('O0141-ALD','O0141-ALO','O0141-ALE','O0141-ALI') -- Exception on HQ office because of multiple AL's: these virtual offices are to be ignored in the facts

--	LEFT JOIN StagingGraphAPI.EntitiesBranches AS EB1
--		ON A.Entity = EB1.EntityBranchName

	LEFT JOIN DataStore2.OtherSite AS OS2
		ON A.Othersite = OS2.OtherSiteName

	LEFT JOIN StagingApprise.Event EV
		ON A.SourceID = EV.EventId
			AND A.Linkedto = 'Event' 

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT,FORMAT(CONVERT(DATETIME, ISNULL(A.[ProcessDate], '1900-01-01'), 103),'yyyyMMdd')) = DS.DimDateId	

	--LEFT JOIN DataStore2.Office AS OEB
	--	ON A.POVOcode = OEB.EntityBranchId
	--	AND DS.DimDateId >= OEB.DimQHSESOfficeStartDateId AND DS.DimDateId <= OEB.DimQHSESOfficeEndDateId

	--new
	LEFT JOIN DataStore2.Entity AS E
		ON A.POVOcode = E.EntityId
		

UNION ALL

SELECT DISTINCT -- Doubles on ActionId in staging table from Impact
	--BUSINESS KEYS
	  CAST([ActionID] AS NVARCHAR(255))                                                                                             AS ActionId
	, CAST([ActionID] AS NVARCHAR(255))                                                                                             AS CustomProcessId
	
    --FOREIGN KEYS
	, COALESCE(PA1.ProjectId, AC.Project, '_N/A')                                                                                   AS ProjectId
	, COALESCE(NULLIF(ICD.VesselId, 'Not Available'), NULLIF(ICD2.VesselId, 'Not Available'), AC.Vessel, '_N/A')                    AS VesselId 
	--, COALESCE(O1.OfficeId, '_N/A')                                                                                                 AS OfficeId
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END                                     AS LegalEntityId
	, CASE 
		WHEN COALESCE(PA1.ProjectId, AC.Project, NULLIF(ICD.VesselId, 'Not Available'), NULLIF(ICD2.VesselId, 'Not Available'), AC.Vessel,OS1.OtherSiteId) IS NULL
		THEN ISNULL(EB1.EntityBranchId, '_N/A')		
		ELSE '_N/A' 
	  END																															AS EntityId
	, COALESCE(OS1.OtherSiteId, '_N/A')                                                                                             AS OtherSiteId
    , '_N/A'                                                                                                                        AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')																AS SupportingServiceTibcoIdentifier													
	, ISNULL(INC.IncidentId, '_N/A')                                                                                                AS IncidentId
	, CASE 
        WHEN ASRC.SourceDescription = 'QHSE-S Related Event' THEN CONVERT(NVARCHAR(255), AC.AuditHeadId) 
        ELSE '_N/A' 
      END                                                                                                                           AS EventId
	, ISNULL(OBS.ObservationId, '_N/A')                                                                                             AS ObservationId -- As the class 'Observation / Improvement Idea' also contains improvement Idea, we do not want those as observation Id
	, CASE 
        WHEN ASRC.SourceDescription = 'Inspection' THEN CONVERT(NVARCHAR(255), AC.AuditHeadId) 
        ELSE '_N/A' 
      END                                                                                                                           AS InspectionId
	, '_N/A'																														AS AuditId
	, CASE 
		WHEN ASRC.SourceDescription = 'QHSE-S Related Event' THEN 'Event'
		WHEN ASRC.SourceDescription = 'Inspection' THEN 'Inspection'
		WHEN OBS.ObservationId IS NOT NULL THEN 'Observation'
		WHEN ASRC.SourceDescription = 'Incident' THEN 'Incident'
		ELSE ISNULL(ASRC.SourceDescription, '_N/A')  
      END                                                                                                                           AS SourceName
	, CASE 
		WHEN ASRC.SourceDescription = 'QHSE-S Related Event' THEN CAST(AC.AuditHeadId AS NVARCHAR(255)) 
		WHEN ASRC.SourceDescription = 'Inspection' THEN CAST(AC.AuditHeadId AS NVARCHAR(255)) 
		WHEN OBS.ObservationId IS NOT NULL THEN CAST(AC.AuditHeadId AS NVARCHAR(255)) 
		ELSE '_N/A' 
      END                                                                                                                           AS SourceId
	, CAST([ActionID] AS NVARCHAR(255))                                                                                             AS ProcessUrlId 
 
      --ATTRIBUTES

        --Date Attributes
    , '1900-01-01'                                                                                                                  AS Duedate
    , '1900-01-01'                                                                                                                  AS DateActionCompleted
	, ISNULL(DS.DimDateId,'19000101')																								AS DimActionDate
 --   , CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(AC.[Date], '01/01/1900')), 'yyyyMMdd'))												AS DimActionDate
	, CONVERT(DATETIME, ISNULL(NULLIF(AC.[Date],'0') , '01/01/1900'))																AS ActionDateTime
	
        --Employee attributes                                                               
	, '_N/A'                                                                                                                        AS ActionCompletedBy
    , '_N/A'                                                                                                                        AS InitiatedBy
    , '_N/A'                                                                                                                        AS PersonAssignedForHandlingTheAction
    , '_N/A'                                                                                                                        AS ProcessCloser
    , '_N/A'                                                                                                                        AS ResponsibleUsers

	, '_N/A'                                                                                                                        AS ActionTopic
   
    , ISNULL(
				CASE WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
					 WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
					 ELSE ST.StatusName 
                END
			 ,'_N/A')                                                                                                               AS [Status]
	, '_N/A'                                                                                                                        AS Substatus
	-- , '_N/A'                                                                                                                     AS ActionSupportingServiceCode
	, '_N/A'                                                                                                                        AS ActionType
	, '_N/A'                                                                                                                        AS ActionTakenDescription
	, '_N/A'                                                                                                                        AS [Group]
	, '_N/A'                                                                                                                        AS ImmediateActionTaken
	, '_N/A'                                                                                                                        AS ImmediateActionTaken2
	, '_N/A'                                                                                                                        AS LessonsLearned
	, '_N/A'                                                                                                                        AS [Priority]
	, '_N/A'                                                                                                                        AS ReasonForRejection
	, '_N/A'                                                                                                                        AS SupportingService
	, '_N/A'                                                                                                                        AS WhatActionHasToBeTaken   
	, 'Impact'                                                                                                                      AS DataSource
	, ISNULL(PG.PlanCategory, '_N/A')																								AS PlanCategoryDescription
	, ISNULL(ICD.ImpactDepartmentName, '_N/A') AS ResDep
	, CASE WHEN ET.ProcessType IS NOT NULL THEN EventType
		 WHEN EventType = 'ToolBox Meeting' THEN 'Toolbox'
		 WHEN EventType LIKE '%Meeting%' THEN 'Meeting'
		 WHEN EventType LIKE '%Induction%' THEN 'Induction'
		 WHEN EventType = 'Management Review' THEN 'Management Review Meeting'
		 WHEN EventType = 'QHSE-S Training' THEN 'Training'
		 ELSE ISNULL(EventType, '_N/A') 
		 END																														AS EventType
	, '_N/A'																														AS EventTypeOfMeeting
    ,  CASE WHEN AC.StatusPerformance IN ('Pending And Overdue', 'Closed Over Time') THEN 'Over Time'
		 WHEN AC.StatusPerformance IN ('Pending Not Overdue', 'Closed In Time') THEN 'In Time'
		 ELSE '_N/A' END																											AS StatusPerformance
	, '_N/A'																														AS SourceItemId

  FROM [StagingImpact].[Action] AS AC 

	LEFT JOIN StagingImpact.PlanCategory PG
		ON AC.AuditHeadId = PG.AuditHeadId


	LEFT JOIN StagingImpact.ActionSource ASRC
		ON AC.Actionitemsource = ASRC.SourceId
		
	LEFT JOIN (SELECT Distinct IncidentGUI, IncidentId FROM StagingImpact.Incident) AS INC
		ON AC.SourceGUI = INC.IncidentGUI
		AND ASRC.SourceDescription = 'Incident'

	LEFT JOIN (SELECT Distinct ObservationId FROM StagingImpact.Observation) AS OBS
		ON AC.AuditHeadId = OBS.ObservationId 
		AND ASRC.SourceDescription = 'Observation / Improvement Idea'

	LEFT JOIN StagingImpact.[Status] AS ST
		ON AC.StatusId = ST.StatusId

-- Resp Department

	LEFT JOIN StagingGraphAPI.ImpactConversionData AS ICD
		ON AC.Responsibledepartment = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices AS O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN StagingGraphAPI.OtherSites AS OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN StagingGraphAPI.EntitiesBranches AS EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	-- Extra Povo fields
	LEFT JOIN StagingGraphAPI.ImpactConversionData AS ICD2
		ON AC.Vessel = ICD2.ImpactDepartmentId
	
/*	ImpactConversionProjectNumber will contain only 1 value instead of multiple values separated by ;
	LEFT JOIN (
		SELECT TRIM(value) AS ImpactConversion, MIN(ProjectId) AS ProjectId
			FROM DataStore1.Project
			CROSS APPLY STRING_SPLIT(ImpactConversionProjectNumber, ';')
			GROUP BY TRIM(value)
			)	PA1
		ON AC.Project = PA1.ImpactConversion
*/
	LEFT JOIN DataStore2.Project AS PA1
		ON AC.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN ( SELECT DISTINCT QHSESEventID,EventType FROM StagingImpact.Event)  EV
		ON AC.AuditHeadId = EV.QHSESEventID
		AND ASRC.SourceDescription = 'QHSE-S Related Event'
    LEFT JOIN ( SELECT DISTINCT 
                    ProcessType 
                FROM StagingApprise.Event 
                WHERE ProcessType IS NOT NULL) ET
        ON EV.EventType = ET.ProcessType

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(AC.[Date], '01/01/1900')), 'yyyyMMdd')) = DS.DimDateId
````
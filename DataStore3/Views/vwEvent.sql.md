# Source: `DBs/AzureSingleDB/DataStore3/Views/vwEvent.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwEvent.sql`
- SHA-256 of original file: `372a2a31a828189a1ab8513d12d1a847c4fc6c8e694d9b454fcf314ff4aab971`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql




CREATE VIEW [DataStore3].[vwEvent] AS

SELECT DISTINCT
	--BUSINESS KEYS
	  EventId														                                    AS EventId
	, ISNULL(CustomProcessID, '_N/A')												                    AS CustomEventId -- Do not use as PK, as these are not unique

	--FOREIGN KEYS          
	, COALESCE(NULLIF(ProcessProjectCode, 'none')	 , LEFT(Project, 6), '_N/A')						AS ProjectId -- If projectid is not filled in (old records, get code out of description)
	, COALESCE(NULLIF(ProcessVesselCode, 'none')	 , LEFT(Vessel, 4),  '_N/A') 						AS VesselId  -- If vesselid is not filled in, get id out of description
--	, COALESCE(NULLIF(EntityCode, 'none')	, EB.EntityBranchId , Entity,  '_N/A')						AS LegalEntityId			 -- If OfficeId is not filled in, use the description to look for the Id in the office Data
--	, COALESCE(NULLIF(EntityCode, 'none'), Entity, '_N/A')												AS LegalEntityId -- if no entitycode, give the description to show in screeening errors
	, COALESCE(NULLIF(EntityCode, 'none'), Entity, '_N/A')												AS EntityId	
--  , COALESCE(NULLIF(ProcessOfficeCode, 'none'), O.OfficeId, EB.OfficeId,  Office, '_N/A')				AS OfficeId -- Office also via legal Entity
--	, COALESCE(NULLIF(ProcessOfficeCode, 'none'), O.OfficeId, Office,  '_N/A')							AS OfficeId -- sometimes only office is filled in
	, COALESCE(NULLIF(ProcessOtherSiteCode, 'none'),  OS.OtherSiteId, OtherSite, '_N/A')				AS OtherSiteId	-- If OtherSiteId is not filled in, use the description to look for the id in the OtherSite data
    , ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')								            AS CharteredVesselId
	, ISNULL(EV.SupportingServiceCode	, '_N/A')                                                       AS SupportingServiceCode
	, ISNULL(ProjectLocation			, '_N/A')							                            AS ProjectLocationCode -- Location Descriptions are not longer staged, since we now  lookup facts to configurationloactions
	, ISNULL(VesselLocation				, '_N/A')							                            AS VesselLocationCode
	, ISNULL(OtherSiteLocation			, '_N/A')							                            AS OtherSiteLocationCode
	, ISNULL(OfficeLocation				, '_N/A')								                        AS EntityLocationCode
	, ISNULL(V.VesselName				, '_N/A')														AS VesselName
	, ISNULL(P.ProjectName				, '_N/A')														AS ProjectName
	, ISNULL(E.EntityName				, '_N/A')														AS EntityName
	, ISNULL(OS2.OtherSiteName			, '_N/A')														AS OtherSiteName
	, ISNULL(SS.SupportingServiceName	, '_N/A')														AS SupportingServiceName
	, ISNULL(SS.TibcoIdentifier			, '00000000-0000-0000-0000-000000000000')						AS SupportingServiceTibcoIdentifier															


	--ATTRIBUTES

	  --Date Attributes

	, ISNULL(DS.DimDateId,'19000101')																	AS DimEventDateId
 --	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, [Date],103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))							AS EventDateTime
	--, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, ProcessCloseDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))						AS EventCloseDate 

	, COALESCE(TRY_CONVERT(DATETIME, [DateText], 103),TRY_CONVERT(DATETIME, [DateText], 126),TRY_CONVERT(DATETIME, [DateText], 127), '1900-01-01 00:00:00.000') AS EventDateTime
	, TRY_CONVERT(DATETIME, ISNULL(ProcessCloseDateText , '1900-01-01'),103)							AS EventCloseDate 


	--Location Attributes
	
	, ISNULL(DetailedDescriptionLocation, '_N/A')					                                    AS DetailedDescriptionLocation

	  --Employee Attributes                                 
	, ISNULL(ProcessCloser			, '_N/A')							                                AS ProcessCloser
	, ISNULL(EV.Lead				, '_N/A')															AS LeadName
	, ISNULL(ExternalLead			, '_N/A')          					                                AS ExternalLead
	, ISNULL(ExternalName  			, '_N/A')							                                AS ExternalName
	, ISNULL(InternalName			, '_N/A')							                                AS InternalName
	, ISNULL(Reportedby    			, '_N/A')							                                AS ReportedBy

	  --Event Attributes                                    
	, ISNULL(EV.AttendanceList		, '_N/A')							                                AS AttendanceList
	, ISNULL(EV.Campaign			, '_N/A')							                                AS Campaign        
	, CONVERT(BIT, CASE WHEN CampaignRelated = 'Yes' THEN 1                                     
				ELSE 0 END )										                                    AS CampaignRelated         
	, ISNULL(EV.Company				, '_N/A')							                                AS Company                           
	, ISNULL(EV.DPDrillType			, '_N/A')							                                AS DPDrillType          
	, ISNULL(EV.DrillEvaluation		, '_N/A')							                                AS DrillEvaluation          
	, ISNULL(EV.DrillType			, '_N/A')							                                AS DrillType
	, ISNULL(EV.SubjectOfEvent		, '_N/A')							                                AS EventName
	, ISNULL(EV.ProcessDescription	, '_N/A')							                                AS EventDescription
	, ISNULL(EV.ProcessPriority		, '_N/A')							                                AS EventPriority
	, ISNULL(EV.[Status]			, '_N/A')										                    AS [Status]	
	, ISNULL(EV.ProcessSubstatus	, '_N/A')			          		                                AS Substatus 
	, ISNULL(EV.ProcessType			, '_N/A')							                                AS EventType  
	, ISNULL(EV.ProcessUrlID   		, '_N/A')							                                AS ProcessURLId
	, ISNULL(EV.[Function]			, '_N/A')							                                AS [Function]
	, ISNULL(EV.[Log]				, '_N/A')							                                AS [Log]
	, ISNULL(T.Title				, '_N/A')															AS MeetingType
	, ISNULL(T.[GUID]				, '_N/A')															AS MeetingTypeGUID
	, ISNULL(T.[Group]				, '_N/A')															AS MeetingTypeGroup
	, ISNULL(T.[Status]				, '_N/A')															AS MeetingTypeStatus
	, ISNULL(ScenarioPlannedActivities , '_N/A')					                                    AS ScenarioPlannedActivities    
	, ISNULL(SpecifyOther			, '_N/A')							                                AS SpecifyOther     

	--FACTS
	, ETL.F_QHSEConvertInt(ISNULL(ProcessTotalActions, 0))					                            AS TotalActions 
	, ETL.F_QHSEConvertInt(ISNULL(TotalNumberOfParticipants, 0))			                            AS TotalParticipants  
	, 'Apprise'                                                                                         AS DataSource
	, '_N/A'																							AS ResDep
	, ISNULL(EV.PMWMVesselSafetyMeeting, '_N/A')														AS ParticipatedPMWM
	, CONVERT(INT, ISNULL(NULLIF(DurationHours, ''), 0)) 												AS DurationHours
	, CONVERT(INT, ISNULL(NULLIF(DurationMinutes, ''), 0))												AS DurationMinutes
	, CONVERT(INT, ISNULL(NULLIF(TotalDEME, ''), 0))													AS TotalDEME
	, ETL.F_QHSEConvertInt(ISNULL(NULLIF(TotalExternal, ''), 0))										AS TotalExternal
	, ISNULL(NULLIF(SubtypeEventValue, ''), '_N/A')														AS SubtypeEventGUID
	, ISNULL(EV.InternalExternal, '_N/A')																AS InternalExternal


FROM StagingApprise.Event EV
/*	
	LEFT JOIN StagingGraphAPI.EntitiesBranches EB
		ON EV.Entity = EB.EntityBranchName
*/
	--LEFT JOIN StagingGraphAPI.Offices O
	--	ON EV.Office = O.OfficeName
	--	AND O.OfficeId not in ('O0141-ALD','O0141-ALO','O0141-ALE','O0141-ALI') -- Exception on HQ office because of multiple AL's: these virtual offices are to be ignored in the facts

	LEFT JOIN DataStore2.OtherSite OS
		ON EV.OtherSite = OS.OtherSiteName

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ProcessVesselCode, 'none')	 , LEFT(Vessel, 4),  '_N/A') 	 = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(NULLIF(ProcessProjectCode, 'none')	 , LEFT(Project, 6), '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON COALESCE(NULLIF(EntityCode, 'none'), Entity, '_N/A') = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE(NULLIF(ProcessOtherSiteCode, 'none'),  OS.OtherSiteId, OtherSite, '_N/A')	 = OS2.OtherSiteId

	LEFT JOIN DataStore2.SupportingService SS 
		ON EV.SupportingServiceCode = SS.SupportingServiceCode

	LEFT JOIN ETL.Date DS 
		ON ISNULL(CONVERT(INT,FORMAT(COALESCE(TRY_CONVERT(DATETIME, [DateText], 103),TRY_CONVERT(DATETIME, [DateText], 126),TRY_CONVERT(DATETIME, [DateText], 127)),'yyyyMMdd')),  '19000101') 
			= DS.DimDateId	

	LEFT JOIN StagingGraphAPI.Topics T
		ON EV.TypeOfMeetingValue = T.GUID

UNION ALL


SELECT 
	  QHSESEventId														                                AS EventId
	, QHSESEventId												                                        AS CustomEventId
      
	, COALESCE(PA1.ProjectId, EV.Project, '_N/A' )                                                      AS ProjectId
	, COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  EV.Vessel, '_N/A')   AS VesselId 
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END         AS LegalEntityId
	, CASE 
		WHEN COALESCE(PA1.ProjectId, EV.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  EV.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END																								AS EntityId
	--, COALESCE( O1.OfficeId,  '_N/A')																	AS OfficeId
	, COALESCE( OS1.OtherSiteId,  '_N/A')																AS OtherSiteId
	, '_N/A'																	                        AS CharteredVesselId
    , '_N/A'                                                                                            AS SupportingServiceCode
	, '_N/A'                                                                                            AS ProjectLocationCode
	, '_N/A'                                                                                            AS VesselLocationCode
	, '_N/A'                                                                                            AS OtherSiteLocationCode
	, '_N/A'                                                                                            AS EntityLocationCode
	, ISNULL(V.VesselName, '_N/A')																		AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																		AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																		AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')																	AS OtherSiteName
	, '_N/A'																							AS SupportingServiceName
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')									AS SupportingServiceTibcoIdentifier	

	, ISNULL(DS.DimDateId,'19000101')																	AS DimEventDateId
--	, CONVERT(INT, FORMAT(CONVERT( [Date], ISNULL([Date], '01/01/1900')), 'yyyyMMdd'))                  AS DimEventDateId
	, CONVERT(DATETIME, ISNULL([Date] , '01/01/1900') )                                                 AS EventDateTime 
	, '01/01/1900'                                                                                      AS EventCloseDate
     --Location Attributes

	, '_N/A'                                                                                            AS DetailedDescriptionLocation

	  --Employee Attributes
	, '_N/A'						                                                                    AS ProcessCloser
	, '_N/A'  						                                                                    AS LeadName
	, '_N/A'         				                                                                    AS ExternalLead
	, '_N/A'						                                                                    AS ExternalName
	, '_N/A'						                                                                    AS InternalName
	, '_N/A'						                                                                    AS ReportedBy

	  --Event Attributes
	, '_N/A'							                                                                AS AttendanceList
	, '_N/A'							                                                                AS Campaign        
	, 0									                                                                AS CampaignRelated         
	, '_N/A'							                                                                AS Company                           
	, '_N/A'							                                                                AS DPDrillType          
	, '_N/A'							                                                                AS DrillEvaluation          
	, '_N/A'							                                                                AS DrillType
	, '_N/A'							                                                                AS EventName
	, '_N/A'							                                                                AS EventDescription
	, '_N/A'							                                                                AS EventPriority
	, ISNULL(
				CASE WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
					 WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
					 ELSE ST.StatusName END
			 ,'_N/A')					
										                                                                AS [Status]
	, '_N/A'			          		                                                                AS Substatus 
	, CASE 
        WHEN ET.ProcessType IS NOT NULL THEN EventType
		 WHEN EventType = 'ToolBox Meeting' THEN 'Toolbox'
		 WHEN EventType = 'Vessel-Project Safety Meeting' THEN 'Vessel-Project Safety Meeting'
		 WHEN EventType LIKE '%Meeting%' THEN 'Meeting'
		 WHEN EventType LIKE '%Induction%' THEN 'Induction'
		 WHEN EventType = 'Management Review' THEN 'Management Review Meeting'
		 WHEN EventType = 'QHSE-S Training' THEN 'Training'
		 ELSE ISNULL(EventType, '_N/A') 
		 END		                                                                                    AS EventType  
	, QHSESEventId							                                                            AS ProcessURLId
	, '_N/A'							                                                                AS [Function]
	, '_N/A'							                                                                AS [Log]
	, '_N/A'							                                                                AS MeetingType  
	, '_N/A'							                                                                AS MeetingTypeGUID
	, '_N/A'																							AS MeetingTypeGroup
	, '_N/A'																							AS MeetingTypeStatus
	, '_N/A'							                                                                AS ScenarioPlannedActivities    
	, '_N/A'							                                                                AS SpecifyOther     

	--FACTS
	, ETL.F_QHSEConvertInt(0)			                                                                AS TotalActions 
	, ETL.F_QHSEConvertInt(ISNULL(TotalParticipants, 0))			                                    AS TotalParticipants    
	, 'Impact'																							AS DataSource
	, ISNULL(ICD.ImpactDepartmentName, '_N/A')															AS ResDep
	, '_N/A'																							AS ParticipatedPMWM
	, 0																									AS DurationHours
	, 0																									AS DurationMinutes
	, 0																									AS TotalDEME
	, 0																									AS TotalExternal
	, '_N/A'																							AS SubtypeEvent
	, '_N/A'																							AS InternalExternal
	
FROM [StagingImpact].[Event] EV
    LEFT JOIN ( SELECT DISTINCT 
                    ProcessType 
                FROM StagingApprise.Event 
                WHERE ProcessType IS NOT NULL) ET
        ON EV.EventType = ET.ProcessType

	LEFT JOIN StagingImpact.[Status] AS ST
		ON ST.StatusId = EV.StatusId

	--Resp Department
	LEFT JOIN StagingGraphAPI.ImpactConversionData ICD
		ON EV.ResponsibleDepartment = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN StagingGraphAPI.OtherSites OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN StagingGraphAPI.EntitiesBranches EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	-- Other POVO Fields


	--LEFT JOIN StagingGraphAPI.EntitiesBranches EB2
	--	ON ICD2.EntityBranchId = EB2.SharepointId

	LEFT JOIN 
	(
		SELECT 
			 -- OfficeId
			  OtherSiteId
			, EntityBranchID 
			, VesselId
			, ImpactDepartmentName
		FROM StagingGraphAPI.ImpactConversionData A
		INNER JOIN (
				SELECT 
					MAX(ImpactDepartmentId) AS MaxId
				FROM StagingGraphAPI.ImpactConversionData 
				GROUP BY ImpactDepartmentName
					) B
				ON A.ImpactDepartmentId = B.MaxId
	
	) ICD3
	 -- Vessel
		ON ICD3.ImpactDepartmentName = EV.Vessel

/*	ImpactConversionProjectNumber will contain only 1 value instead of multiple values separated by ;	
	LEFT JOIN (
		SELECT TRIM(value) AS ImpactConversion, MIN(ProjectId) AS ProjectId
			FROM DataStore1.Project
			CROSS APPLY STRING_SPLIT(ImpactConversionProjectNumber, ';')
			GROUP BY TRIM(value)
			)	PA1
		ON EV.Project = PA1.ImpactConversion
*/

	LEFT JOIN DataStore2.Project AS PA1
		ON EV.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(EV.[Date], '01/01/1900')), 'yyyyMMdd')) = DS.DimDateId	

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  EV.Vessel, '_N/A') = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(PA1.ProjectId, EV.Project, '_N/A' )  = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON CASE 
		WHEN COALESCE(PA1.ProjectId, EV.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  EV.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE( OS1.OtherSiteId,  '_N/A') = OS2.OtherSiteId
````
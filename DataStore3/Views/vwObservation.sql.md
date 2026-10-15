# Source: `DBs/AzureSingleDB/DataStore3/Views/vwObservation.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwObservation.sql`
- SHA-256 of original file: `14cab216d327b8f786902275860f048004f23bd472cc058404d84729773c909b`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql














/****** Script for SelectTopNRows command from SSMS  ******/



CREATE VIEW [DataStore3].[vwObservation] AS 


SELECT DISTINCT
	--PK
	ObservationId
	, ISNULL(CustomProcessId, '_N/A')																AS CustomObservationId

	  -- POVO FK
	--, ISNULL(NULLIF(ProcessOfficeCode, 'none'),'_N/A')											AS OfficeId		   -- Special mapping not neccassry as Process - POVO - Codes are filled in correctly
	--, ISNULL(NULLIF(EntityCode, 'none'), '_N/A')													AS LegalEntityId
	, ISNULL(NULLIF(EntityCode, 'none'), '_N/A')													AS EntityId
	, ISNULL(NULLIF(ProcessOtherSiteCode, 'none'), '_N/A')											AS OtherSiteId
	, ISNULL(NULLIF(ProcessProjectCode, 'none'), '_N/A')											AS ProjectId
	, ISNULL(NULLIF(ProcessVesselCode, 'none'), '_N/A')												AS VesselId
	, ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')										AS CharteredVesselId
    , ISNULL(O.SupportingServiceCode,'_N/A')														AS SupportingServiceCode
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')							AS SupportingServiceTibcoIdentifier
	 
	 -- POVO Location
	, ISNULL(ProjectLocation	, '_N/A')															AS ProjectLocationCode -- Location Descriptions are not longer staged, since we now  lookup facts to configurationloactions
	, ISNULL(VesselLocation	, '_N/A')																AS VesselLocationCode
	, ISNULL(OtherSiteLocation	, '_N/A')															AS OtherSiteLocationCode
	, ISNULL(OfficeLocation, '_N/A')																AS EntityLocationCode

	  -- Other

	, ISNULL(DS.DimDateId,'19000101')																														AS DimObservationDateId
--	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, dateUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')	AS DimObservationDateId
 --	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, dateUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))							AS ObservationDateTime
	--, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, ProcessCloseDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))					AS ProcessCloseDate
	, CONVERT(DATETIME, ISNULL(ProcessDate, '1900-01-01'),103)										AS ObservationDateTime
	, TRY_CONVERT(DATE, ISNULL(ProcessClosedOnDate, '1900-01-01'),103)								AS ProcessCloseDate


	, ISNULL(V.VesselName, '_N/A')																	AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																	AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																	AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')																AS OtherSiteName
	, ISNULL(SS.SupportingServiceName, '_N/A')														AS SupportingServiceName
	
	, ISNULL(Closecomments, '_N/A')																	AS CloseComments
	, ISNULL(DescriptionAndProposedAction , '_N/A')													AS DescriptionAndProposedAction 
	, ISNULL(DetailedLocation , '_N/A')																AS DetailedLocation
	, ISNULL(ExplainImmediateActionTaken , '_N/A')													AS ImmediateActionTakenExplanation
	, CONVERT(BIT, CASE WHEN ImmediateActionTaken = 'Yes' THEN 1 ELSE 0 END)						AS ImmediateActionTaken
	, CONVERT(INT, ISNULL(Numberofaddedactions, '0'))												AS TotalActions
	, ISNULL(Observationwillbeassignedto, '_N/A')													AS ObservationWillBeAssignedTo
	, ISNULL(processCloser, '_N/A')																	AS ProcessCloser
	, ISNULL(processOriginator, '_N/A')																AS ProcessOriginator
	, ISNULL(processPriority, '_N/A')																AS ProcessPriority
	, ISNULL(processSubstatus, '_N/A')																AS Substatus
	, ISNULL(ProcessType, '_N/A')																	AS ProcessType
	, ISNULL(processUrlId, '_N/A')																	AS ProcessURLId
	, CONVERT( BIT, CASE WHEN Reportanonymously = 'Yes' THEN 1 ELSE 0 END)							AS ReportedAnonymously
	, ISNULL(Responsibleoffice, '_N/A')																AS ResponsibleOffice
	, ISNULL(Responsibleothersite, '_N/A')															AS ResponsibleOtherSite
	, ISNULL(Responsibleproject, '_N/A')															AS ResponsibleProject
	, ISNULL(Responsiblevessel, '_N/A')																AS ResponsibleVessel
	, ISNULL([Status], '_N/A')																		AS [Status] 
	, ISNULL(Title, '_N/A')																			AS Title
	, CONVERT(NVARCHAR(255), 'Apprise')																AS DataSource
	, '_N/A'																						AS ResDep
	, ISNULL(NULLIF(TrendCategories, ''), '_N/A')													AS TrendCategories
	, COALESCE(NULLIF(ProcessTrendCategories, ''), NULLIF(TrendCategoriesDescription, ''), '_N/A')	AS TrendCategoriesDescription
	, COALESCE(NULLIF(ProcessHRT, ''), NULLIF(HighRiskTask, ''), '_N/A')							AS HighRiskTask
	, COALESCE(NULLIF(ProcessActivity, ''), NULLIF(ActivitiesBlock4, ''), '_N/A')					AS ActivitiesBlock4
	, COALESCE(NULLIF(ProcessSecondaryFactor, ''), NULLIF(SecondaryFactor, ''), '_N/A')				AS SecondaryFactor
	, ISNULL(NULLIF(ReportedBehalfOf, ''), '_N/A')													AS ReportedBehalfOf
	, ISNULL(NULLIF(ReportedBehalfOfDEME, ''), '_N/A')												AS ReportedBehalfOfDEME
	, ISNULL(NULLIF(RadioCards, ''), '_N/A')														AS TypeOfObservation
	, ISNULL(NULLIF(ProcessHRT2, ''), '_N/A')														AS HighRiskTaskLevel2
	, ISNULL(NULLIF(TypeOfOperation, ''), '_N/A')													AS TypeOfOperation
	, ISNULL(NULLIF(processHRTOther, ''), '_N/A')													AS SpecifyOtherHighRiskTask	
	, ISNULL(NULLIF(processTypeOfOperationOther, ''), '_N/A')										AS SpecifyOtherSecondaryFactor
	, ISNULL(NULLIF(ActivityOther, ''), '_N/A')														AS SpecifyOtherActivityAndTechnique

  FROM StagingApprise.Observation O

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT,FORMAT(CONVERT(DATE, ProcessDate, 103),'yyyyMMdd')) = DS.DimDateId	
	
	LEFT JOIN DataStore2.Vessel V
		ON ProcessVesselCode = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON ISNULL(NULLIF(ProcessProjectCode, 'none'), '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON ISNULL(NULLIF(EntityCode, 'none'), '_N/A') = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON ISNULL(NULLIF(ProcessOtherSiteCode, 'none'), '_N/A')	 = OS2.OtherSiteId

	LEFT JOIN DataStore2.SupportingService SS 
		ON O.SupportingServiceCode = SS.SupportingServiceCode

UNION ALL

SELECT 
	ObservationId
	, ObservationId																				AS CustomObservationId
	--, COALESCE(O1.OfficeId,  '_N/A')															AS OfficeId
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END AS LegalEntityId 
	, CASE 
		WHEN COALESCE(PA1.ProjectId, OBS.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  OBS.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END																								AS EntityId
	, COALESCE(OS1.OtherSiteId,  '_N/A')														AS OtherSiteId
	, COALESCE(PA1.ProjectId, OBS.Project, '_N/A' )												AS ProjectId
	, COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselID, 'Not Available'), OBS.Vessel, '_N/A' )  AS VesselId 
	, '_N/A'																					AS CharteredVesselId
    , '_N/A'																					AS SupportingServiceCode  
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')							AS SupportingServiceTibcoIdentifier													
	, '_N/A'																					AS ProjectLocationCode
	, '_N/A'																					AS VesselLocationCode
	, '_N/A'																					AS OtherSiteLocationCode
	, '_N/A'																					AS EntityLocationCode

	  -- Other
	,  ISNULL(DS.DimDateId,'19000101')															AS DimObservationDateId
--	, CONVERT(INT,FORMAT(CONVERT(DATE, ISNULL(Date, '01/01/1900')),'yyyyMMdd'))					AS ObservationDate
	, CONVERT(DATETIME, ISNULL([Date] , '01/01/1900') )											AS ObservationDateTime 
	, CONVERT(DATE, ISNULL([Date] , '01/01/1900') )												AS ProcessCloseDate
	, ISNULL(V.VesselName, '_N/A')	AS VesselName
	, ISNULL(P.ProjectName, '_N/A')	AS ProjectName
	, ISNULL(E.EntityName, '_N/A')	AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')	AS OtherSiteName
	, '_N/A'	AS SupportingServiceName

	, '_N/A'																					AS CloseComments
	, '_N/A'																					AS DescriptionAndProposedAction 
	, '_N/A'																					AS DetailedLocation
	, '_N/A'																					AS ImmediateActionTakenExplanation
	, CONVERT(BIT, 0)																			AS ImmediateActionTaken
	, CONVERT(INT, 0)																			AS TotalActions
	, '_N/A'																					AS ObservationWillBeAssignedTo
	, '_N/A'																					AS ProcessCloser
	, '_N/A'																					AS ProcessOriginator
	, '_N/A'																					AS ProcessPriority
	, '_N/A'																					AS Substatus

	, ISNULL(
			CASE WHEN ObservationClassification = 'Positive observation / Good practice'
					THEN 'Positive observation'
				ELSE ObservationClassification END		
			
		, '_N/A')																				AS ProcessType

	, ObservationId																				AS ProcessURLId
	, CONVERT(BIT, 0)																			AS  ReportedAnonymously
	, '_N/A'																					AS ResponsibleOffice
	, '_N/A'																					AS  ResponsibleOtherSite
	, '_N/A'																					AS ResponsibleProject
	, '_N/A'																					AS ResponsibleVessel
	,  ISNULL(
				CASE WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
					 WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
					 ELSE ST.StatusName END
			 ,'_N/A')					
																								AS [Status] 
	, '_N/A'																					AS Title
	, 'Impact'																					AS DataSource
	, ISNULL(ICD.ImpactDepartmentName, '_N/A')													AS ResDep
	, '_N/A'																					AS TrendCategories
	, '_N/A'																					AS TrendCategoriesDescription
	, '_N/A'																					AS HighRiskTask
	, '_N/A'																					AS ActivitiesBlock4
	, '_N/A'																					AS SecondaryFactor
	, '_N/A'																					AS ReportedBehalfOf
	, '_N/A'																					AS ReportedBehalfOfDEME
	, '_N/A'																					AS TypeOfObservation
	, '_N/A'																					AS HighRiskTaskLevel2
	, '_N/A'																					AS TypeOfOperation
	, '_N/A'																					AS SpecifyOtherHighRiskTask	
	, '_N/A'																					AS SpecifyOtherSecondaryFactor
	, '_N/A'																					AS SpecifyOtherActivityAndTechnique
  FROM StagingImpact.Observation OBS

	LEFT JOIN StagingImpact.[Status] ST
		ON ST.StatusId = OBS.StatusId
	
	-- Resp Dep
	LEFT JOIN StagingGraphAPI.ImpactConversionData ICD
		ON OBS.ResponsibleDepartment = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN StagingGraphAPI.OtherSites OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN StagingGraphAPI.EntitiesBranches EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	
	-- Other POVO Fields

		-- SiteOFfice



		-- Vessel

		LEFT JOIN 
	(
		SELECT 
			  
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
		ON ICD3.ImpactDepartmentName = OBS.Vessel

	LEFT JOIN DataStore2.Project AS PA1
		ON OBS.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(OBS.[Date], '01/01/1900')), 'yyyyMMdd')) = DS.DimDateId	

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselID, 'Not Available'), OBS.Vessel, '_N/A' ) = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(PA1.ProjectId, OBS.Project, '_N/A' ) = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON CASE 
		WHEN COALESCE(PA1.ProjectId, OBS.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  OBS.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END	 = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE(OS1.OtherSiteId,  '_N/A')	 = OS2.OtherSiteId


UNION ALL

-- data source ServiceNow for technical department Zwijndrecht
SELECT 
	  FMD.Id																					AS ObservationId
	, FMD.Id																					AS CustomObservationId

	, '_N/A'																					AS EntityId
	, ISNULL(FMD.OtherSiteCode, '_N/A')															AS OtherSiteId
	, '_N/A'																					AS ProjectId
	, '_N/A'																					AS VesselId 
	, '_N/A'																					AS CharteredVesselId 
    , '_N/A'																					AS SupportingServiceCode     
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')							AS SupportingServiceTibcoIdentifier													
	, '_N/A'																					AS ProjectLocationCode
	, '_N/A'																					AS VesselLocationCode
	, ISNULL(FMD.OtherSiteLocation,'_N/A')														AS OtherSiteLocationCode
	, '_N/A'																					AS EntityLocationCode


	  -- Other
	, ISNULL(DS.DimDateId,'19000101')												AS DimObservationDateId
	, CONVERT(DATETIME, ISNULL(FMD.created, '01/01/1900'), 103)									AS ObservationDateTime 
	, CONVERT(DATE, ISNULL(FMD.closed, '01/01/1900'), 103)										AS ProcessCloseDate

	, '_N/A'																					AS VesselName
	, '_N/A'																					AS ProjectName
	, '_N/A'																					AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')															AS OtherSiteName
	, '_N/A'																					AS SupportingServiceName
	, '_N/A'																					AS CloseComments
	, '_N/A'																					AS DescriptionAndProposedAction 
	, '_N/A'																					AS DetailedLocation
	, '_N/A'																					AS ImmediateActionTakenExplanation
	, CONVERT(BIT, 0)																			AS ImmediateActionTaken
	, CONVERT(INT, 0)																			AS TotalActions
	, '_N/A'																					AS ObservationWillBeAssignedTo
	, '_N/A'																					AS ProcessCloser
	, '_N/A'																					AS ProcessOriginator
	, '_N/A'																					AS ProcessPriority
	, '_N/A'																					AS Substatus
	, ISNULL(FMD.FMDCategory, '_N/A')															AS ProcessType
	, FMD.Id																					AS ProcessURLId
	, CONVERT(BIT, 0)																			AS ReportedAnonymously
	, '_N/A'																					AS ResponsibleOffice
	, '_N/A'																					AS ResponsibleOtherSite
	, '_N/A'																					AS ResponsibleProject
	, '_N/A'																					AS ResponsibleVessel
	,  '_N/A'																					AS [Status] 
	, ISNULL(FMD.ShortDescription, '_N/A')														AS Title
	, 'ServiceNow'																				AS DataSource
	, '_N/A'																					AS ResDep
	, '_N/A'																					AS TrendCategories
	, '_N/A'																					AS TrendCategoriesDescription
	, '_N/A'																					AS HighRiskTask
	, '_N/A'																					AS ActivitiesBlock4
	, '_N/A'																					AS SecondaryFactor
	, '_N/A'																					AS ReportedBehalfOf
	, '_N/A'																					AS ReportedBehalfOfDEME
	, '_N/A'																					AS RadioCards
	, '_N/A'																					AS HighRiskTaskLevel2
	, '_N/A'																					AS TypeOfOperation
	, '_N/A'																					AS SpecifyOtherHighRiskTask	
	, '_N/A'																					AS SpecifyOtherSecondaryFactor
	, '_N/A'																					AS SpecifyOtherActivityAndTechnique
  FROM StagingDataOcean.FMDIncidents FMD

  LEFT JOIN ETL.Date DS 
		ON CONVERT(INT,FORMAT(CONVERT(DATE,FMD.created, 103),'yyyyMMdd')) = DS.DimDateId	

	LEFT JOIN DataStore2.OtherSite OS2
		ON FMD.OtherSiteCode = OS2.OtherSiteId
````
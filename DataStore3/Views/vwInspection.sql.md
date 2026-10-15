# Source: `DBs/AzureSingleDB/DataStore3/Views/vwInspection.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwInspection.sql`
- SHA-256 of original file: `d05abd81c009188a50a7a601e8f9b8ba5fac4718143b4b8aaeef469d5610444d`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE VIEW [DataStore3].[vwInspection] AS 

SELECT DISTINCT
	
	-- BUSINESS KEYS
	  InspectionId
	, ISNULL(ProcessCustomID, '_N/A') AS CustomInspectionId 
	
	--FOREIGN KEYS
	, COALESCE(NULLIF(ProcessProjectCode, 'none'), LEFT(Project, 6),   '_N/A')                              AS ProjectId        -- When the processProjectCode is not filled in, we can get the code out of  the first 6 characters of the description
	, COALESCE(NULLIF(ProcessVesselCode, 'none'), LEFT(Vessel, 4),  '_N/A')                                 AS VesselId         -- When the vesselcode is not filled in, we can get the vesselcode out of the first 4 char from the description
--	, COALESCE(NULLIF(EntityCode, 'none') , EB.EntityBranchId, Entity ,  '_N/A')                            AS LegalEntityId    -- When the OfficeCode is not filled in, use office description to look up officeid, if not found, give description (for screening errors)
--	, COALESCE(NULLIF(EntityCode, 'none') , Entity , '_N/A')												AS LegalEntityId    -- When the enitycode is not filled in, use entity description (for screening errors)
	, COALESCE(NULLIF(EntityCode, 'none') , Entity , '_N/A')												AS EntityId
--	, COALESCE(NULLIF(ProcessOfficeCode, 'none'), O.OfficeId, EB.OfficeId, Office, '_N/A')                  AS OfficeId
--	, COALESCE(NULLIF(ProcessOfficeCode, 'none'), O.OfficeId, Office, '_N/A')								AS OfficeId			-- sometimes processofficode is not filled in but office is
	, COALESCE(NULLIF(ProcessOtherSiteCode, 'none') , OS.OtherSiteId, OtherSite,  '_N/A')                   AS OtherSiteId      -- Same as for office
    , ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')												AS CharteredVesselId
	, ISNULL(I.SupportingServiceCode,'_N/A')                                                                AS SupportingServiceCode
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')									AS SupportingServiceTibcoIdentifier
	, ISNULL(V.VesselName, '_N/A')	AS VesselName
	, ISNULL(P.ProjectName, '_N/A')	AS ProjectName
	, ISNULL(E.EntityName, '_N/A')	AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')	AS OtherSiteName
	, ISNULL(SS.SupportingServiceName, '_N/A')	AS SupportingServiceName

	--ATTRIBUTES
      --Date Attributes

	, ISNULL(DS.DimDateId,'19000101')																		AS DimInspectionDateId
--	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, dateUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')	AS DimInspectionDateId
 	, COALESCE(TRY_CONVERT(DATETIME, ProcessDate, 103),TRY_CONVERT(DATETIME, ProcessDate, 126), '1900-01-01 00:00:00.000')							AS InspectionDateTime

      --Other Attributes
    , ISNULL(ProjectLocation	, '_N/A')							                                        AS ProjectLocationCode 
	, ISNULL(VesselLocation		, '_N/A')							                                        AS VesselLocationCode
	, ISNULL(OtherSiteLocation	, '_N/A')							                                        AS OtherSiteLocationCode
	, ISNULL(OfficeLocation, '_N/A')								                                        AS EntityLocationCode
	, ISNULL(I.ChecklistId, '_N/A')                                                                         AS ChecklistId
	, ISNULL(ExternalInspectorName, '_N/A')                                                                 AS ExternalInspectorName
	, ETL.F_QHSEConvertInt(ISNULL(NumberInspectedQuestions, 0))                                             AS NumberInspectedQuestions
	, ETL.F_QHSEConvertInt(ISNULL(NumberNOKQuestions, 0))                                                   AS NumberNOKQuestions
	, ISNULL(ProcessOpenAction, '_N/A')                                                                     AS ProcessOpenAction
	, ETL.F_QHSEConvertInt(ISNULL(ProcessTotalActions, 0))                                                  AS ProcessTotalAction
	, ISNULL(ProcessOriginator, '_N/A')                                                                     AS ProcessOriginator
	, ISNULL(ProcessPriority, '_N/A')                                                                       AS ProcessPriority
	, ISNULL(Company, '_N/A')                                                                               AS Company
    --, ISNULL(CurrentUser, '_N/A')                                                                         AS CurrentUser
    , ISNULL(DetailedLocation, '_N/A')                                                                      AS DetailedLocation
    , ISNULL(ProcessCloser, '_N/A')                                                                         AS ProcessCloser
    , ISNULL(ProcessDescription, '_N/A')                                                                    AS ProcessDescription
    , ISNULL(ProcessSubject, '_N/A')                                                                        AS ProcessSubject
    , ISNULL(ProcessSubstatus, '_N/A')                                                                      AS Substatus
    , ISNULL(ProcessType, '_N/A')                                                                           AS ProcessType
    , ISNULL(ProcessUrlID   , '_N/A')                                                                       AS ProcessURLId
	, ISNULL(I.Status, '_N/A')                                                                              AS Status
	, 'Apprise'                                                                                             AS DataSource
	, '_N/A' AS ResDep
	, ISNULL(ICL.ChecklistName, '_N/A') AS CheckListName
	, ISNULL(ICL.ChecklistCode, '_N/A') AS CheckListCode
	, ISNULL(ICL.Status, '_N/A') AS CheckListStatus
	, CONVERT(BIT, CASE WHEN ICL.[Statistics] = 'false' THEN 0 ELSE 1 END) AS IncludeStatistics
	, TRIM(ISNULL(NULLIF(REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE(ProcessAssetValue,'[\[\]"]',''),',\s*', ','),'\s+', ''),''),'_N/A'))		AS ProcessAssetValue																
	, ISNULL(NULLIF(ProcessAsset,''), '_N/A')																			AS ProcessAsset
			
   
  FROM StagingApprise.Inspection I 
/*
	LEFT JOIN StagingGraphAPI.EntitiesBranches EB
		ON I.Entity = EB.EntityBranchName
*/
	LEFT JOIN DataStore2.OtherSite OS
		ON I.OtherSite = OS.OtherSiteName

	--LEFT JOIN StagingGraphAPI.Offices O
	--	ON I.Office = O.OfficeName
	--	AND O.OfficeId not in ('O0141-ALD','O0141-ALO','O0141-ALE','O0141-ALI') -- Exception on HQ office because of multiple AL's: these virtual offices are to be ignored in the facts

	LEFT JOIN StagingApprise.InspectionCheckList ICL
		ON I.ChecklistId = ICL.ChecklistId
  
	LEFT JOIN ETL.Date DS 
		ON  ISNULL(CONVERT(INT,FORMAT(COALESCE(TRY_CONVERT(DATETIME, ProcessDate, 103),TRY_CONVERT(DATETIME, ProcessDate, 126)),'yyyyMMdd')),  '19000101') = DS.DimDateId		

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ProcessVesselCode, 'none'), LEFT(Vessel, 4),  '_N/A')  = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(NULLIF(ProcessProjectCode, 'none'), LEFT(Project, 6),   '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON COALESCE(NULLIF(EntityCode, 'none') , Entity , '_N/A') = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE(NULLIF(ProcessOtherSiteCode, 'none') , OS.OtherSiteId, OtherSite,  '_N/A')	 = OS2.OtherSiteId

	LEFT JOIN DataStore2.SupportingService SS 
		ON I.SupportingServiceCode = SS.SupportingServiceCode


UNION ALL

SELECT
    --BUSINESS KEYS
	  InspectionId
	, InspectionId AS CustomInspectionId

    --FOREIGN KEYS
	, COALESCE(PA1.ProjectId, INS.Project, '_N/A')                                                                  AS ProjectId
	, COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId, 'Not Available'),  INS.Vessel, '_N/A' ) AS VesselId 
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END                     AS LegalEntityId 
	, CASE 
		WHEN COALESCE(PA1.ProjectId, INS.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  INS.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END																									AS EntityId
	--, COALESCE(O1.OfficeId, '_N/A')                                                                         AS OfficeId
	, COALESCE(OS1.OtherSiteId,  '_N/A')                                                                    AS OtherSiteId
	, '_N/A'																								AS CharteredVesselId
    , '_N/A'                                                                                                AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')										AS SupportingServiceTibcoIdentifier													
	, ISNULL(V.VesselName, '_N/A')	AS VesselName
	, ISNULL(P.ProjectName, '_N/A')	AS ProjectName
	, ISNULL(E.EntityName, '_N/A')	AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')	AS OtherSiteName
	,  '_N/A'	AS SupportingServiceName


	
    --ATTRIBUTES
      --Date Attributes
	, ISNULL(DS.DimDateId,'19000101')																		AS DimInspectionDateId
--	, ETL.F_QHSEConvertInt(FORMAT(CONVERT( Date, ISNULL([Date], '01/01/1900')), 'yyyyMMdd'))                AS DimInspectionDateId
	, CONVERT(DATETIME, ISNULL([Date] , '01/01/1900') )                                                     AS InspectionDateTime
	
      --Other Attributes
  	, '_N/A'                                                                                                AS ProjectLocation
	, '_N/A'                                                                                                AS VesselLocation
	, '_N/A'                                                                                                AS OtherSiteLocation
	, '_N/A'                                                                                                AS EntityLocation
	, '_N/A'                                                                                                AS ChecklistId
	, '_N/A'                                                                                                AS ExternalInspectorName
	, ETL.F_QHSEConvertInt(0)                                                                               AS NumberInspectedQuestions
	, ETL.F_QHSEConvertInt(0)                                                                               AS NumberNOKQuestions
	, '_N/A'                                                                                                AS ProcessOpenAction
	, ETL.F_QHSEConvertInt(0)                                                                               AS ProcessTotalAction
	, '_N/A'                                                                                                AS ProcessOriginator
	, '_N/A'                                                                                                AS ProcessPriority
	, '_N/A'                                                                                                AS Company   
    , '_N/A'                                                                                                AS DetailedLocation
    , '_N/A'                                                                                                AS ProcessCloser
    , '_N/A'                                                                                                AS ProcessDescription
    , '_N/A'                                                                                                AS  ProcessSubject
    , '_N/A'                                                                                                AS Substatus
    , '_N/A'                                                                                                AS ProcessType
    , InspectionId                                                                                          AS ProcessURLId
	,  ISNULL(
				CASE WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
					 WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
					 ELSE ST.StatusName END
			 ,'_N/A')					
										                                                                    AS [Status]
	, 'Impact'                                                                                              AS DataSource
	, ISNULL(ICD.ImpactDepartmentName, '_N/A') AS ResDep
	,  '_N/A' AS CheckListName
	,  '_N/A' AS CheckListCode
	, '_N/A' AS CheckListStatus
	, 1 AS IncludeStatistics
	, '_N/A'		AS ProcessAssetValue																
	, '_N/A'																		AS ProcessAsset


  FROM StagingImpact.Inspection INS

  LEFT JOIN StagingImpact.[Status] AS ST
		ON ST.StatusId = INS.StatusId


-- RESP Dep
  LEFT JOIN StagingGraphAPI.ImpactConversionData ICD
		ON INS.ResponsibleDepartment = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN StagingGraphAPI.OtherSites OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN StagingGraphAPI.EntitiesBranches EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	LEFT JOIN 
	(
		SELECT 
			  --OfficeId
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
		ON ICD3.ImpactDepartmentName = INS.Vessel

	LEFT JOIN DataStore2.Project AS PA1
		ON INS.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN ETL.Date DS 
		ON CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(INS.[Date], '01/01/1900')), 'yyyyMMdd')) = DS.DimDateId
	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId, 'Not Available'),  INS.Vessel, '_N/A' )   = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(PA1.ProjectId, INS.Project, '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON CASE 
		WHEN COALESCE(PA1.ProjectId, INS.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  INS.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE(OS1.OtherSiteId,  '_N/A')	 = OS2.OtherSiteId
````
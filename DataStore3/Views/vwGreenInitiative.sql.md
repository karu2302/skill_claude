# Source: `DBs/AzureSingleDB/DataStore3/Views/vwGreenInitiative.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwGreenInitiative.sql`
- SHA-256 of original file: `f73eeb76f50d0d0b46b5d8f7f2183141b21aef6ef8f056a712b9f3e411ea622d`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql














CREATE VIEW [DataStore3].[vwGreenInitiative] AS

SELECT DISTINCT
	--BUSINESS KEYS
	  GreenInitiativeId												                                                AS GreenInitiativeId
	, ISNULL(GI.ProcessCustomID, '_N/A')												                            AS CustomGreenInitiativeId -- Do not use as PK, as these are not uniqu    
	
    --FOREIGN KEYS                  
	, COALESCE(NULLIF(GI.ProjectId, 'none'), LEFT(GI.ProjectName, 6), '_N/A')							                AS ProjectId                -- If projectid is not filled in (old records, get code out of description)
	, COALESCE(NULLIF(GI.VesselId, 'none')	    , LEFT(GI.VesselName, 4),  '_N/A') 							        AS VesselId                 -- If vesselid is not filled in, get id out of description
	--, COALESCE(NULLIF(GI.EntityId, 'none')	    , EB.EntityBranchId , GI.EntityName    , '_N/A')					AS LegalEntityId			-- If OfficeId is not filled in, use the description to look for the Id in the office Data
	, COALESCE(NULLIF(GI.EntityId, 'none')	    , EB.EntityBranchId , GI.EntityName    , '_N/A')					AS EntityId
	--, COALESCE(NULLIF(GI.OfficeId, 'none')      , O.OfficeId        , EB.OfficeId      , GI.OfficeName, '_N/A')		AS OfficeId                 -- Office also via legal Entity
	, COALESCE(NULLIF(GI.OtherSiteId, 'none')   , OS.OtherSiteId    , GI.OtherSiteName , '_N/A')					AS OtherSiteId	            -- If OtherSiteId is not filled in, use the description to look for the id in the OtherSite data
    , ISNULL(NULLIF(GI.processCharteredVesselCode, ''), '_N/A')														AS CharteredVesselId
	, ISNULL(GI.SupportingServiceId     , '_N/A')                                                                   AS SupportingServiceCode
	, ISNULL(GI.ProjectLocation	        , '_N/A')							                                        AS ProjectLocationCode          -- Location Descriptions are not longer staged, since we now  lookup facts to configurationloactions
	, ISNULL(GI.VesselLocation		    , '_N/A')							                                        AS VesselLocationCode
	, ISNULL(GI.OtherSiteLocation	    , '_N/A')							                                        AS OtherSiteLocationCode
	, ISNULL(GI.OfficeLocation          , '_N/A')								                                    AS EntityLocationCode
	, ISNULL(V.VesselName, '_N/A')																					AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																					AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																					AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')																				AS OtherSiteName
	, ISNULL(SS.SupportingServiceName, '_N/A')																		AS SupportingServiceName
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')											AS SupportingServiceTibcoIdentifier
	--ATTRIBUTES

	  --Date Attributes
	/*  date fields replaced by UCT date fields
	  , CASE
        WHEN GreenInitiativeDate LIKE '%-%' THEN  CONVERT(INT, FORMAT(CONVERT(DATE, GreenInitiativeDate, 103), 'yyyyMMdd'))
        WHEN GreenInitiativeDate LIKE '%/%' THEN 
            CASE
                WHEN    CONVERT(INT, LEFT(GreenInitiativeDate,2)) <=31 
                    AND CONVERT(INT, RIGHT(LEFT(GreenInitiativeDate, 5),2))>12 THEN CONVERT(INT, FORMAT(CONVERT(DATE, GreenInitiativeDate, 101), 'yyyyMMdd'))
                ELSE    CONVERT(INT, FORMAT(CONVERT(DATE, GreenInitiativeDate, 105), 'yyyyMMdd'))
            END
        ELSE CONVERT(INT, FORMAT(CONVERT(DATE, '1900-01-01'), 'yyyyMMdd'))
       END                                                                                                          AS DimGreenInitiativeDateId
    , CASE
        WHEN GreenInitiativeDate LIKE '%-%' THEN  CONVERT(DATE, GreenInitiativeDate, 103)
        WHEN GreenInitiativeDate LIKE '%/%' THEN 
            CASE
                WHEN    CONVERT(INT, LEFT(GreenInitiativeDate,2)) <=31 
                    AND CONVERT(INT, RIGHT(LEFT(GreenInitiativeDate, 5),2))>12 THEN CONVERT(DATE, GreenInitiativeDate, 101)
                ELSE    CONVERT(DATE, GreenInitiativeDate, 105)
            END
        ELSE CONVERT(DATE, '1900-01-01')
       END                                                                                                          AS GreenInitiativeDate
    , CONVERT(DATETIME, COALESCE(GIClosedDate, ProcessCloseDate, '01/01/1900'), 105)                                AS GreenInitiativeClosedDate 
*/

	--, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, GI.GreenInitiativeDateUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')	AS DimGreenInitiativeDateId
 --	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, GI.GreenInitiativeDateUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS GreenInitiativeDate
	--, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessCloseDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))									AS GreenInitiativeClosedDate 

	, ISNULL(CONVERT(INT,FORMAT(TRY_CONVERT(DATETIME,GI.GreenInitiativeDate,103),'yyyyMMdd')),'19000101')	AS DimGreenInitiativeDateId
 	, TRY_CONVERT(DATETIME, ISNULL(GI.GreenInitiativeDate,'1900-01-01'),103) 							AS GreenInitiativeDate
	, TRY_CONVERT(DATETIME, ISNULL(ProcessCloseDate,'1900-01-01'), 103) 							AS GreenInitiativeClosedDate

	--Location Attributes
	
	, ISNULL(DetailedLocationName, '_N/A')					                                                        AS DetailedDescriptionLocation

	  --Employee Attributes                                 
	, ISNULL(ProcessCloser		, '_N/A')							                                                AS ProcessCloser
	, ISNULL(processOriginator	, '_N/A')							                                                AS GIOriginator
    , ISNULL(GIApprovedBy       , '_N/A')                                                                           AS GIApprovedBy
    , ISNULL(GIUser             , '_N/A')                                                                           AS GIUser

	  --GI Attributes                                    
	, ISNULL(ProcessSubject     , '_N/A')                                                                           AS GISubject
    , ISNULL(ProcessDescription	, '_N/A')							                                                AS GIDescription
    , ISNULL([Status], '_N/A')										                                                AS [Status]	
--	, ISNULL(ProcessSubstatus   , '_N/A')			          		                                                AS Substatus 
	, ISNULL(ProcessType		, '_N/A')							                                                AS GIType  
	, ISNULL(ProcessUrlID   	, '_N/A')							                                                AS ProcessURLId
--	, ISNULL(NULLIF(CONVERT(INT, GI.Score), ''), 0)																	AS GIScore		/** Task 13878  **/
	, ISNULL(NULLIF(CONVERT(INT, GI.Score), ''), 0) + ISNULL(NULLIF(CONVERT(INT, GI.Scorehidden), ''), 0)			AS GIScore
	, ISNULL(GI_YN_MaterialsReused, '_N/A')																			AS MaterialsReused
	, ISNULL([GI_LISTSIN_Ideasuggestion?inlineButtons], '_N/A')														AS IdeaSuggestion


	, ISNULL(GIEnvironmentAspect        , '_N/A')                                                                   AS GIEnvironmentAspect
	, ISNULL(GIFollowUpCommentsSummary  , '_N/A')                                                                   AS GIFollowUpCommentsSummary
	, ISNULL(GIImpact                   , '_N/A')                                                                   AS GIImpact
	, ISNULL(GIProcess                  , '_N/A')                                                                   AS GIProcess
	, COALESCE(ProcessSubstatus, GIRejectedOrApproved, '_N/A')                                                      AS GIRejectedOrApproved
	, ISNULL(GIResult                   , '_N/A')                                                                   AS GIResult
	, 'Apprise'                                                                                                     AS DataSource
	, '_N/A' AS ResDep
	, ISNULL(NULLIF(processActivity, ''), '_N/A')																	AS ProcessActivity
	, ISNULL(NULLIF(processActivityOther, ''), '_N/A')																AS ProcessActivityOther
	, ISNULL(NULLIF(ImpactInlineButtons, ''), '_N/A')																AS ImpactInlineButtons
	, ISNULL(NULLIF(EffortInlineButtons, ''), '_N/A')																AS EffortInlineButtons
   	, ISNULL(NULLIF(GI_YN_EmissionReductionMethodOfOperations, ''), '_N/A')											AS EmissionReductionMethodOfOperations -- Task 30622
    , ISNULL(NULLIF(GI_YN_EmissionReductionTechnicalIntervention, ''), '_N/A')										AS EmissionReductionTechnicalIntervention --Task 30622
    , ISNULL(NULLIF(GI_YN_OtherEmissionReduction, ''), '_N/A')														AS OtherEmissionReduction --Task 30622
	, ISNULL(NULLIF(GI_LST_ApprovalStatus, ''), '_N/A')																AS ApprovalStatus --Task 30622
	, ISNULL(NULLIF(FB_LST_EffortInlineButtons, ''), '_N/A')														AS FeedbackEffort --Task 30622
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FB_NUM_EffortScore,',','.')), 0)									AS EffortScore  --Task 30622
	, ISNULL(NULLIF(FB_LST_ImpactInlineButtons, ''), '_N/A')														AS FeedbackImpact --Task 30622
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FB_NUM_ImpactScore,',','.')), 0)									AS ImpactScore  --Task 30622
	, ISNULL(NULLIF(FB_LST_ApplicabilityInlineButtons, ''), '_N/A')													AS FeedbackApplicability --Task 30622
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FB_NUM_ApplicabilityScore,',','.')), 0)								AS ApplicabilityScore --Task 30622
	, ISNULL(NULLIF(FB_LST_OriginalityInlineButtons, ''), '_N/A')													AS FeedbackOriginality --Task 30622
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FB_NUM_OriginalityScore,',','.')), 0)								AS OriginalityScore--Task 30622
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FB_NUM_FinalScore,',','.')), 0)										AS FinalScore --Task 30622
	, CONVERT(BIT, CASE WHEN GI.WorldCleanupCampaign ='Yes' THEN 1
					ELSE 0 END)																						AS WorldCleanupCampaign
    ,ISNULL(NULLIF(GI.[CompletedBy],''),'_N/A')                                                                        AS [CompletedBy]
    ,ISNULL(NULLIF(GI.[CompletedDate],''),'_N/A')                                                                      AS [CompletedDate]
    ,ISNULL(NULLIF(GI.[FeedbackRespondent],''),'_N/A')                                                                   AS [FeedbackRespondent]
	,ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(GI.[AmountSaving],',','.')), 0)	                                             AS [AmountSaving]
	,ISNULL(NULLIF(GI.[UnitSaving],''),'_N/A')                                                                   AS [UnitSaving]
FROM StagingApprise.GreenInitiative AS GI
	
	LEFT JOIN StagingGraphAPI.EntitiesBranches AS EB
		ON GI.EntityName = EB.EntityBranchName

	--LEFT JOIN StagingGraphAPI.Offices AS O
	--	ON GI.OfficeName = O.OfficeName
	--	AND O.OfficeId not in ('O0141-ALD','O0141-ALO','O0141-ALE','O0141-ALI') -- Exception on HQ office because of multiple AL's: these virtual offices are to be ignored in the facts

	LEFT JOIN DataStore2.OtherSite AS OS
		ON GI.OtherSiteName = OS.OtherSiteName

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(GI.VesselId, 'none')	    , LEFT(GI.VesselName, 4),  '_N/A') = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(NULLIF(GI.ProjectId, 'none'), LEFT(GI.ProjectName, 6), '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON COALESCE(NULLIF(GI.EntityId, 'none')	    , EB.EntityBranchId , GI.EntityName    , '_N/A') = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON COALESCE(NULLIF(GI.OtherSiteId, 'none')   , OS.OtherSiteId    , GI.OtherSiteName , '_N/A')	 = OS2.OtherSiteId

	LEFT JOIN DataStore2.SupportingService SS 
		ON GI.SupportingServiceId = SS.SupportingServiceCode

WHERE GI.GreenInitiativeDateUTC > '2020-10-01'	-- cut-off date between Apprise and Impact

UNION ALL

SELECT DISTINCT
	  GreenInitiativeId														                                        AS GreenInitiativeId
    , GreenInitiativeId												                                                AS CustomGreenInitiativeId -- Do not use as PK, as these are not uniqu    
	
    --FOREIGN KEYS 

    , COALESCE(PA1.ProjectId, GI.Project,  '_N/A')                                                                  AS ProjectId
	, COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  GI.Vessel, '_N/A')    AS VesselId 
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END                     AS LegalEntityId
	, CASE 
		WHEN COALESCE(PA1.ProjectId, GI.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  GI.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END																											AS EntityId
	--, COALESCE(O1.OfficeId, '_N/A')																					AS OfficeId
	, COALESCE(OS1.OtherSiteId, '_N/A')																				AS OtherSiteId
	, '_N/A'																										AS CharteredVesselId
    , '_N/A'                                                                                                        AS SupportingServiceCode
	,  '_N/A'                                                                                                       AS ProjectLocation
	, '_N/A'                                                                                                        AS VesselLocation
	, '_N/A'                                                                                                        AS OtherSiteLocation
	, '_N/A'                                                                                                        AS EntityLocation
	, ISNULL(V.VesselName, '_N/A')																					AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																					AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																					AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')																				AS OtherSiteName
	, '_N/A'																										AS SupportingServiceName
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')												AS SupportingServiceTibcoIdentifier													



	--ATTRIBUTES
      --Date Attributes
	, CONVERT(INT, FORMAT(CONVERT( [Date], ISNULL([Date], '01/01/1900')), 'yyyyMMdd'))                              AS DimGreenInitiativeId
	, CONVERT(DATE, ISNULL([Date] , '01/01/1900') )																	AS GreenInitiativeDate 
	, '01/01/1900'                                                                                                  AS GreenInitiativeClosedDate

      --Location Attributes
	, '_N/A'                                                                                                        AS DetailedDescriptionLocation

      --Employee Attributes
	, '_N/A'						                                                                                AS ProcessCloser
	, '_N/A'  						                                                                                AS GIOriginator
	, '_N/A'         				                                                                                AS GIApprovedBy
	, '_N/A'						                                                                                AS GIUser

      --GI Attributes

    , '_N/A'                                                                                                       AS GISubject
    , '_N/A'                            							                                               AS GIDescription
    , ISNULL(CASE 
                WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
			    WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
			    ELSE ST.StatusName 
             END
			 ,'_N/A')					                                                                           AS [Status]
--	, '_N/A'                            			          		                                               AS Substatus 
	, '_N/A'                            							                                               AS GIType  
	, GreenInitiativeId                    							                                               AS ProcessURLId
	, 0																											   AS GIScore
	, '_N/A'																										AS MaterialsReused
	, '_N/A'																										AS IdeaSuggestion

    ,  CASE 
		WHEN PlanCategory  = 'Green initiative – air'   THEN 'Air emissions' 
		WHEN PlanCategory= 'Green initiative – energy' THEN  'Energy consumption'
		WHEN PlanCategory = 'Green initiative – fauna / flora' THEN 'Fauna & Flora'
		WHEN PlanCategory = 'Green initiative – soil' THEN 'Soil emissions'
		WHEN PlanCategory =  'Green initiative – water consumption' THEN 'Use of natural resources'
		WHEN PlanCategory = 'Green initiative – Tackling ocean plastics (TOP)' OR PlanCategory = 'Green initiative – waste'   THEN 'Waste'
		WHEN PlanCategory =  'Green initiative – water emission' THEN 'Water emissions'
		ELSE '_N/A'
		END                       AS GIEnvironmentAspect
	, '_N/A'                                                                                                       AS GIFollowUpCommentsSummary
	, '_N/A'                                                                                                       AS GIImpact
	, '_N/A'                                                                                                       AS GIProcess
	, 'Approved'                                                                                                   AS GIRejectedOrApproved
	, '_N/A'                                                                                                       AS GIResult
	, 'Impact'                                                                                                     AS DataSource    
	, ISNULL(ICD.ImpactDepartmentName, '_N/A')																	   AS ResDep
	, '_N/A'																									   AS ProcessActivity
	, '_N/A'																									   AS ProcessActivityOther
	, '_N/A'																									   AS ImpactInlineButtons
	, '_N/A'																									   AS EffortInlineButtons
	, '_N/A'																									   AS EmissionReductionMethodOfOperations -- Task 30622
	, '_N/A'																									   AS EmissionReductionTechnicalIntervention --Task 30622
	, '_N/A'																									   AS OtherEmissionReduction --Task 30622
	, '_N/A'																									   AS ApprovalStatus --Task 30622
	, '_N/A'																									   AS FeedbackEffort --Task 30622
	, 0																											   AS EffortScore --Task 30622
	, '_N/A'																									   AS FeedbackImpact --Task 30622
	, 0																											   AS ImpactScore --Task 30622
	, '_N/A'																									   AS FeedbackApplicability --Task 30622
	, 0																											   AS ApplicabilityScore --Task 30622
	, '_N/A'																									   AS FeedbackOriginality --Task 30622
	, 0																											   AS OriginalityScore --Task 30622
	, 0																											   AS FinalScore --Task 30622
	, CONVERT(BIT, 0)																							   AS WorldCleanupCampaign	
	,ISNULL(NULL,'_N/A')                                                                       AS [CompletedBy]
    ,ISNULL(NULL,'_N/A')                                                                     AS [CompletedDate]
    ,ISNULL(NULL,'_N/A')                                                                  AS [FeedbackRespondent]
	,'0'																				 AS [AmountSaving]
	,'_N/A'																					 AS [UnitSaving]
 FROM StagingImpact.GreenInitiative AS GI

	LEFT JOIN StagingImpact.[Status] AS ST
		ON ST.StatusId = GI.StatusId

	--Responsible Department
	LEFT JOIN StagingGraphAPI.ImpactConversionData AS ICD
		ON GI.ResponsibleDepartment = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices AS O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN StagingGraphAPI.OtherSites AS OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN StagingGraphAPI.EntitiesBranches AS EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	-- Other POVO Fields

	LEFT JOIN 
	(
		SELECT 
			 --OfficeId
			  OtherSiteId
			, EntityBranchID 
			, VesselId
			, ImpactDepartmentName
		FROM StagingGraphAPI.ImpactConversionData AS A
		INNER JOIN (
				SELECT 
					MAX(ImpactDepartmentId) AS MaxId
				FROM StagingGraphAPI.ImpactConversionData 
				GROUP BY ImpactDepartmentName
					) AS B
				ON A.ImpactDepartmentId = B.MaxId
	
	) AS ICD3
	 -- Vessel
		ON ICD3.ImpactDepartmentName = GI.Vessel

/*	ImpactConversionProjectNumber will contain only 1 value instead of multiple values separated by ;	
	LEFT JOIN (
		SELECT TRIM(value) AS ImpactConversion, MIN(ProjectId) AS ProjectId
			FROM DataStore1.Project
			CROSS APPLY STRING_SPLIT(ImpactConversionProjectNumber, ';')
			GROUP BY TRIM(value)
			)	PA1
		ON GI.Project = PA1.ImpactConversion
*/

	LEFT JOIN DataStore2.Project AS PA1
		ON GI.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN DataStore2.Vessel V
		ON COALESCE(NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  GI.Vessel, '_N/A') = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON COALESCE(PA1.ProjectId, GI.Project,  '_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON CASE 
		WHEN COALESCE(PA1.ProjectId, GI.Project, NULLIF(ICD.VesselID, 'Not Available'), NULLIF(ICD3.VesselId,'Not Available'),  GI.Vessel,OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityBranchId, '_N/A' )	
		ELSE '_N/A'
	  END = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON  COALESCE(OS1.OtherSiteId, '_N/A')	= OS2.OtherSiteId
````
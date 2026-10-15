# Source: `DBs/AzureSingleDB/DataStore3/Views/vwWorkingHour.sql`

- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwWorkingHour.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `569dfb81092887b82d958cff0a8f1b06545052dc8a167801a10b885ab92482e5`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql




CREATE VIEW [DataStore3].[vwWorkingHour] AS 
SELECT DISTINCT
	WorkingHourId
	, ISNULL(CASE WHEN ProcessPovoType = 'Project' THEN ProcessPovoCode END,'_N/A')				AS ProjectId
	, ISNULL(CASE WHEN ProcessPovoType = 'Vessel' THEN ProcessPovoCode  END,'_N/A')				AS VesselId
	--, ISNULL(CASE WHEN ProcessPovoType = 'Supporting Service' THEN CASE
	--															WHEN SS.ActivityLineId = 'ALD' THEN 'O0141-ALD'
	--															WHEN SS.ActivityLineId = 'ALO' THEN 'O0141-ALO'
	--															WHEN SS.ActivityLineId = 'ALE' THEN 'O0141-ALE'
	--															WHEN SS.ActivityLineId = 'ALI' THEN 'O0141-ALI'
	--															ELSE 'O0141' END	
	--			WHEN ProcessPovoType = 'Entity' THEN O.OfficeId
	--			WHEN ProcessPovoType = 'Office' THEN ProcessPovoCode  END,'_N/A') AS OfficeId
	--, ISNULL(CASE WHEN ProcessPovoType = 'Entity' THEN ProcessPovoCode END, '_N/A') AS LegalEntityId
	, ISNULL(CASE WHEN ProcessPovoType = 'Entity' THEN ProcessPovoCode END, '_N/A')				AS EntityId
	, ISNULL(CASE WHEN ProcessPovoType = 'Other Site' THEN ProcessPovoCode END, '_N/A')			AS OtherSiteId
	, ISNULL(CASE WHEN ProcessPovoType = 'Supporting service' THEN ProcessPovoCode END, '_N/A') AS SupportingServiceCode
	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, ProcessDateUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')	AS DimWorkingHourDateId
	, CONVERT(NUMERIC(19,6), ISNULL(NumberOfEmployeeHours, 0))									AS NumberOfEmployeeHours
	, CONVERT(NUMERIC(19,6), ISNULL(NumberOfJointVentureHours, 0))								AS NumberOfJointVentureHours
	, CONVERT(NUMERIC(19,6), ISNULL(NumberOfSubcontractorHours, 0))								AS NumberOfSubcontractorHours
	, CONVERT(NUMERIC(19,6), ISNULL(NumberOfTemporaryHours, 0))									AS NumberOfTemporaryHours
	, 'Apprise'																					AS DataSource
	, ISNULL(ProcessPovoType, '_N/A')															AS PovoType
 	, ISNULL(CASE WHEN ProcessPovoType = 'Project' THEN processPOVOLocationCode END,'_N/A')		AS ProjectLocationCode
 	, ISNULL(CASE WHEN ProcessPovoType = 'Vessel' THEN processPOVOLocationCode  END,'_N/A')		AS VesselLocationCode
 	, ISNULL(CASE WHEN ProcessPovoType IN ('Office', 'Entity', 'Supporting Service') THEN processPOVOLocationCode  END,'_N/A') AS EntityLocationCode
 	, ISNULL(CASE WHEN ProcessPovoType = 'Other Site' THEN processPOVOLocationCode END,'_N/A')	AS OtherSiteLocationCode
	, ISNULL(V.VesselName, '_N/A')																AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')															AS OtherSiteName
	, ISNULL(SS.SupportingServiceName, '_N/A')													AS SupportingServiceName
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')						AS SupportingServiceTibcoIdentifier
	, ISNULL(W.ProcessCharteredVesselCode, '_N/A')												AS CharteredVesselId

  FROM StagingApprise.WorkingHour W
  
	LEFT JOIN DataStore2.SupportingService AS SS
		ON W.ProcessPovoCode = SS.SupportingServiceCode

	--LEFT JOIN DataStore2.Office AS O
	--	ON O.EntityBranchId = W.ProcessPovoCode
	LEFT JOIN DataStore2.Vessel V
		ON ISNULL(CASE WHEN ProcessPovoType = 'Vessel' THEN ProcessPovoCode  END,'_N/A') = V.VesselId

	LEFT JOIN DataStore2.Project P 
		ON ISNULL(CASE WHEN ProcessPovoType = 'Project' THEN ProcessPovoCode END,'_N/A') = P.ProjectId

	LEFT JOIN DataStore2.Entity E 
		ON ISNULL(CASE WHEN ProcessPovoType = 'Entity' THEN ProcessPovoCode END, '_N/A') = E.EntityId

	LEFT JOIN DataStore2.OtherSite OS2
		ON ISNULL(CASE WHEN ProcessPovoType = 'Other Site' THEN ProcessPovoCode END, '_N/A')	 = OS2.OtherSiteId


UNION ALL

SELECT 

	CAST(WorkingHourId AS NVARCHAR(255))								AS WorkingHourId
	, '_N/A'															AS ProjectId
	, '_N/A'															AS VesselId
	--, COALESCE(O1.OfficeId, O2.OfficeId,/*DSO.OfficeId,*/  '_N/A')	AS OfficeId
	--, CASE WHEN 
	--	O1.OfficeId IS NOT NULL THEN COALESCE(EB1.EntityBranchId, EB2.EntityBranchId , '_N/A')
	--	ELSE '_N/A' END
	--		AS LegalEntityId
	, CASE 
		WHEN COALESCE( OS1.OtherSiteId, OS2.OtherSiteId) IS NULL 
		THEN COALESCE(EB1.EntityBranchId, EB2.EntityBranchId , '_N/A')
		ELSE '_N/A'	
      END																AS EntityId
	, COALESCE( OS1.OtherSiteId, OS2.OtherSiteId,  '_N/A')				AS OtherSiteId
    , '_N/A'															AS SupportingServiceCode
	, CONVERT(INT,FORMAT(DATE,'yyyyMMdd'))								AS Date 
	, [DEME Employee]													AS NumberOfEmployeeHours
	, 0																	AS NumberOfJointVentureHours
	, [Sub-Contractor DEME]												AS NumberOfSubcontractorHours
	, ([DEME Temps] + [DEME Job students/ apprentices])					AS NumberOfTemporaryHours
	, 'Impact'															AS DataSource
	, 'Office'															AS PovoType
 	, '_N/A'															AS ProjectLocationCode
 	, '_N/A'															AS VesselLocationCode
 	, '_N/A'															AS OfficeLocationCode
 	, '_N/A'															AS OtherSiteLocationCode
	, '_N/A'															AS VesselName
	, '_N/A'															AS ProjectName
	, ISNULL(E.EntityName, '_N/A')										AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')									AS OtherSiteName
	, '_N/A'															AS SupportingServiceName
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	, '_N/A'															AS CharteredVesselId

FROM 
	(
		SELECT * 

		FROM 
			(
				SELECT		
					[Category]
					, [Date]
					, [Hour]
					, Office
					, WorkingHourId
				FROM [StagingImpact].[WorkingHourOffice] WHO
			) SRC
			PIVOT
				(MIN([HOUR]) FOR Category IN (
						[Sub-Contractor DEME]
						,[DEME Employee]
						,[DEME Temps]
						,[DEME Job students/ apprentices]
						)
				) PIV
	) WHO
			
	LEFT JOIN StagingImpact.KpiSite KS 
		ON WHO.Office = KS.SiteId
			
	LEFT JOIN 
		( -- Description - Department <=> 1-n 
			SELECT 
				MIN(DepartmentId) AS DepartmentId
				, SiteDS
			FROM StagingImpact.KpiSiteDepartment
			GROUP BY SiteDS
		) KSD 
		ON KS.SiteDS = KSD.SiteDS

LEFT JOIN StagingGraphAPI.ImpactConversionData ICD 
	ON KSD.DepartmentId = ICD.ImpactDepartmentId

-- Get Office/OS/LE ID via Department
LEFT JOIN StagingGraphAPI.EntitiesBranches EB1
	ON ICD.EntityBranchId = EB1.SharepointId
			
--LEFT JOIN StagingGraphAPI.Offices O1
--	ON ICD.OfficeId = O1.SharepointId

LEFT JOIN StagingGraphAPI.OtherSites OS1
	ON ICD.OtherSiteId = OS1.SharepointId


-- Get Office/LE/OS ID via Description
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

	) ICD2
	ON ICD2.ImpactDepartmentName = KS.SiteDS

		

			--LEFT JOIN StagingGraphAPI.Offices O2
			--	ON ICD2.OfficeId = O2.SharepointId

LEFT JOIN StagingGraphAPI.OtherSites OS2
	ON ICD2.OtherSiteId = OS2.SharepointId

LEFT JOIN StagingGraphAPI.EntitiesBranches EB2
	ON ICD2.EntityBranchId = EB2.SharepointId
				
LEFT JOIN DataStore2.Entity E 
	ON CASE 
		WHEN COALESCE( OS1.OtherSiteId, OS2.OtherSiteId) IS NULL 
		THEN COALESCE(EB1.EntityBranchId, EB2.EntityBranchId , '_N/A')
		ELSE '_N/A'	
      END = E.EntityId

LEFT JOIN DataStore2.OtherSite OS3
	ON COALESCE( OS1.OtherSiteId, OS2.OtherSiteId,  '_N/A') = OS2.OtherSiteId

			--LEFT JOIN DataStore1.Office DSO
			--	ON COALESCE(EB1.EntityBranchId, EB2.EntityBranchId)  = DSO.EntityBranchId

		
			--LEFT JOIN (
			--	SELECT TRIM(value) AS ImpactConversion, MIN(EntityBranchId) AS LegalEntityId, MIN(OfficeId) AS OfficeId
			--		FROM StagingGraphAPI.EntitiesBranches
			--		CROSS APPLY STRING_SPLIT(ImpactConversionDetail, ';')
			--		GROUP BY TRIM(value)
			--		)	EB2
			--	ON KS.SiteDS = EB2.ImpactConversion

			--	LEFT JOIN (
			--	SELECT TRIM(value) AS ImpactConversion, MIN(OfficeId) AS OfficeId
			--		FROM DataStore1.Office
			--		CROSS APPLY STRING_SPLIT(ImpactConversionOfficeName, ';')
			--		GROUP BY TRIM(value)
			--		)	O1
			--	ON KS.SiteDS = O1.ImpactConversion
			
			---- Get Other Site ID via Description
			--LEFT JOIN (
			--	SELECT TRIM(value) AS ImpactConversion, MIN(OtherSiteId) AS OtherSiteId
			--		FROM DataStore1.OtherSite
			--		CROSS APPLY STRING_SPLIT(ImpactConversionDetail, ';')
			--		GROUP BY TRIM(value)
			--		)	OS1
			--	ON KS.SiteDS = OS1.ImpactConversion


UNION ALL 

SELECT 
	CAST(WorkingHourId AS NVARCHAR(255))									AS WorkingHourId
	, COALESCE( PA.ProjectId, WHP.ProjectName, '_N/A')						AS ProjectId
	, '_N/A'																AS VesselId
	--, '_N/A' AS OfficeId
	--, '_N/A' AS LegalEntityId
	, '_N/A'																AS EntityId
	, '_N/A'																AS OtherSiteId	
    , '_N/A'																AS SupportingServiceCode
	, CONVERT(INT,FORMAT(DATE,'yyyyMMdd'))									AS Date
	, ISNULL([DEME Employee], 0)											AS NumberOfEmployeeHours
	, (ISNULL([JV employees], 0) + ISNULL([JV partner employees], 0))		AS NumberOfJointVentureHours
	, (ISNULL([Subcontractors JV partner], 0) + ISNULL([Sub-Contractor DEME], 0) + ISNULL([Sub-Contractor JV], 0) + ISNULL(Supplier, 0) + ISNULL([Subcontractors client], 0)) AS NumberOfSubContractorHours
	, (ISNULL([DEME Temps], 0) + ISNULL([DEME Job students/apprentices], 0)) AS NumberOfTemporaryHours
	, 'Impact'																AS DataSource
	, 'Project'																AS PovoType
 	, '_N/A'																AS ProjectLocationCode
 	, '_N/A'																AS VesselLocationCode
 	, '_N/A'																AS EntityLocationCode
 	, '_N/A'																AS OtherSiteLocationCode
	, '_N/A'																AS VesselName
	, ISNULL(P.ProjectName, '_N/A')											AS ProjectName
	, '_N/A'																AS EntityName
	, '_N/A'																AS OtherSiteName
	, '_N/A'																AS SupportingServiceName
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')		AS SupportingServiceTibcoIdentifier
	, '_N/A'																AS CharteredVesselId
FROM 
	(
		SELECT * 
		FROM 
			(
				SELECT [Category]
					, [Date]
					, [Hour]
					, [ProjectName]
					, WorkingHourId
				FROM [StagingImpact].[WorkingHourProject]
			) src
			pivot
			(	MIN([HOUR]) FOR Category IN (
						[Subcontractors JV partner]
						, [Sub-Contractor DEME]
						, [DEME Employee]
						, [JV employees]
						, [Subcontractors client]
						, [DEME Temps]
						, [DEME Job students/apprentices]
						, [JV partner employees]
						, [Supplier]
						, [Sub-Contractor JV]
			)) PIV
	) WHP

LEFT JOIN DataStore2.Project PA
	ON WHP.ProjectName = PA.ImpactConversionProjectNumber

LEFT JOIN DataStore2.Project P
	ON COALESCE( PA.ProjectId, WHP.ProjectName, '_N/A') = P.ProjectId
``
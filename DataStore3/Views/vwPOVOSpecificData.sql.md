# Source: `DBs/AzureSingleDB/DataStore3/Views/vwPOVOSpecificData.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwPOVOSpecificData.sql`
- SHA-256 of original file: `1506e726a95541638766d1d9de252c6d20427c41ae9264e82d9bbab72cd526fc`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql












CREATE VIEW [DataStore3].[vwPOVOSpecificData] AS

SELECT DISTINCT
    --BUSINESS KEY
	  ProcessURLId                                                                              AS PSDId
    
    --FOREIGN KEYS
--	, ISNULL(ProjectId				, '_N/A')                                                 AS ProjectId
--	, ISNULL(OfficeId				, '_N/A')                                                 AS OfficeId
--	, ISNULL(EntityId				, '_N/A')                                                 AS LegalEntityId
--	, ISNULL(VesselId				, '_N/A')                                                 AS VesselId
--	, ISNULL(OtherSiteId            , '_N/A')                                                 AS OtherSiteId
--	, ISNULL(SupportingServiceId	, '_N/A')                                                 AS SupportingServiceId

	, ISNULL(P.ProjectId, '_N/A')																AS ProjectId
	--, CASE
	--	WHEN SS.SupportingServiceCode IS NULL THEN COALESCE(O.OfficeId, '_N/A')
	--	WHEN SS.ActivityLineId = 'ALD' THEN 'O0141-ALD'
	--	WHEN SS.ActivityLineId = 'ALO' THEN 'O0141-ALO'
	--	WHEN SS.ActivityLineId = 'ALE' THEN 'O0141-ALE'
	--	WHEN SS.ActivityLineId = 'ALI' THEN 'O0141-ALI'
	--	ELSE 'O0141' END																		AS OfficeId
	--, ISNULL(OEB.EntityId, '_N/A')															AS LegalEntityId
	, ISNULL(OEB.EntityId, '_N/A')																AS EntityId
	, ISNULL(V.VesselId, '_N/A')																AS VesselId
	, ISNULL(OS.OtherSiteId, '_N/A')															AS OtherSiteId
	, ISNULL(SS.SupportingServiceCode, '_N/A')                                                  AS SupportingServiceCode
	, ISNULL(SS.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')						AS SupportingServiceTibcoIdentifier
	, ISNULL(V.VesselName, '_N/A')																AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																AS ProjectName
	, ISNULL(OS.OtherSiteName, '_N/A')															AS OtherSiteName
	, ISNULL(OEB.EntityName, '_N/A')															AS EntityName
	, ISNULL(SS.SupportingServiceName, '_N/A')													AS SupportingServiceName
 
 --ATTRIBUTES
      --Date
	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATETIME,ProcessDate,103),'yyyyMMdd')),'19000101')		AS DimPSDDate  
      --PSD attributes
	, ISNULL(PSD.ProcessCloser, '_N/A')                                                         AS ProcessCloser
    , PSD.ProcessUrlId                                                                          AS ProcessUrlId
	, ISNULL(PSD.ProcessCustomId,'_N/A')														AS ProcessCustomId
 
    --FACTS
    , ETL.F_QHSEConvertDecimal(PSD.TotalNumbersSIPD)                                            AS NumberOfSuperintendentUpToProjectDirector
    , ETL.F_QHSEConvertDecimal(PSD.TotalNumbersVessels)                                         AS NumberOfMasterAndChiefEngineer
	, ETL.F_QHSEConvertDecimal(NULLIF(NumberOfISMVessels, ''))									AS NumberOfISMVesselPresent
	, 'Apprise' AS DataSource
 	, ISNULL(CASE WHEN P.ProjectId IS NOT NULL THEN processPOVOLocationCode END,'_N/A') AS ProjectLocationCode
 	, ISNULL(CASE WHEN V.VesselId IS NOT NULL THEN processPOVOLocationCode  END,'_N/A') AS VesselLocationCode
 	, ISNULL(CASE WHEN OEB.EntityId IS NOT NULL THEN processPOVOLocationCode END,'_N/A') AS EntityLocationCode
 	, ISNULL(CASE WHEN OS.OtherSiteId IS NOT NULL THEN processPOVOLocationCode END,'_N/A') AS OtherSiteLocationCode
	, CAST(CASE 
			WHEN PSD.NumberCharteredVessels = '' THEN '0.00'
			WHEN PSD.NumberCharteredVessels IS NULL THEN '0.00'
			ELSE REPLACE(REPLACE(PSD.NumberCharteredVessels, '.', ''), ',', '.')
		--ELSE ISNULL(PSD.NumberCharteredVessels, '0.00') 
			END AS DECIMAL(8,2))																AS NumberCharteredVessels		

	--, ISNULL(CASE WHEN OEB.EntityId IS NOT NULL THEN processPOVOLocationCode END,'_N/A') AS EntityLocationCode
	, ISNULL(NULLIF(ProcessCharteredVesselCode, ''), '_N/A')									AS CharteredVesselId

  FROM StagingApprise.POVOSpecificData PSD
   
	LEFT JOIN DataStore2.Vessel AS V
		ON PSD.POVOId = V.VesselId

	LEFT JOIN DataStore2.Project AS P
		ON PSD.POVOId = P.ProjectId

	LEFT JOIN DataStore2.OtherSite AS OS
		ON PSD.POVOId = OS.OtherSiteId

	--LEFT JOIN DataStore2.Office AS O
	--	ON PSD.POVOId = O.OfficeId
	--	AND O.EntityBranchId = '_N/A'
	
	LEFT JOIN DataStore2.Entity AS OEB
		ON PSD.POVOId = OEB.EntityId
	
	LEFT JOIN DataStore2.SupportingService AS SS
		ON PSD.POVOId = SS.SupportingServiceCode

  UNION ALL

  SELECT 
    --BUSINESS KEY
	  PSDId																						AS PSDId
    
    --FOREIGN KEYS
	, Coalesce(PA1.ProjectId , PSD.ProjectId            , '_N/A')                               AS ProjectId
	--, '_N/A'																					AS OfficeId
	--, '_N/A'																					AS LegalEntityId
	, '_N/A'																					AS EntityId
	, '_N/A'																					AS VesselId
	, '_N/A'																					AS OtherSiteId
	, '_N/A'																					AS SupportingServiceId
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')							AS SupportingServiceTibcoIdentifier	
	, '_N/A'																					AS VesselName
	, ISNULL(PA1.ProjectName, '_N/A')															AS ProjectName
	, '_N/A'																					AS OtherSiteName
	, '_N/A'																					AS EntityName
	, '_N/A'																					AS SupportingServiceName

    --ATTRIBUTES
      --Date
	, CONVERT(INT, FORMAT(CONVERT(DATE, ISNULL(Date, '01/01/1900')), 'yyyyMMdd'))				AS DimPSDDate  

      --PSD attributes
	, '_N/A'																					AS ProcessCloser
    , '_N/A'																					AS ProcessUrlId
	, '_N/A'																					AS ProcessCustomId
 
    --FACTS
    , CONVERT(DECIMAL(19,6), ISNULL([Own SI (Super Intendants up to PM present on site this month], 0))                 AS NumberOfSuperintendentUpToProjectDirector
    , CONVERT(DECIMAL(19,6), ISNULL([Own Chief Engineers and Master present on board this month], 0))                   AS NumberOfMasterAndChiefEngineer
	, CONVERT(DECIMAL(19,6), ISNULL([ISM vessels present on the project this month], 0))								AS NumberOfISMVesselPresent


	, 'Impact'																					AS DataSource
   	, '_N/A'																					AS ProjectLocationCode
 	, '_N/A'																					AS VesselLocationCode
 	, '_N/A'																					AS EntityLocationCode
 	, '_N/A'																					AS OtherSiteLocationCode
	, CONVERT(DECIMAL(8,2), 0.00)																AS NumberCharteredVessels
	, '_N/A'																					AS CharteredVesselId

    
  FROM (
  			SELECT * 
						FROM (
							SELECT		
								Category
								, [Count]
								, Date
								, ProjectId
								, PSDId
							FROM [StagingImpact].POVOSpecificData PSD
							) SRC
						PIVOT(MIN([Count]) FOR Category IN (
									[Number of Closed Action Items prior to 01-Jan-2013]
									, [ISM vessels present on the project this month]
									, [First aiders required on site this month]
									, [First aiders present on site this month]
									, [Number of Closed Action Items over due prior to 01-Jan-2013]
									, [Own Chief Engineers and Master present on board this month]
									, [Planned QHSE-S Inspections]
									, [Planned emergency drills on site this month]
									, [Own SI (Super Intendants up to PM present on site this month]
									, [Planned emergency drills on the vessels working for the project this month]
									)) PIV				
						) PSD

	LEFT JOIN DataStore2.Project AS PA1
		ON PSD.ProjectId = PA1.IMpactConversionProjectNumber
````
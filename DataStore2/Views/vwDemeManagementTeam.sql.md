# Source: `DBs/AzureSingleDB/DataStore2/Views/vwDemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwDemeManagementTeam.sql`
- SHA-256 of original file: `eb69f51227343bacf75a5199b970a8f306a1052f3ba0eb57735beaffdb34429f`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE VIEW [DataStore2].[vwDemeManagementTeam] AS
SELECT
	  DMT.Email
	, DMT.FullName
	, ISNULL(DH.DEME,'_N/A')																				AS DEME
	, ISNULL(DH.ActivityLineId, '_N/A')																		AS ActivityLineId
	, ISNULL(DH.BusinessUnitId, '_N/A')																		AS BusinessUnitId            
    , ISNULL(DH.BusinessGroupId, '_N/A')																	AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')																			AS DivisionId 
	, ISNULL(C.CountryId, '_N/A') AS CountryId
	, ISNULL(SS.SupportingServiceCode, '_N/A') AS SupportingService
	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, DMT.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '20500101')) AS QHSESEndDate
	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, DMT.QHSESStartDate,103) AT TIME ZONE 'Central European Standard Time', '19000101')) AS QHSESStartDate
	, CONVERT(BIT, ISNULL(DMT.Senior,'False')) AS Senior
	, CONVERT(INT, ISNULL(DMT.TargetQHSESVisit, 0) ) AS TargetQHSESVisit
	, CONVERT(INT, ISNULL(DMT.TargetVesselVisit, 0) ) AS TargetVesselVisit
	, CONVERT(BIT, ISNULL(DMT.Activemember, 'False')) AS ActiveMember
	, CONVERT(BIT, ISNULL(DMT.CDWE, 'False')) AS CDWE
	, CONVERT(BIT, ISNULL(DMT.Campus, 'False')) AS Campus
	
FROM StagingGraphAPI.DemeManagementTeam AS DMT

	LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
		ON DOS.SharepointId = DMT.DemeOrganisationalStructureId

	LEFT JOIN ( -- added 25/11/24 to take into account inactive hierarchy. To be moved to new datastore1 view DataStore1.vwDEMEHierarchyHistorical
		SELECT  DISTINCT
			  DEME.Abbrevation				AS DEME
			, AL.Abbrevation				AS ActivityLineId
			, AL.LongDescription			AS ActivityLineName
			, AL.ShortDescription			AS ActivityLineNameShort
			, BG.Abbrevation				AS BusinessGroupId
			, BG.LongDescription			AS BusinessGroupName
			, BG.ShortDescription			AS BusinessGroupNameShort
			, BU.Abbrevation				AS BusinessUnitId
			, BU.LongDescription			AS BusinessUnitName
			, BU.ShortDescription			AS BusinessUnitNameShort
			, D.Abbrevation					AS DivisionId
			, D.LongDescription				AS DivisionName
			, D.ShortDescription			AS DivisionNameShort
			, D.Type						AS Type
			, D.TIBCOIndetifierUUID			AS TibcoIdentifierUUId
			--, D.ParentLevelUUID				AS ParentLevelUUID
			, ISNULL(CONVERT(Date, D.InactiveSince), '1900-01-01')	AS InactiveSince
		
		FROM StagingDataMarket.OrganisationalStructure D
		LEFT JOIN StagingDataMarket.OrganisationalStructure BU
			ON D.ParentLevelUUID = BU.TIBCOIndetifierUUID
			AND D.[Parent Type] = BU.Type
		--	 AND BU.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure BG
			ON BU.ParentLevel = BG.LongDescription
			AND BU.[Parent Type] = BG.Type
		--	 AND BG.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure AL
			ON BG.ParentLevelUUID = AL.TIBCOIndetifierUUID
			AND BG.[Parent Type] = AL.Type
		--	 AND AL.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure DEME
			ON AL.ParentLevelUUID = DEME.TIBCOIndetifierUUID
			AND AL.[Parent Type] = DEME.Type
		WHERE D.Type = 'Division' 
		
		UNION ALL
		
		SELECT DISTINCT
			  DEME.Abbrevation				AS DEME
			, AL.Abbrevation				AS ActivityLineId
			, AL.LongDescription			AS ActivityLineName
			, AL.ShortDescription			AS ActivityLineNameShort
			, BG.Abbrevation				AS BusinessGroupId
			, BG.LongDescription			AS BusinessGroupName
			, BG.ShortDescription			AS BusinessGroupNameShort
			, BU.Abbrevation				AS BusinessUnitId
			, BU.LongDescription			AS BusinessUnitName
			, BU.ShortDescription			AS BusinessUnitNameShort
			, '_N/A'						AS DivisionId
			, '_N/A'						AS DivisionName
			, '_N/A'						AS DivisionNameShort
			, BU.Type						AS Type
			, BU.TIBCOIndetifierUUID		AS TibcoIdentifierUUId
			--, BU.ParentLevelUUID			AS ParentLevelUUID
			, ISNULL(CONVERT(Date, BU.InactiveSince), '1900-01-01')	AS InactiveSince
		
		FROM StagingDataMarket.OrganisationalStructure BU
		LEFT JOIN StagingDataMarket.OrganisationalStructure BG
			ON BU.ParentLevelUUID = BG.TIBCOIndetifierUUID
			AND BU.[Parent Type] = BG.Type
		--	 AND BG.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure AL
			ON BG.ParentLevelUUID = AL.TIBCOIndetifierUUID
			AND BG.[Parent Type] = AL.Type
		--	 AND AL.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure DEME
			ON AL.ParentLevelUUID = DEME.TIBCOIndetifierUUID
			AND AL.[Parent Type] = DEME.Type
		WHERE BU.Type = 'Business Unit'
		
		UNION ALL
		
		SELECT DISTINCT
			  DEME.Abbrevation				AS DEME
			, AL.Abbrevation				AS ActivityLineId
			, AL.LongDescription			AS ActivityLineName
			, AL.ShortDescription			AS ActivityLineNameShort
			, BG.Abbrevation				AS BusinessGroupId
			, BG.LongDescription			AS BusinessGroupName
			, BG.ShortDescription			AS BusinessGroupNameShort
			, '_N/A'						AS BusinessUnitId
			, '_N/A'						AS BusinessUnitName
			, '_N/A'						AS BusinessGroupNameShort
			, '_N/A'						AS DivisionId
			, '_N/A'						AS DivisionName
			, '_N/A'						AS DivisionNameShort
			, BG.Type						AS Type
			, BG.TIBCOIndetifierUUID		AS TibcoIdentifierUUId
			--, BG.ParentLevelUUID			AS ParentLevelUUID
			, ISNULL(CONVERT(Date, BG.InactiveSince), '1900-01-01')	AS InactiveSince
		
		FROM StagingDataMarket.OrganisationalStructure BG
		LEFT JOIN StagingDataMarket.OrganisationalStructure AL
			ON BG.ParentLevelUUID = AL.TIBCOIndetifierUUID
			AND BG.[Parent Type] = AL.Type
		--	AND AL.InactiveSince IS NULL
		LEFT JOIN StagingDataMarket.OrganisationalStructure DEME
			ON AL.ParentLevelUUID = DEME.TIBCOIndetifierUUID
			AND AL.[Parent Type] = DEME.Type
		WHERE BG.Type = 'Business Group'
		
		UNION ALL
		
		SELECT DISTINCT
			  DEME.Abbrevation				AS DEME
			, AL.Abbrevation				AS ActivityLineId
			, AL.LongDescription			AS ActivityLineName
			, AL.ShortDescription			AS ActivityLineNameShort
			, '_N/A'						AS BusinessGroupId
			, '_N/A'						AS BusinessGroupName
			, '_N/A'						AS BusinessGroupNameShort
			, '_N/A'						AS BusinessUnitId
			, '_N/A'						AS BusinessUnitName
			, '_N/A'						AS BusinessGroupNameShort
			, '_N/A'						AS DivisionId
			, '_N/A'						AS DivisionName
			, '_N/A'						AS DivisionNameShort
			, AL.Type						AS Type
			, AL.TIBCOIndetifierUUID		AS TibcoIdentifierUUId
			--, AL.ParentLevelUUID			AS ParentLevelUUID
			, ISNULL(CONVERT(Date, AL.InactiveSince), '1900-01-01')	AS InactiveSince
		
		FROM StagingDataMarket.OrganisationalStructure AL
			LEFT JOIN StagingDataMarket.OrganisationalStructure DEME
			ON AL.ParentLevelUUID = DEME.TIBCOIndetifierUUID
			AND AL.[Parent Type] = DEME.Type
		
		WHERE AL.Type = 'Activity Line'
		
		UNION ALL 
		
		SELECT DISTINCT
			  Abbrevation					AS DEME
			, '_N/A'						AS ActivityLineId
			, '_N/A'						AS ActivityLineName
			, '_N/A'						AS ActivityLineNameShort
			, '_N/A'						AS BusinessGroupId
			, '_N/A'						AS BusinessGroupName
			, '_N/A'						AS BusinessGroupNameShort
			, '_N/A'						AS BusinessUnitId
			, '_N/A'						AS BusinessUnitName
			, '_N/A'						AS BusinessGroupNameShort
			, '_N/A'						AS DivisionId
			, '_N/A'						AS DivisionName
			, '_N/A'						AS DivisionNameShort
			, AL.Type						AS Type
			, AL.TIBCOIndetifierUUID		AS TibcoIdentifierUUId
			--, AL.ParentLevelUUID			AS ParentLevelUUID
			, ISNULL(CONVERT(Date, AL.InactiveSince), '1900-01-01')	AS InactiveSince
		
		FROM StagingDataMarket.OrganisationalStructure AL
		
		WHERE Type = 'Top') AS DH
		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId


--	LEFT JOIN DataStore1.DEMEHierarchy DH
--		ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId

		--LEFT JOIN StagingGraphAPI.ActivityLines AL
		--	ON DMT.ActivityLine = AL.SharepointId
		--LEFT JOIN StagingGraphAPI.BusinessGroups BG
		--	ON DMT.BusinessGroup = BG.SharepointId
		--LEFT JOIN StagingGraphAPI.AreasBusinessUnits ABU
		--	ON DMT.AreaBU = ABU.SharepointId
		--LEFT JOIN StagingGraphAPI.RegionsDivisions RD
		--	ON DMT.RegionDivision = RD.SharepointId

	LEFT JOIN StagingGraphAPI.Countries C
		ON DMT.Country = C.SharepointId
	LEFT JOIN StagingGraphAPI.SupportingService SS
        ON DMT.SupportingService = SS.SharepointId
````
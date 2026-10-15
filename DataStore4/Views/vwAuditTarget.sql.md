# Source: `DBs/AzureSingleDB/DataStore4/Views/vwAuditTarget.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore4/Views/vwAuditTarget.sql`
- SHA-256 of original file: `5cf9e8e1e7ceb9750a50d99b94ae299b2c0c65c8613e228a7a4d98bed61c2b1c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE VIEW [DataStore4].[vwAuditTarget] AS
--old code
/*
SELECT 
	  A.AuditId
	, CONVERT(NVARCHAR(5), ISNULL(NULLIF(OS.ActivityLine, ''), '_N/A'))	AS ActivityLineId	
	, CONVERT(NVARCHAR(5), ISNULL(BG.BusinessGroupId, '_N/A'))			AS BusinessGroupId
	, CONVERT(NVARCHAR(5), ISNULL( ABU.AreaBUId, '_N/A'))				AS AreaBUId
	, CONVERT(NVARCHAR(5), ISNULL( RD.RegionDivisionId, '_N/A'))		AS RegionDivisionId
	, CONVERT(NVARCHAR(5), '_N/A')										AS CountryId
	, ISNULL(SS.value, '_N/A')											AS SupportingServiceCode
	, ISNULL(S.SupportingServiceName, '_N/A')							AS SupportingServiceName
	, CONVERT(NVARCHAR(10), '_N/A')										AS EntityBranchId
	, CONVERT(NVARCHAR(10), '_N/A')										AS VesselId
	, CONVERT(NVARCHAR(10), '_N/A')										AS ProjectId
	, CONVERT(NVARCHAR(10), '_N/A')										AS OfficeId
	, CONVERT(NVARCHAR(10), '_N/A')										AS OtherSiteId
	, CONVERT(NVARCHAR(255), '_N/A')									AS VesselLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS ProjectLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS OfficeLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS OtherSiteLocationCode
	, 'OS'																AS LineFrom
FROM DataStore2.Audit A

LEFT JOIN StagingApprise.AuditOrganisationalStructure OS
	ON OS.Name = A.AuditId
LEFT JOIN DataStore1.AreaBusinessUnit ABU
	ON OS.AreaBU = ABU.AreaBUNameShort
LEFT JOIN DataStore1.BusinessGroup BG
	ON OS.BusinessGroup = BG.BusinessGroupNameShort
LEFT JOIN DataStore1.RegionDivision RD
	ON OS.RegionDivision = RD.RegionDivisionNameShort

CROSS APPLY string_split(SupportingServiceCode, ',') SS

LEFT JOIN DataStore1.SupportingService S
	ON SS.value = S.SupportingServiceCode
*/
--Fix for changed AreaBU's & RegionDivisions in TIBCO but not yet in apprise

SELECT 
	  A.AuditId
	, ISNULL(AL.DEME, '_N/A')											AS DEME
	, CONVERT(NVARCHAR(5), ISNULL(AL.ActivityLineId, '_N/A'))	AS ActivityLineId	
	, CONVERT(NVARCHAR(5), COALESCE(RD.BusinessGroupId, BU.BusinessGroupId, BG.BusinessGroupId, '_N/A'))			AS BusinessGroupId
	, CONVERT(NVARCHAR(5), COALESCE(RD.BusinessUnitId, BU.BusinessUnitId, '_N/A'))				AS BusinessUnitId
	, CONVERT(NVARCHAR(32), ISNULL( RD.DivisionId, '_N/A'))										AS DivisionId
	, CONVERT(NVARCHAR(5), '_N/A')										AS CountryId
	, CONVERT(NVARCHAR(10), '_N/A')										AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	--, CONVERT(NVARCHAR(10), '_N/A')										AS EntityBranchId
	, CONVERT(NVARCHAR(10), '_N/A')										AS EntityId
	, CONVERT(NVARCHAR(10), '_N/A')										AS VesselId
	, CONVERT(NVARCHAR(10), '_N/A')										AS ProjectId
	--, CONVERT(NVARCHAR(10), '_N/A')										AS OfficeId
	, CONVERT(NVARCHAR(10), '_N/A')										AS OtherSiteId
	, CONVERT(NVARCHAR(255), '_N/A')									AS VesselLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS ProjectLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS EntityLocationCode
	, CONVERT(NVARCHAR(255), '_N/A')									AS OtherSiteLocationCode
	, 'OS'																AS LineFrom

FROM DataStore3.Audit A

LEFT JOIN StagingApprise.AuditOrganisationalStructure OS
	ON OS.Name = A.AuditId

LEFT JOIN DataStore1.DEMEHierarchy RD
	ON ISNULL(NULLIF(OS.RegionDivision, ''), '_N/A') = RD.DivisionNameShort
	AND ISNULL(NULLIF(OS.AreaBU, ''), '_N/A') = RD.BusinessUnitNameShort
	AND ISNULL(NULLIF(OS.BusinessGroup, ''), '_N/A') = RD.BusinessGroupNameShort
	AND ISNULL(NULLIF(OS.ActivityLine, ''), '_N/A') = RD.ActivityLineId
	AND RD.Type = 'Division'

LEFT JOIN DataStore1.DEMEHierarchy BU
	ON  ISNULL(NULLIF(OS.AreaBU, ''), '_N/A') = BU.BusinessUnitNameShort
	AND ISNULL(NULLIF(OS.BusinessGroup, ''), '_N/A') = BU.BusinessGroupNameShort
	AND ISNULL(NULLIF(OS.ActivityLine, ''), '_N/A') = BU.ActivityLineId
	AND BU.Type = 'Business Unit'

LEFT JOIN DataStore1.DEMEHierarchy BG
	ON  ISNULL(NULLIF(OS.BusinessGroup, ''), '_N/A') = BG.BusinessGroupNameShort
	AND ISNULL(NULLIF(OS.ActivityLine, ''), '_N/A') = BG.ActivityLineId
	AND BG.Type = 'Business Group'

LEFT JOIN DataStore1.DEMEHierarchy AL
	ON  ISNULL(NULLIF(OS.ActivityLine, ''), '_N/A') = AL.ActivityLineId
	AND AL.Type = 'Activity Line'



--LEFT JOIN 
--	(
--		SELECT DISTINCT OS1.Abbrevation AS RegionDivisionId, OS2.Abbrevation AS ActivityLineId, OS3.Abbrevation AS BusinessGroupId, OS4.Abbrevation AS AreaBUId
--		FROM StagingDataMarket.OrganisationalStructure OS1
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS2
--			ON OS1.ActivityLine = OS2.LongDescription
--			AND OS2.Type = 'Activity Line'
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS3
--			ON OS1.BusinessGroup = OS3.LongDescription
--			AND OS3.Type = 'Business Group'
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS4
--			ON OS1.ParentLevel = OS4.LongDescription
--			AND OS1.ParentType = OS4.Type
--		WHERE OS1.Type = 'Region' OR OS1.Type = 'Division'
--	) RD2
--	ON RD.RegionDivisionId = RD2.RegionDivisionId
--	AND OS.ActivityLine = RD2.ActivityLineId

--LEFT JOIN 
--	(
--		SELECT DISTINCT OS1.Abbrevation AS AreaBUId, OS2.Abbrevation AS ActivityLineId, OS3.Abbrevation AS BusinessGroupId
--		FROM StagingDataMarket.OrganisationalStructure OS1
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS2
--			ON OS1.ActivityLine = OS2.LongDescription
--			AND OS2.Type = 'Activity Line'
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS3
--			ON OS1.BusinessGroup = OS3.LongDescription
--			AND OS3.Type = 'Business Group'
--		WHERE OS1.Type = 'Area' OR OS1.Type = 'Business Unit'
--	) ABU2
--	ON ABU.AreaBUId = ABU2.AreaBUId
--	AND OS.ActivityLine = ABU2.ActivityLineId

--	LEFT JOIN 
--	(
--		SELECT DISTINCT OS1.Abbrevation AS BusinessGroupId, OS2.Abbrevation AS ActivityLineID
--		FROM StagingDataMarket.OrganisationalStructure OS1
--		LEFT JOIN StagingDataMarket.OrganisationalStructure OS2
--			ON OS1.ActivityLine = OS2.LongDescription
--			AND OS2.Type = 'Activity Line'
--		WHERE OS1.Type = 'Business Group'
--	) BG2
--	ON BG.BusinessGroupId = BG2.BusinessGroupId
--	AND OS.ActivityLine = BG2.ActivityLineId


UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(E.DEME,'_N/A')							AS DEME
	, ISNULL(E.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(E.BusinessGroupId, '_N/A')				AS BusinessGroupId
	, ISNULL(E.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(E.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(E.CountryId,'_N/A')					AS CountryId
	, '_N/A'										AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	--, ISNULL(NULLIF(SP.value, ''), '_N/A')			AS EntityBranchId
	, ISNULL(E.EntityId, '_N/A')					AS EntityId
	, '_N/A'										AS VesselId
	, '_N/A'										AS ProjectId
	--, ISNULL(O.OfficeId, '_N/A')					AS OfficeId
	, '_N/A'										AS OtherSiteId
	, '_N/A'										AS VesselLocationCode
	, '_N/A'										AS ProjectLocationCode
	, '_N/A'										AS EntityLocationCode
	, '_N/A'										AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom

FROM DataStore3.Audit A

CROSS APPLY string_split(EntityBranchId, ',') SP

LEFT JOIN DataStore2.Entity E
	ON SP.value = E.EntityId --AND SP.Value <> '_N/A' AND A.DimDateId >= O.DimQHSESOfficeStartDateId AND A.DimDateId <= O.DimQHSESOfficeEndDateId

--LEFT JOIN DataStore2.Office O
--	ON E.EntityId = O.EntityBranchId


	/*
UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(O.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(O.BusinessGroupId, '_N/A')				AS BusinessGroupId
	, ISNULL(O.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(O.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(O.CountryId,'_N/A')					AS CountryId
	, ISNULL(SS.value, '_N/A')						AS SupportingServiceCode
	, ISNULL(S.SupportingServiceName, '_N/A')		AS SupportingServiceName
	--, '_N/A'										AS EntityBranchId
	, '_N/A'										AS EntityId
	, '_N/A'										AS VesselId
	, '_N/A'										AS ProjectId
--	, ISNULL(NULLIF(SP.value, ''), '_N/A')			AS OfficeId
	, '_N/A'										AS OtherSiteId
	, '_N/A'										AS VesselLocationCode
	, '_N/A'										AS ProjectLocationCode
	, ISNULL(A.OfficeLocationCode, '_N/A')			AS OfficeLocationCode
	, '_N/A'										AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom
FROM DataStore3.Audit A

CROSS APPLY string_split(OfficeId, ',') SP

LEFT JOIN DataStore2.Office O
	ON SP.value = O.OfficeId AND O.EntityBranchId = '_N/A'
 
CROSS APPLY string_split(SupportingServiceCode, ',') SS

LEFT JOIN DataStore2.SupportingService S
	ON SS.value = S.SupportingServiceCode
*/

UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(V.DEME,'_N/A')							AS DEME
	, ISNULL(V.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(V.BusinessGroupId, '_N/A')				AS BusinessGroupId
	, ISNULL(V.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(V.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(V.CountryId,'_N/A')					AS CountryId
	, '_N/A'										AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	--, '_N/A'										AS EntityBranchId
	, '_N/A'										AS EntityId
	, ISNULL(NULLIF(SP.value, ''), '_N/A')			AS VesselId
	, '_N/A'										AS ProjectId
	--, '_N/A'										AS OfficeId
	, '_N/A'										AS OtherSiteId
	, ISNULL(A.VesselLocationCode, '_N/A')			AS VesselLocationCode
	, '_N/A'										AS ProjectLocationCode
	, '_N/A'										AS EntityLocationCode
	, '_N/A'										AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom
FROM DataStore3.Audit A

CROSS APPLY string_split(A.VesselId, ',') SP

LEFT JOIN DataStore2.Vessel V
	ON SP.value = V.VesselId


UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(P.DEME,'_N/A')							AS DEME
	, ISNULL(P.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(P.BusinessGroupId, '_N/A')				AS BusinessGroupId
	, ISNULL(P.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(P.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(P.CountryId,'_N/A')					AS CountryId
	, '_N/A'										AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	--, '_N/A'										AS EntityBranchId
	, '_N/A'										AS EntityId
	, '_N/A'										AS VesselId
	, ISNULL(NULLIF(SP.value, ''), '_N/A')			AS ProjectId
	--, '_N/A'										AS OfficeId
	, '_N/A'										AS OtherSiteId
	, '_N/A'										AS VesselLocationCode
	, ISNULL(A.ProjectLocationCode,'_N/A')			AS ProjectLocationCode
	, '_N/A'										AS EntityLocationCode
	, '_N/A'										AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom
FROM DataStore3.Audit A

CROSS APPLY string_split(A.ProjectId, ',') SP

LEFT JOIN DataStore2.Project P
	ON SP.value = P.ProjectId


UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(OS.DEME,'_N/A')						AS DEME
	, ISNULL(OS.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(OS.BusinessGroupId, '_N/A')			AS BusinessGroupId
	, ISNULL(OS.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(OS.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(OS.CountryId,'_N/A')					AS CountryId
	, '_N/A'										AS SupportingServiceCode
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier	
	--, '_N/A'										AS EntityBranchId
	, '_N/A'										AS EntityId
	, '_N/A'										AS VesselId
	, '_N/A'										AS ProjectId
	--, '_N/A'										AS OfficeId
	, ISNULL(NULLIF(SP.value, ''), '_N/A')			AS OtherSiteId
	, '_N/A'										AS VesselLocationCode
	, '_N/A'										AS ProjectLocationCode
	, '_N/A'										AS EntityLocationCode
	, ISNULL(A.OtherSiteLocationCode, '_N/A')		AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom

FROM DataStore3.Audit A

CROSS APPLY string_split(A.OtherSiteId, ',') SP

LEFT JOIN DataStore2.OtherSite OS
	ON SP.value = OS.OtherSiteId

UNION ALL

SELECT 
	  A.AuditId
	, ISNULL(S.DEME,'_N/A')							AS DEME
	, ISNULL(S.ActivityLineId,'_N/A')				AS ActivityLineId	
	, ISNULL(S.BusinessGroupId, '_N/A')				AS BusinessGroupId
	, ISNULL(S.BusinessUnitId, '_N/A')				AS BusinessUnitId
	, ISNULL(S.DivisionId,'_N/A')					AS DivisionId
	, ISNULL(S.CountryId,'_N/A')					AS CountryId
	, ISNULL(SS.value, '_N/A')						AS SupportingServiceCode
	, ISNULL(S.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')	AS SupportingServiceTibcoIdentifier
	--, '_N/A'										AS EntityBranchId
	, '_N/A'										AS EntityId
	, '_N/A'										AS VesselId
	, '_N/A'										AS ProjectId
	--, '_N/A'										AS OfficeId
	, '_N/A'										AS OtherSiteId
	, '_N/A'										AS VesselLocationCode
	, '_N/A'										AS ProjectLocationCode
	, '_N/A'										AS EntityLocationCode
	, '_N/A'										AS OtherSiteLocationCode
	, 'POVO'										AS LineFrom

FROM DataStore3.Audit A

CROSS APPLY string_split(SupportingServiceCode, ',') SS

LEFT JOIN DataStore2.SupportingService S
	ON SS.value = S.SupportingServiceCode
````
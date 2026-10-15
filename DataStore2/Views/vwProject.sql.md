# Source: `DBs/AzureSingleDB/DataStore2/Views/vwProject.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwProject.sql`
- SHA-256 of original file: `6ba2ea043bd7e7cba2b97b33812f28e9f539d1057939643cfcaf63c41bb7bf0d`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql










CREATE VIEW [DataStore2].[vwProject] AS

SELECT 
	  --BUSINESS KEY
	  ISNULL(P.ProjectId, '_N/A')																		                AS ProjectId

	  --FOREIGN KEYS        
	, ISNULL(DH.DEME , '_N/A')																							AS DEME
	, ISNULL(DH.ActivityLineId, '_N/A')																	                AS ActivityLineId
	, ISNULL(DH.ActivityLineNameShort , '_N/A')																			AS ActivityLine
    , ISNULL(DH.BusinessUnitId, '_N/A')																					AS BusinessUnitId             --No Area/Business Unit specified
    , ISNULL(DH.BusinessGroupId, '_N/A')																				AS BusinessGroupId
    , ISNULL(DH.DivisionId, '_N/A')																						AS DivisionId 
	, ISNULL(P.Country, '_N/A')																			                AS CountryId
	, ISNULL(DH.BusinessUnitNameShort, '_N/A')																			AS BusinessUnitName
	, ISNULL(C.CountryName, '_N/A')																						AS CountryName
	, ISNULL(DH.DivisionNameShort, '_N/A')																				AS DivisionName

	  --ATTRIBUTES              
	, ISNULL(P.ProjectName, '_N/A')																		                AS ProjectName
	, ISNULL(P.ProjectTitle, '_N/A')																	                AS ProjectId_Name
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, P.StartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS StartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, P.EndDate,103) AT TIME ZONE 'Central European Standard Time', '9999-01-01'))	AS EndDate
	, ISNULL(P.ProjectWithC02, '_N/A')																	                AS ProjectWithC02
	--, ISNULL(P.Boundary, '_N/A')																		                AS Boundary
	, ISNULL(P.BudgetClosed, '_N/A')																	                AS BudgetClosed
	, ISNULL(P.IMpactConversionProjectNumber, '_N/A')													                AS IMpactConversionProjectNumber
	, ISNULL(NULLIF(P.QHSEStatus,''), '_N/A')																		    AS QHSEStatus
	, ISNULL(DS.DimDateId,'19000101')																					AS DimQHSEStartDateId
	, ISNULL(DE.DimDateId,'99990101')																					AS DimQHSESEndDateId
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, P.QHSEStartDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))								AS QHSEStartDate
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, P.QHSESEndDate,103) AT TIME ZONE 'Central European Standard Time', '9999-01-01'))								AS QHSESEndDate
	, ISNULL(P.QHSESCampaigns, '_N/A')																	                AS QHSESCampaigns
	, CONVERT(NVARCHAR(4000), ISNULL(REPLACE(REPLACE(REPLACE(P.Exclude, '["',''),'","',', '), '"]',''), '_N/A'))		AS Exclude
	, CONVERT(NVARCHAR(4000), ISNULL(REPLACE(REPLACE(REPLACE(P.QHSESCampaignTopic, '["',''),'","',', '), '"]',''), '_N/A'))		AS QHSESCampaignTopic
	, CAST(ISNULL(P.DEMETurnover,0) AS BIGINT)																			AS DEMETurnover
	, ISNULL(P.BudgetEuro, '_N/A')																						AS BudgetEuro
	, CONVERT(BIT, CASE WHEN P.Exclude LIKE '%qhses-green-initiative%' THEN 0
						WHEN DATEDIFF(DAY, P.QHSEStartDate, P.QHSESEndDate)	>= 90 THEN 1
						ELSE 0 END)																						AS GIRequired
	, CONVERT(DATE, ISNULL(CASE WHEN CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time' < '2018-07-01' THEN '1900-01-01'
								WHEN CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time' >= '2018-07-01'
									THEN CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time'
								WHEN DATEADD(YEAR
											, 2018-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time') > '2018-07-01'
									THEN DATEADD(YEAR
											, 2017-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
								ELSE DATEADD(YEAR
											, 2018-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
								END, '1900-01-01'))																		AS GITargetStartDate
	, CONVERT(DATE, ISNULL(CASE WHEN CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time' < '2018-07-01' THEN '2050-12-31'
								WHEN CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time' <= 
									DATEADD(DAY, -1, 
										DATEADD(YEAR, YEAR(CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time')-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time'))
											
									THEN DATEADD(DAY, -1, 
										DATEADD(YEAR, YEAR(CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time')-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time'))
								ELSE DATEADD(DAY, -1, 
										DATEADD(YEAR, 1 + YEAR(CONVERT(DATETIMEOFFSET, P.QHSESEndDate, 103) AT TIME ZONE 'Central European Standard Time')-YEAR(CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time')
											, CONVERT(DATETIMEOFFSET, P.QHSEStartDate, 103) AT TIME ZONE 'Central European Standard Time'))
								END, '2050-12-31'))																					AS GITargetEndDate
	, CONVERT(BIT, CASE WHEN P.JointVenture LIKE 'Yes' THEN 1
						ELSE 0 END)																									AS JointVenture

FROM StagingGraphAPI.ProjectsAX AS P

LEFT JOIN StagingGraphAPI.DemeOrganisationalStructure DOS
	ON DOS.SharepointId = P.DemeOrganisationalStructureId

LEFT JOIN DataStore1.DEMEHierarchy DH
	ON DOS.TibcoIdentifier = DH.TibcoIdentifierUUId



-- Join with StagingGraphAPI.AreaBusinessUnits to find corresponding AreaBUId (via Sharepoint Id)
--LEFT JOIN StagingGraphAPI.AreasBusinessUnits AS ABU
--ON P.AreaBusinessUnitId = ABU.SharepointId

----Fix For Hierarchy
--LEFT JOIN StagingGraphAPI.BusinessGroups AS BG
--    ON ABU.BusinessGroupId = BG.SharepointId

---- Join with StagingGraphAPI.RegionsDivisions to find corresponding RegionDivisionId (via Sharepoint Id)
--LEFT JOIN StagingGraphAPI.RegionsDivisions AS RD
--ON P.RegionDivisionId = RD.SharepointId

LEFT JOIN StagingGraphAPI.Countries C
	ON P.Country = C.CountryId

LEFT JOIN ETL.Date DS 
	ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, P.QHSEStartDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DS.DimDateId

LEFT JOIN ETL.Date DE 
	ON CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET, P.QHSESendDate,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')) = DE.DimDateId
````
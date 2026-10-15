# Source: `DBs/AzureSingleDB/DataStore3/Views/vwAudit.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwAudit.sql`
- SHA-256 of original file: `33dc4bd924333f78402606cb3d7b1b38ce97f0c189b56375a1f5e2e6a45f280c`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE VIEW [DataStore3].[vwAudit] AS
SELECT DISTINCT
	--PK
	  AuditId																																AS AuditId
	, ISNULL(NULLIF(CustomProcessID, ''), '_N/A')																							AS CustomAuditId
	--FK's
	, D.DateKey																																AS DimDateId
	, ISNULL(NULLIF(ProcessProjectCode, ''), '_N/A')																						AS ProjectId
	, ISNULL(NULLIF(ProcessVesselCode, ''), '_N/A')																							AS VesselId
	, ISNULL(NULLIF(ProcessOfficeCode, ''), '_N/A')																							AS OfficeId
	, ISNULL(NULLIF(ProcessOtherSiteCode, ''), '_N/A')																						AS OtherSiteId
	, ISNULL(NULLIF(ProcessEntityCode, ''), '_N/A')																							AS EntityBranchId
	, ISNULL(NULLIF(ProcessEntityCode, ''), '_N/A')																							AS EntityId
	, ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')																				AS CharteredVesselId

	, ISNULL(NULLIF(ProcessProjectLocationCode, ''), '_N/A')																				AS ProjectLocationCode
	, ISNULL(NULLIF(ProcessVesselLocationCode, ''), '_N/A')																					AS VesselLocationCode
	, ISNULL(NULLIF(ProcessOfficeLocationCode, ''), '_N/A')																					AS OfficeLocationCode
	, ISNULL(NULLIF(ProcessOtherSiteLocationCode, ''), '_N/A')																				AS OtherSiteLocationCode

	, ISNULL(NULLIF(ProcessSupportingServiceCode, ''), '_N/A')																				AS SupportingServiceCode
	, ISNULL(V.VesselUnitName, '_N/A')																										AS VesselCodeName
	--Attributes
	, ISNULL(NULLIF(ProcessType, ''), '_N/A')																								AS ProcessType
	, ISNULL(NULLIF(ProcessSubject, ''), '_N/A')																							AS Title
	, ISNULL(NULLIF(ProcessDescription, ''), '_N/A')																						AS Comments
	, ISNULL(NULLIF(Standard, ''), '_N/A')																									AS Standard
	, ISNULL(NULLIF(AuditStatus, ''), '_N/A')																								AS AuditStatus
	--, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessdateUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS AuditDate
	--, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessCloseDate,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS ClosedOn
	, CONVERT(DATETIME, ISNULL(Processdate, '1900-01-01'),103)  																			AS AuditDate
	, CONVERT(DATETIME, ISNULL( ProcessCloseDateText, '1900-01-01'),103)																	AS ClosedOn
	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, Created,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))			AS CreatedDate

	, ISNULL(NULLIF(ProcessDetailedLocation, ''), '_N/A')																					AS DetailedLocation	
	, ISNULL(NULLIF(ActivitiesPerfBlock4, ''), '_N/A')																						AS ActivitiesAndTechniquesBlock4
	, ISNULL(NULLIF(SupplierSubcontractor, ''), '_N/A')																						AS SupplierSubcontractor
	, ISNULL(NULLIF(ALOSupplierSubcontractor, ''), '_N/A')																					AS ALOSupplierSubcontractor
	, ISNULL(NULLIF(TDSupplierSubcontractor, ''), '_N/A')																					AS TDSupplierSubcontractor
	, ISNULL(NULLIF(Client, ''), '_N/A')																									AS Client
	, ISNULL(NULLIF(AuditCoordinator, ''), '_N/A')																							AS AuditCoordinator
	, ISNULL(NULLIF(InternalAuditees, ''), '_N/A')																							AS InternalAuditees
	, ISNULL(NULLIF(InternalAuditors, ''), '_N/A')																							AS InternalAuditors
	, ISNULL(NULLIF(ExternalAuditees, ''), '_N/A')																							AS ExternalAuditees
	, ISNULL(NULLIF(ExternalAuditors, ''), '_N/A')																							AS ExternalAuditors
	, ISNULL(NULLIF(CertificationBody, ''), '_N/A')																							AS CertificationBody
	, ISNULL(NULLIF(HQInvolvement, ''), '_N/A')																								AS HQInvolvement
	, ISNULL(NULLIF(processHRT, ''), '_N/A')																								AS ProcessHRT
	, ISNULL(NULLIF(processHRT2, ''), '_N/A')																								AS ProcessHRT2

	, ISNULL(NULLIF(ProcessSubstatus, ''), '_N/A')																							AS SubStatus
	, ISNULL(NULLIF(ProcessOriginator, ''), '_N/A')																							AS ProcessOriginator
	, ISNULL(NULLIF(ProcessCloser, ''), '_N/A')																								AS ProcessCloser
	, ISNULL(NULLIF(ProcessUrlId, ''), '_N/A')																								AS ProcessUrlId

	--Facts
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberMNC,'')))																			AS NumberMNC
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberNC,'')))																			AS NumberNC
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberRC,'')))																			AS NumberRC
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberND,'')))																			AS NumberND
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberOFI,'')))																			AS NumberOFI
	, CONVERT(INT, ETL.F_QHSEConvertDecimal(NULLIF(NumberP,'')))																			AS NumberP
	, ISNULL(NULLIF(A.QuickScanChecklist, ''), '_N/A')																						AS QuickScanChecklist

FROM StagingApprise.Audit A

CROSS APPLY ETL.F_GetDateKey(CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessdateUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01')), null, 0) D

LEFT JOIN DataStore2.Vessel V
	ON A.ProcessVesselCode = V.VesselId

--WHERE CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, Created,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01')) >= '2021-05-01'
````
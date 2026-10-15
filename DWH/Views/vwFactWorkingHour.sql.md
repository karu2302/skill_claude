# Source: `DBs/AzureSingleDB/DWH/Views/vwFactWorkingHour.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactWorkingHour.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `2a8358ff7af89fd86cf5909029efed9b01fd1e73cf307aef473fa02e009ccf54`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql





CREATE VIEW [DWH].[vwFactWorkingHour] AS 
SELECT 
	ProjectId
    , VesselId
  --  , OfficeId
    , OtherSiteId
	, EntityId
	, CharteredVesselId
    , SupportingServiceCode
    , DimWorkingHourDateId
    , NumberOfEmployeeHours
    , NumberOfJointVentureHours
    , NumberOfSubcontractorHours
    , NumberOfTemporaryHours
	, DataSource
	--, LegalEntityId
	, PovoType
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, VesselLocationCode
	, VesselName
	, ProjectName
	, OtherSiteName
	, EntityName
	, SupportingServiceName
	, SupportingServiceTibcoIdentifier

  FROM DataStore3.WorkingHour
``
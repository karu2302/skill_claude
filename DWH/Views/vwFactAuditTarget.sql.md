# Source: `DBs/AzureSingleDB/DWH/Views/vwFactAuditTarget.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactAuditTarget.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `0a36ec8724b125424ff5317da7bdbc5e90f9e3cf559e2b475ba9c70cc16bbfb5`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql


CREATE VIEW [DWH].[vwFactAuditTarget] AS
SELECT 
	  AuditId
	, DEME
	, ActivityLineId	
	, BusinessGroupId
	, BusinessUnitId
	, DivisionId
	, CountryId
	, SupportingServiceCode
	--, EntityBranchId
	, VesselId
	, ProjectId
	--, OfficeId
	, OtherSiteId
	, EntityId
	, VesselLocationCode
	, ProjectLocationCode
	, EntityLocationCode
	, OtherSiteLocationCode
	, SupportingServiceTibcoIdentifier
	, LineFrom

FROM DataStore4.AuditTarget
``
# Source: `DBs/AzureSingleDB/DWH/Views/vwDimEntity.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwDimEntity.sql`
- SHA-256 of original file: `8336cc49f49d94d6f8883a1ba4950a455d16f91d634105a1b378637a5ab8c9f1`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql








CREATE VIEW [DWH].[vwDimEntity] AS
SELECT 
	  TibcoIdentifier
    , EntityId
	, DEME
    , ActivityLineId
    , BusinessUnitId
    , BusinessGroupId
    , DivisionId
    , CountryId
    , AddressLine
    , PostalCode
   -- , Boundary
    , EntityName
   -- , EntityBranchOldCode
    , EntityType
    , Exclude
    , QHSESCampaigns
    , QHSESCampaignTopic
    , Place
    , DimQHSESEntityStartDateId
    , DimQHSESEntityEndDateId
    , QHSESEntityStartDate
    , QHSESEntityEndDate
   -- , Certified
   -- , CertifiedByALocalNotifiedBody
    , CompanyLegalForm
    , CompanyStatus
   -- , Substatus
    , GIDPBW
    --, ImpactConversionDetail
    , Lead
    --, Management
    --, ManagementExternal
    --, PartOfDEMEIntegratedMS
   -- , PartOfDEMEMultisiteContract
	, GIRequired
	, GITargetEndDate
	, GITargetStartDate
	, Active
  
FROM DataStore2.Entity
````
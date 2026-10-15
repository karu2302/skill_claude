# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimEntity.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimEntity.sql`
- SHA-256 of original file: `661b9ef869342adbb5cf3056712d0c80c1e6b062b20e8f19fd717dbe65860620`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql






CREATE VIEW [SSAS].[vwDimEntity] AS
SELECT 
	  DimEntityId
	, DimDEMEHierarchyId
	, TibcoIdentifier
    , EntityId
    , AddressLine
    , PostalCode
  --  , Boundary
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
    --, Certified
    --, CertifiedByALocalNotifiedBody
    , CompanyLegalForm
    , CompanyStatus
    --, Substatus
    , GIDPBW
   -- , ImpactConversionDetail
    , Lead
    --, PartOfDEMEIntegratedMS
    --, PartOfDEMEMultisiteContract
	, Active
  
FROM DWH.DimEntity
````
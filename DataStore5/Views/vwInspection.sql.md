# Source: `DBs/AzureSingleDB/DataStore5/Views/vwInspection.sql`

- Original repository path: `DBs/AzureSingleDB/DataStore5/Views/vwInspection.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `d9b1649ceee890f2e55d7e1b4bf8359125c3234775e92fd0ff3f2ac57894705c`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql

CREATE VIEW [DataStore5].[vwInspection] AS  
  
WITH CTE_PA AS  
(  
SELECT  CI.InspectionId  InspectionId
   , STRING_AGG(A.Display, ', ') ProcessAsset  
   , CI.ProcessAssetValue  ProcessAssetValue
FROM  DataStore3.Inspection CI 
CROSS APPLY STRING_SPLIT(ProcessAssetValue, ',') ids  
LEFT JOIN StagingGraphAPI.Asset A  
ON   LOWER(A.guid) = LOWER(ids.Value)  
GROUP BY CI.ProcessAssetValue, CI.InspectionId  
)  
  
SELECT   
   I.InspectionId  
 , CustomInspectionId  
 , ProjectId  
 , VesselId  
 --, LegalEntityId  
 , EntityId  
 --, OfficeId  
 , OtherSiteId  
 , CharteredVesselId  
 , SupportingServiceCode  
 , DimInspectionDateId  
 , InspectionDateTime  
 , ProjectLocationCode  
 , VesselLocationCode  
 , OtherSiteLocationCode  
 , EntityLocationCode  
 , VesselName  
 , ProjectName  
 , OtherSiteName  
 , EntityName  
 , SupportingServiceName  
 , SupportingServiceTibcoIdentifier  
 , ChecklistId  
 , ExternalInspectorName  
 , NumberInspectedQuestions  
 , NumberNOKQuestions  
 , ProcessOpenAction  
 , ProcessTotalAction  
 , ProcessOriginator  
 , ProcessPriority  
 , Company  
 , DetailedLocation  
 , ProcessCloser  
 , ProcessDescription  
 , ProcessSubject  
 , Substatus  
 , CASE   
   WHEN MI.InspectionId IS NULL  
   THEN I.ProcessType  
   ELSE 'Management Visit'   
   END          AS ProcessType  
 , ProcessURLId  
 , Status  
 , DataSource  
 , ResDep  
 , CheckListName  
 , CheckListCode  
 , CheckListStatus  
 , IncludeStatistics  
 , CTE_PA.ProcessAssetValue  
 , ISNULL(CTE_PA.ProcessAsset,'_N/A') AS ProcessAsset  
  
FROM DataStore3.Inspection I  
LEFT JOIN   
 (  
  SELECT DISTINCT InspectionId  
  FROM DataStore4.ManagementInspection  
 ) MI  
ON I.InspectionId = MI.InspectionId  
LEFT JOIN CTE_PA  
ON CTE_PA.InspectionId = I.InspectionId
``
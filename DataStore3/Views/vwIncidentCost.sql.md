# Source: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentCost.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentCost.sql`
- SHA-256 of original file: `3cd5e82549a3cd284aed4bfb508f967b6186a304313b7754b8ba14e204a34241`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql








/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DataStore3].[vwIncidentCost] AS 
SELECT
    --BUSINESS KEY
	  CostId

    --FOREIGN KEY
	, IncidentId 

    --ATTRIBUTES
	/* Task 22206
	, ISNULL(CASE 
                WHEN CostDeme = 'Yes' THEN CONVERT(BIT, 1)
                ELSE CONVERT(BIT, 0)
              END, CONVERT(BIT, 0))                                    AS CostDEME */

	, CASE
		WHEN CostOwner IS NOT NULL AND CostOwner <> '' THEN CostOwner
		WHEN CostDeme = 'Yes' THEN 'DEME'
		WHEN CostDeme = 'No' THEN 'External'
		ELSE '_N/A' END										AS CostDEME
	, ETL.F_QHSEConvertDecimal(ISNULL(ValueEuro, 0))        AS ValueEuro
    , ISNULL(EstimatedCostDescription, '_N/A')              AS EstimatedCostDescription
	, ISNULL(OtherTypeOfCost, '_N/A')                       AS OtherTypeOfCost
	, ISNULL(InsuranceCaseReferenceNumber, '_N/A')          AS InsuranceCaseReferenceNumber
	, ISNULL(InsuranceCase, '_N/A')							AS InsuranceCase
	, ISNULL(TypeOfCost, '_N/A')              AS TypeOfCost

  FROM StagingApprise.IncidentCost
````
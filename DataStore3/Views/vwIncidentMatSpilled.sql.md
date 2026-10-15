# Source: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentMatSpilled.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentMatSpilled.sql`
- SHA-256 of original file: `6c1fba6f115339aee6743d045a3526c8e6b57f2213882d7822b74ebe4c687209`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql




/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DataStore3].[vwIncidentMatSpilled] AS 
SELECT 
    --BUSINESS KEY
	  MatSpilledId

    --FOREIGN KEY
	, IncidentId 

    --ATTRIBUTES
	, ETL.F_QHSEConvertDecimal(ISNULL(Amount, 0))       AS Amount -- ',' or '.' as decimal??
	, ISNULL(MaterialSpilledOrReleased, '_N/A')         AS MaterialSpilledOrReleased
	, ISNULL([Medium], '_N/A')                          AS Medium	
	, ISNULL(Unit, '_N/A')                              AS Unit
    
  FROM StagingApprise.IncidentMatSpilled
````
# Source: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentDamageClassification.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentDamageClassification.sql`
- SHA-256 of original file: `420bf6b9d32ac7f49965601aa7fc9c25759625aa463c444c522dcb166e82f2dd`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql





/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DataStore3].[vwIncidentDamageClassification] AS 
SELECT 
    --BUSINESS KEY
	  DamageClassificationId

    --FOREIGN KEY
	, IncidentId 

    --ATTRIBUTES
	, ISNULL(PotentialDamage, '_N/A')                       AS PotentialDamage
	, ETL.F_QHSEConvertInt(ISNULL(Risk, 0))                 AS Risk
	, ETL.F_QHSEConvertInt(ISNULL(SafetyProbability, 0))    AS SafetyProbability
	, ETL.F_QHSEConvertInt(ISNULL(Severity, 0))             AS Severity

  FROM StagingApprise.IncidentDamageClassification
````
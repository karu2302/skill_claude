# Source: `DBs/AzureSingleDB/DWH/Views/vwFactIncidentQHSESResponsible.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactIncidentQHSESResponsible.sql`
- SHA-256 of original file: `8ccb4ef31924d833da335f3b520e36be5c2c60ddc766378d03136c0eb2b4fc5a`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql




/****** Script for SelectTopNRows command from SSMS  ******/


CREATE VIEW [DWH].[vwFactIncidentQHSESResponsible] AS 

SELECT 
	incidentId
	, [Name]
	, [Role]
  FROM DataStore3.IncidentQHSESResponsible
````
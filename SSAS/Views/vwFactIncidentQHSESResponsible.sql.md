# Source: `DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql`
- SHA-256 of original file: `13b9632217ac5f1e11d9e21d73d803c5686f6ce4edcfa0ed37942142b9db381e`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE   VIEW [SSAS].[vwFactIncidentQHSESResponsible] AS
SELECT
	 
	[FactIncidentId]
	, [Name]
	, [Role]
FROM DWH.FactIncidentQHSESResponsible
````
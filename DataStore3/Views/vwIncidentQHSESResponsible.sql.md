# Source: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql`
- SHA-256 of original file: `9f516a91b66e067230082c6edaa4542a78fa6fa27fc563427694d4f324bf2713`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


	
CREATE VIEW [DataStore3].[vwIncidentQHSESResponsible] AS 
	 
SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsibleHQ'              AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsibleHQ , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsibleHQOffice'        AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsibleHQOffice , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsibleHQOtherSite'     AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsibleHQOtherSite , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsibleHQProject'       AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsibleHQProject , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsibleHQVessel'        AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsibleHQVessel , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsiblelocal'           AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsiblelocal , '_N/A'), ',') AS CS


UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsiblelocalOffice'     AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsiblelocalOffice , '_N/A'), ',') AS CS


UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsiblelocalOtherSite'  AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsiblelocalOtherSite , '_N/A'), ',') AS CS

UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsiblelocalProject'    AS [Role]

FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsiblelocalProject , '_N/A'), ',') AS CS


UNION ALL 

SELECT 
      IncidentId                        AS IncidentId
	, CS.value                          AS [Name]
	, 'QHSESResponsiblelocalVessel'     AS [Role]
    
FROM StagingApprise.Incident
CROSS APPLY STRING_SPLIT (ISNULL(QHSESResponsiblelocalVessel , '_N/A'), ',') AS CS
````
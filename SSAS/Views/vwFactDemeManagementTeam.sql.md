# Source: `DBs/AzureSingleDB/SSAS/Views/vwFactDemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwFactDemeManagementTeam.sql`
- SHA-256 of original file: `2aa800e806c223ba53653d3901c621697b9bdc044eedb0bafe002376d99386be`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

/****** Script for SelectTopNRows command from SSMS  ******/
CREATE VIEW [SSAS].[vwFactDemeManagementTeam] AS 
SELECT 
	   DimDEMEHierarchyId
      ,[Email]
      ,[FullName]
      ,[QHSESEndDate]
      ,[QHSESStartDate]
	  ,TargetQHSESVisit
	  ,TargetVesselVisit
	  ,Senior
      ,ActiveMember
	  ,CDWE
	  ,Campus
  FROM [DWH].[FactDemeManagementTeam]
````
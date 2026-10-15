# Source: `DBs/AzureSingleDB/DataStore4/Views/vwManagementInspection.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore4/Views/vwManagementInspection.sql`
- SHA-256 of original file: `ea5cc81a71bb348ce65d63e554f383868c30dbd8796095cd9eac4f19bfe0b5c7`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







/****** Script for SelectTopNRows command from SSMS  ******/



CREATE VIEW [DataStore4].[vwManagementInspection] AS 
SELECT I.InspectionId
	, DMT.Email

FROM DataStore3.Inspection AS I

INNER JOIN DataStore3.InspectionFunction AS IFU
	ON IFU.InspectionId = I.InspectionId

INNER JOIN (SELECT DISTINCT FullName
							, Email
							, QHSESStartDate
							, QHSESEndDate
			FROM DataStore2.DemeManagementTeam) AS DMT
	ON IFU.InspectorName = DMT.FullName
		AND I.InspectionDateTime >= DMT.QHSESStartDate
		AND I.InspectionDateTime <= DMT.QHSESEndDate
````
# Source: `DBs/AzureSingleDB/DataStore2/Views/vwHREmployeeRLS.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwHREmployeeRLS.sql`
- SHA-256 of original file: `588f9fd23e1e5c7260aa872e16962a49d637472c78aad9195bfa88af87b92b01`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql





CREATE VIEW [DataStore2].[vwHREmployeeRLS] AS

SELECT 
	DISTINCT 
	  [EmployeeId]
	, [UserPrincipalName]
	, [FullName]
	, [OrganizationUnitDescription] AS SupervisoryOrganization
	, [JobFamilyDescription] AS JobFamily
	, CASE WHEN OrganizationUnitDescription LIKE '%- HR%' AND ISNULL(JobFamilyDescription,'') <> 'Support' THEN 'HR'
		   WHEN OrganizationUnitDescription LIKE 'CEN - HR - Talent%' THEN 'HR'
		   WHEN OrganizationUnitDescription LIKE '%QHSE%' THEN 'QHSE'
		   WHEN JobFamilyDescription LIKE 'Strategic Project Management' THEN 'SPM'
	  END AS RLSTag
	, CASE WHEN OrganizationUnitDescription LIKE '%- HR%' AND ISNULL(JobFamilyDescription,'') <> 'Support' THEN 'Part of HR Supervisory Org + not in Support JobFamily'
		   WHEN OrganizationUnitDescription LIKE 'CEN - HR - Talent%' THEN 'Part of CEN - HR- Talent'
		   WHEN OrganizationUnitDescription LIKE '%QHSE%' THEN 'Part of QHSE'
		   WHEN JobFamilyDescription LIKE 'Strategic Project Management' THEN 'Part of Strategic Project Managment'
	  END AS AddedByRule
FROM [DataStore1].[HREmployeeRLS] WHERE ( OrganizationUnitDescription LIKE '%- HR%' AND ISNULL(JobFamilyDescription,'') <> 'Support')

OR

OrganizationUnitDescription like 'CEN - HR - Talent%'

OR OrganizationUnitDescription like '%QHSE%'

Or JobFamilyDescription  like 'Strategic Project Management'
````
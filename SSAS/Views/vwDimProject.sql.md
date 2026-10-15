# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimProject.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimProject.sql`
- SHA-256 of original file: `05e17bb81d306f2964f3cec5f54af7e790c42e5b66837343a0e500c0bf84ba07`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql














CREATE   VIEW [SSAS].[vwDimProject] AS
SELECT
	  DimProjectId
	, [DimDEMEHierarchyId]
	, [ProjectName]
    , ProjectId
	, [ProjectId_Name]
	, ActivityLine
	, ActivityLineId
	, [ProjectWithC02]
	--, [Boundary]
	, [BudgetClosed]
	, [QHSEStatus]          
--	, DimQHSEStartDateId                  
--	, DimQHSESEndDateId                   
--	, [QHSESCampaigns]   
--	, QHSESCampaignTopic
--	, [Exclude]
	, DEMETurnover
	, BudgetEuro
-- extra date fields requested, maybe temporarly until changed datamodel (Filip - 7/10/20)
--	, QHSEStartDate
--	, QHSESEndDate
FROM DWH.DimProject
````
# Source: `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_DeleteTestData.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_DeleteTestData.sql`
- SHA-256 of original file: `effb40a0d5f955f1413c190ecb536b62cd9d90fe7ba091fd2263c69ca7fb3a7a`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql




CREATE PROCEDURE [ETL].[SPR_DeleteTestData] AS

DECLARE @SQL1 NVARCHAR(MAX)

DECLARE @Environment NVARCHAR(5) = (    SELECT ConfiguredValue
                                        FROM ETL.S_ProjectParameters
                                        WHERE ConfigurationFilter = 'Environment')
 
IF @Environment ='ACC' BEGIN
;WITH CTE1 AS (
	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''Deleted'', ''Rejected'') '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise') AND (Column_Name = 'ProcessSubStatus')
	   
	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''Deleted''
	,''Draft''
	,''Topic''
	,''Rejected''
	,''Test''
	,''Classification incident''
	) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise') AND (Column_Name = 'Status')

	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	SELECT StatusId From StagingImpact.Status WHERE StatusName IN (
	''Deleted''
	,''Cancelled''
	)) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingImpact') AND (Column_Name = 'StatusId') AND (Table_Name <> 'Status')
	)

	SELECT @SQL1 = STRING_AGG(CAST(Statement AS NVARCHAR(MAX)), ' ') 
		FROM CTE1

	EXEC( @SQL1)
	END 
IF @Environment <> 'ACC' BEGIN

;WITH CTE1 AS (
	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''Deleted'') '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise') AND (Column_Name = 'ProcessSubStatus')
	   
	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''Deleted''
	,''Draft''
	,''Topic''
	,''Rejected''
	,''Test''
	,''Classification incident''
	) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise') AND (Column_Name = 'Status')

	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	SELECT StatusId From StagingImpact.Status WHERE StatusName IN (
	''Deleted''
	,''Cancelled''
	)) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingImpact') AND (Column_Name = 'StatusId') AND (Table_Name <> 'Status')
	
	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''TESTV'',''TESTVALD'' ,''TESTVALO'' ,''TESTVALI'',''TESTVALE'', ''TESTV - Test Vessel'') '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise', 'StagingGraphAPI') AND (Column_Name LIKE '%Vessel%' OR Column_Name = 'VesselId' OR Column_Name like '%PovoCode' OR COLUMN_NAME = 'PovoId')

	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''TESTPR''
	,''TESTPRALD''
	,''TESTPRALO''
	,''TESTPRALI''
	,''TESTPRALE''
	,''TESTPRALOWTGOM''
    , ''TESTPRALD - Test Project HQ QHSE-S ALD''
	, ''TESTPRALO - Test Project HQ QHSE-S ALO''
	, ''TESTPRALI - Test Project HQ QHSE-S ALI''
	, ''TESTPRALE - Test Project HQ QHSE-S ALE''
	, ''Test Project ALO WTG OM''
	, ''TESTPRALOWTGOM - Test Project ALO WTG OM''
	, ''TESTPR - Test Project''
	) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise', 'StagingGraphAPI') AND (Column_Name LIKE '%Project%' or Column_Name LIKE '%PovoCode' OR COLUMN_NAME = 'PovoId')
	
	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''O0319'',
	''O0320'',
	''O0323'',
	''O0322'',
	''O0321'',
	''TESTO - TEST OFFICE'',
	''TESTOALD - TEST OFFICE ALD'',
	''TESTOALE - TEST OFFICE ALE'',
	''TESTOALI - TEST OFFICE ALI'',
	''TESTOALO - TEST OFFICE ALO''
	) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise', 'StagingGraphAPI') AND (Column_Name LIKE '%Office%' OR Column_Name = 'OfficeId' OR Column_Name LIKE '%PovoCode' OR COLUMN_NAME = 'PovoId')
	
	UNION ALL

	SELECT 'Delete from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' WHERE ' + COLUMN_NAME + ' IN (
	''OS0003'',
	''BE - TESTOS - Test Other Site''
	) '
	AS Statement
	FROM information_schema.columns
	WHERE Table_Schema IN ('StagingApprise', 'StagingGraphAPI') AND (Column_Name LIKE '%OtherSite%' OR Column_Name = 'OtherSiteId' OR Column_Name LIKE '%PovoCode' OR COLUMN_NAME = 'PovoId')

) 

SELECT @SQL1 = STRING_AGG(CAST(Statement AS NVARCHAR(MAX)), ' ') 
		FROM CTE1

	EXEC( @SQL1)

 
END
````
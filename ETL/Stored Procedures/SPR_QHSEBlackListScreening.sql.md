# Source: `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_QHSEBlackListScreening.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_QHSEBlackListScreening.sql`
- SHA-256 of original file: `2ecb2a01f9b7920828176166173c7a5665aa1b54b14690cfc1429f7712a02d96`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE PROC [ETL].[SPR_QHSEBlackListScreening] 
@NrOfRows INT = 0 OUTPUT, 
@NrOfErrors INT = 0 OUTPUT

AS


DECLARE @Query NVARCHAR(MAX) = ''

SELECT @Query = @Query + 
    'DELETE F												' + CHAR(10) +                                                                                              
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    INNER JOIN DataStore1.ImpactConversionBlackList BL	' + CHAR(10) +
    '        ON F.VesselId = BL.VesselId					' + CHAR(10) +
    'WHERE F.ProjectId = ''_N/A''							' + CHAR(10) +
    '    AND F.EntityId = ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    INNER JOIN DataStore1.ImpactConversionBlackList BL	' + CHAR(10) +
    '        ON F.ProjectId = BL.ProjectId					' + CHAR(10) +
    'WHERE F.VesselId = ''_N/A''							' + CHAR(10) +
    '    AND F.EntityId = ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    INNER JOIN DataStore1.ImpactConversionBlackList BL	' + CHAR(10) +
    '        ON F.EntityId = BL.EntityId					' + CHAR(10) +
    'WHERE F.VesselId = ''_N/A''							' + CHAR(10) +
    '    AND F.ProjectId = ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLP	' + CHAR(10) +
    '        ON  F.ProjectId = BLP.ProjectId				' + CHAR(10) +
    '        AND BLP.ProjectId IS NOT NULL					' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLV	' + CHAR(10) +
    '        ON  F.VesselId = BLV.VesselId					' + CHAR(10) +
    '        AND BLV.VesselId IS NOT NULL					' + CHAR(10) +
    'WHERE F.EntityId =  ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '    AND BLP.ProjectId IS NOT NULL						' + CHAR(10) +
    '    AND BLV.VesselId IS NOT NULL						' + CHAR(10) + 
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLP	' + CHAR(10) +
    '        ON  F.ProjectId = BLP.ProjectId				' + CHAR(10) +
    '        AND BLP.ProjectId IS NOT NULL					' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLO	' + CHAR(10) +
    '        ON  F.EntityId = BLO.EntityId					' + CHAR(10) +
    '        AND BLO.EntityId IS NOT NULL					' + CHAR(10) +
    'WHERE F.VesselId =  ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '    AND BLP.ProjectId IS NOT NULL						' + CHAR(10) +
    '    AND BLO.EntityId IS NOT NULL						' + CHAR(10) + 
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLO	' + CHAR(10) +
    '        ON  F.EntityId = BLO.EntityId					' + CHAR(10) +
    '        AND BLO.EntityId IS NOT NULL					' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLV	' + CHAR(10) +
    '        ON  F.VesselId = BLV.VesselId					' + CHAR(10) +
    '        AND BLV.VesselId IS NOT NULL					' + CHAR(10) +
    'WHERE F.ProjectId =  ''_N/A''							' + CHAR(10) +
    '    AND F.OtherSiteId = ''_N/A''						' + CHAR(10) +
    '    AND BLO.EntityId IS NOT NULL						' + CHAR(10) +
    '    AND BLV.VesselId IS NOT NULL						' + CHAR(10) + 
    '														' + CHAR(10) +
    'DELETE F												' + CHAR(10) +
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLP	' + CHAR(10) +
    '        ON  F.ProjectId = BLP.ProjectId				' + CHAR(10) +
    '        AND BLP.ProjectId IS NOT NULL					' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLV	' + CHAR(10) +
    '        ON  F.VesselId = BLV.VesselId					' + CHAR(10) +
    '        AND BLV.VesselId IS NOT NULL					' + CHAR(10) +
    '    LEFT JOIN DataStore1.ImpactConversionBlackList BLO	' + CHAR(10) +
    '        ON  F.EntityId = BLO.EntityId					' + CHAR(10) +
    '        AND BLO.EntityId IS NOT NULL					' + CHAR(10) +
    'WHERE F.OtherSiteId =  ''_N/A''						' + CHAR(10) +
    '    AND BLO.EntityId IS NOT NULL						' + CHAR(10) +
    '    AND BLP.ProjectId IS NOT NULL						' + CHAR(10) +
    '    AND BLV.VesselId IS NOT NULL						' + CHAR(10) + 
    '														' + CHAR(10) +
    'UPDATE F SET											' + CHAR(10) + 
    '    VesselId = ''_N/A''								' + CHAR(10) + 
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) + 
    '    INNER JOIN DataStore1.ImpactConversionBlackList BV	' + CHAR(10) + 
    '        ON F.VesselId = BV.VesselId					' + CHAR(10) +
    '														' + CHAR(10) +
    'UPDATE F SET											' + CHAR(10) + 
    '    EntityId = ''_N/A''								' + CHAR(10) + 
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) + 
    '    INNER JOIN DataStore1.ImpactConversionBlackList BO	' + CHAR(10) + 
    '        ON F.EntityId = BO.EntityId					' + CHAR(10) + 
    '														' + CHAR(10) + 
    'UPDATE F SET											' + CHAR(10) + 
    '    ProjectId = ''_N/A''								' + CHAR(10) + 
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) + 
    '    INNER JOIN DataStore1.ImpactConversionBlackList BL	' + CHAR(10) + 
    '        ON F.ProjectId = BL.ProjectId					' + CHAR(10) +
	'														' + CHAR(10) + 
	'UPDATE F SET											' + CHAR(10) + 
    '    SupportingServiceCode = ''_N/A''					' + CHAR(10) + 
    'FROM ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' F			' + CHAR(10) + 
    '    INNER JOIN DataStore1.ImpactConversionBlackList BL	' + CHAR(10) + 
    '        ON F.SupportingServiceCode = BL.SupportingServiceId' + CHAR(10) 

FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_SCHEMA  = 'DataStore3'
    AND TABLE_NAME IN (
              'Action'
            , 'Event'
            , 'Incident'
            , 'Observation'
            , 'Inspection'
            , 'WorkingHour'
            , 'GreenInitiative'
			, 'PovoSpecificData'
    )

--PRINT @Query
EXECUTE sp_ExecuteSQL @Query
````
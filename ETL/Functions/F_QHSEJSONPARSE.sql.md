# Source: `DBs/AzureSingleDB/ETL/Functions/F_QHSEJSONPARSE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/ETL/Functions/F_QHSEJSONPARSE.sql`
- SHA-256 of original file: `6b2c2505091e73bf9ef3889820ef71f1554df2b4a848c7b719086fca723f54eb`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE FUNCTION [ETL].[F_QHSEJSONPARSE](

@JSON  NVARCHAR(2550))
--@COLUMN NVARCHAR(2550))
RETURNS NVARCHAR(2550)
AS
BEGIN
DECLARE @SQL NVARCHAR(255) 
     

 SELECT  @SQL = CONCAT(@SQL, ',', '') + s.value 
from openjson(' {"column" :'  + @json  + '}')
with (
    [column] nvarchar(max) as json
) t
cross apply(
    select *
    from openjson(t.[COLUMN])
    with (
        [Value]           nvarchar(50) '$.LookupValue'
      
    )
) s
RETURN @SQL
END
````
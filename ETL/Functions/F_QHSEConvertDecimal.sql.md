# Source: `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertDecimal.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertDecimal.sql`
- SHA-256 of original file: `664dc3cc8895198549fa2dfe0c8ac848a9ec7a9e05eb812b1c6f8a03c218d229`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE FUNCTION [ETL].[F_QHSEConvertDecimal](

@Value NVARCHAR(255))
RETURNS DECIMAL(19,6)
AS
BEGIN
     RETURN  ISNULL( CONVERT(DECIMAL(19,6), REPLACE(REPLACE(@Value, '.', ''), ',', '.')), 0)
             
END
````
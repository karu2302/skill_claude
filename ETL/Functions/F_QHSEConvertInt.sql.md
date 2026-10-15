# Source: `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertInt.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertInt.sql`
- SHA-256 of original file: `7c0756bc43b2929b0402e117c5f1b65d343d4986a12a343e62d889652195b369`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE FUNCTION [ETL].[F_QHSEConvertInt](

@Value NVARCHAR(255))
RETURNS INT
AS
BEGIN
     RETURN  ISNULL( CONVERT(INT, CONVERT(DECIMAL(19,6), REPLACE(REPLACE(@Value, '.', ''), ',', '.'))), 0)
             
END
````
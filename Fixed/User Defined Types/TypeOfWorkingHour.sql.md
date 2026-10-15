# Source: `DBs/AzureSingleDB/Fixed/User Defined Types/TypeOfWorkingHour.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/Fixed/User Defined Types/TypeOfWorkingHour.sql`
- SHA-256 of original file: `18d3b66bc00c66ae7edf6818e6c822c571543afcaae74bdce5828e288b7cc71a`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [Fixed].[TypeOfWorkingHour] AS TABLE (
    [TypeOfWorkingHour] NVARCHAR (50) NULL);


````
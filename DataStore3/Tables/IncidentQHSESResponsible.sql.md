# Source: `DBs/AzureSingleDB/DataStore3/Tables/IncidentQHSESResponsible.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Tables/IncidentQHSESResponsible.sql`
- SHA-256 of original file: `c4f77f42a1662c018373987d4393907ed58a5c0f609c37a49ec6103d85e25444`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore3].[IncidentQHSESResponsible] (
    [IncidentId] NVARCHAR (255) NULL,
    [Name]       NVARCHAR (255) NOT NULL,
    [Role]       VARCHAR (30)   NOT NULL
);


````
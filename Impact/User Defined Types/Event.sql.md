# Source: `DBs/AzureSingleDB/Impact/User Defined Types/Event.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/Impact/User Defined Types/Event.sql`
- SHA-256 of original file: `eecff2382dc382fad0653efc969ee8e0e28696d707f3b51a80d1d48a97dfbb36`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [Impact].[Event] AS TABLE (
    [AU_AUDITDT]                NVARCHAR (255) NULL,
    [AU_STATUSID]               INT            NULL,
    [AUDITHEADID]               NVARCHAR (255) NULL,
    [DEPARTMENTID]              NVARCHAR (255) NULL,
    [PROJECTNAME]               NVARCHAR (255) NULL,
    [UDF_AU_QHSEE_ATTENDEE_CNT] INT            NULL,
    [UDF_QHSE_EVENT_TYPE_DS]    NVARCHAR (255) NULL,
    [UDF_VESSEL_DS]             NVARCHAR (255) NULL);




````
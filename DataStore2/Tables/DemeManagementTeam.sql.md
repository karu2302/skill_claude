# Source: `DBs/AzureSingleDB/DataStore2/Tables/DemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/DemeManagementTeam.sql`
- SHA-256 of original file: `fa035dcb4adbf58ec19461e22ee60f980378af3a62bff466c7b3f63ac29cdaa7`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[DemeManagementTeam] (
    [Email]             NVARCHAR (255) NULL,
    [FullName]          NVARCHAR (255) NULL,
    [DEME]              NVARCHAR (32)  NOT NULL,
    [ActivityLineId]    NVARCHAR (32)  NOT NULL,
    [BusinessUnitId]    NVARCHAR (32)  NOT NULL,
    [BusinessGroupId]   NVARCHAR (32)  NOT NULL,
    [DivisionId]        NVARCHAR (32)  NOT NULL,
    [CountryId]         NVARCHAR (10)  NOT NULL,
    [SupportingService] NVARCHAR (255) NOT NULL,
    [QHSESEndDate]      DATETIME       NULL,
    [QHSESStartDate]    DATETIME       NULL,
    [Senior]            BIT            NULL,
    [TargetQHSESVisit]  INT            NULL,
    [TargetVesselVisit] INT            NULL,
    [ActiveMember]      BIT            NULL,
    [CDWE]              BIT            NULL,
    [Campus]            BIT            NULL
);










````
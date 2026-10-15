# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/DemeManagementTeam.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/DemeManagementTeam.sql`
- SHA-256 of original file: `d6e3680d74f4e8890bf94502ce08a22f9ced26abecf6a51fc0fca05ebb9506d2`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[DemeManagementTeam] AS TABLE (
    [ActiveMember]                  NVARCHAR (255) NULL,
    [Campus]                        NVARCHAR (255) NULL,
    [CDWE]                          NVARCHAR (255) NULL,
    [Country]                       NVARCHAR (255) NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)  NULL,
    [Email]                         NVARCHAR (255) NULL,
    [FullName]                      NVARCHAR (255) NULL,
    [QHSESEndDate]                  NVARCHAR (255) NULL,
    [QHSESStartDate]                NVARCHAR (255) NULL,
    [Senior]                        NVARCHAR (255) NULL,
    [SupportingService]             NVARCHAR (255) NULL,
    [TargetQHSESVisit]              NVARCHAR (255) NULL,
    [TargetVesselVisit]             NVARCHAR (255) NULL);










````
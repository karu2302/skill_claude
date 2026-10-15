# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/EntitiesBranches.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/EntitiesBranches.sql`
- SHA-256 of original file: `edbe4e5ff26608d9dd4695c915bb390525ccd9033dc26214ccbcd605d9001ff7`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[EntitiesBranches] AS TABLE (
    [AddressLine1]                  NVARCHAR (255)  NULL,
    [EntityBranchId]                NVARCHAR (255)  NULL,
    [CompanyLegalForm]              NVARCHAR (255)  NULL,
    [CompanyStatus]                 NVARCHAR (255)  NULL,
    [CountryCodeAlpha3]             NVARCHAR (255)  NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [EntityBranchActive]            NVARCHAR (255)  NULL,
    [EntityType]                    NVARCHAR (255)  NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [GIDPBW]                        NVARCHAR (255)  NULL,
    [SharepointId]                  INT             NULL,
    [Lead]                          NVARCHAR (255)  NULL,
    [Place]                         NVARCHAR (255)  NULL,
    [PostalCode]                    NVARCHAR (255)  NULL,
    [QHSEScampaigns]                NVARCHAR (255)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [TibcoIdentifier]               NVARCHAR (255)  NULL,
    [EntityBranchName]              NVARCHAR (255)  NULL);
















````
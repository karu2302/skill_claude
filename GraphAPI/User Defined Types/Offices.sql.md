# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/Offices.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/Offices.sql`
- SHA-256 of original file: `0974e7be1ee33355a4717952f2e9f1fdc93a591e1e3b3ee0e0a6b339164aaca0`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[Offices] AS TABLE (
    [ActivityLineId]                NVARCHAR (10)   NULL,
    [Application]                   NVARCHAR (255)  NULL,
    [AreaBUId]                      NVARCHAR (10)   NULL,
    [CountryId]                     NVARCHAR (10)   NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [SharepointId]                  INT             NULL,
    [ImpactConversionOfficeName]    NVARCHAR (4000) NULL,
    [OfficeId]                      NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [RegionDivisionId]              NVARCHAR (255)  NULL,
    [OfficeName]                    NVARCHAR (255)  NULL);




````
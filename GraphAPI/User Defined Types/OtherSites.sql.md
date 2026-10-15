# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/OtherSites.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/OtherSites.sql`
- SHA-256 of original file: `fe00ca01d16869f0cc098a2fdc452d9d89ee245ad7b19b27f242581353cfcef8`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[OtherSites] AS TABLE (
    [CountryId]                     NVARCHAR (10)   NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [Exclude]                       NVARCHAR (255)  NULL,
    [SharepointId]                  INT             NULL,
    [OtherSiteId]                   NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [OtherSiteName]                 NVARCHAR (255)  NULL);










````
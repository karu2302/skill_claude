# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/ProjectsAX.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/ProjectsAX.sql`
- SHA-256 of original file: `a451b8a0500234f41336695b4a175ed50673487e33059f850fa0e06ca2cb7822`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[ProjectsAX] AS TABLE (
    [BudgetClosed]                  NVARCHAR (255)  NULL,
    [BudgetEuro]                    NVARCHAR (255)  NULL,
    [Country]                       NVARCHAR (10)   NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [DEMETurnover]                  NVARCHAR (255)  NULL,
    [EndDate]                       NVARCHAR (50)   NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [ImpactConversionProjectNumber] NVARCHAR (255)  NULL,
    [JointVenture]                  NVARCHAR (10)   NULL,
    [ProjectId]                     NVARCHAR (255)  NULL,
    [ProjectName]                   NVARCHAR (255)  NULL,
    [ProjectWithC02]                NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESendDate]                  NVARCHAR (255)  NULL,
    [QHSEStartDate]                 NVARCHAR (255)  NULL,
    [QHSEStatus]                    NVARCHAR (255)  NULL,
    [StartDate]                     NVARCHAR (255)  NULL,
    [ProjectTitle]                  NVARCHAR (255)  NULL);










````
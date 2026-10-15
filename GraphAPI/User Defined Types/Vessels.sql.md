# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/Vessels.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/Vessels.sql`
- SHA-256 of original file: `9256a6d35d2e76742ddee6bf0e052b8009bb29fbd903a035c4ad3f528fee0190`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[Vessels] AS TABLE (
    [ClassificationSociety]         NVARCHAR (255)  NULL,
    [CSRD]                          NVARCHAR (255)  NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)   NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [FuelType]                      NVARCHAR (255)  NULL,
    [GT]                            NVARCHAR (255)  NULL,
    [ISM]                           NVARCHAR (255)  NULL,
    [ManagementVisitScope]          NVARCHAR (255)  NULL,
    [QHSESCampaigns]                NVARCHAR (255)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [QHSESEndDate]                  NVARCHAR (255)  NULL,
    [QHSESStartDate]                NVARCHAR (255)  NULL,
    [RMPE]                          NVARCHAR (255)  NULL,
    [VesselId]                      NVARCHAR (255)  NULL,
    [VesselUnitName]                NVARCHAR (255)  NULL,
    [VesselActive]                  NVARCHAR (10)   NULL,
    [VesselLifecycleStatus]         NVARCHAR (255)  NULL,
    [VesselName]                    NVARCHAR (255)  NULL,
    [VMSType]                       NVARCHAR (255)  NULL);
















````
# Source: `DBs/AzureSingleDB/GraphAPI/User Defined Types/SupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/User Defined Types/SupportingService.sql`
- SHA-256 of original file: `790bdd4d3a92bc5b81247205977e63e66a67497bc7b428ab9d9220e439366e42`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TYPE [GraphAPI].[SupportingService] AS TABLE (
    [SupportingServiceId]           NVARCHAR (10)  NULL,
    [DemeOrganisationalStructureId] NVARCHAR (10)  NULL,
    [Exclude]                       NVARCHAR (10)  NULL,
    [SharepointId]                  INT            NULL,
    [InactiveSince]                 NVARCHAR (255) NULL,
    [QHSESCampaigns]                NVARCHAR (10)  NULL,
    [QHSESCampaignTopic]            NVARCHAR (MAX) NULL,
    [QHSESEndDate]                  NVARCHAR (255) NULL,
    [SupportingServiceCode]         NVARCHAR (255) NULL,
    [TIBCOIdentifier]               NVARCHAR (255) NULL,
    [SupportingServiceName]         NVARCHAR (255) NULL);














````
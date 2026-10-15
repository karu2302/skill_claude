# Source: `DBs/AzureSingleDB/DataStore2/Tables/Entity.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/Entity.sql`
- SHA-256 of original file: `4d369a897dcaee29ef5f96ed58e8bec34840aad10a065453584d0e11ad25d7db`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[Entity] (
    [TibcoIdentifier]           UNIQUEIDENTIFIER NOT NULL,
    [SharepointId]              INT              NULL,
    [EntityId]                  NVARCHAR (255)   NOT NULL,
    [DEME]                      NVARCHAR (10)    NOT NULL,
    [ActivityLineId]            NVARCHAR (10)    NOT NULL,
    [BusinessUnitId]            NVARCHAR (10)    NOT NULL,
    [BusinessGroupId]           NVARCHAR (10)    NOT NULL,
    [DivisionId]                NVARCHAR (10)    NOT NULL,
    [CountryId]                 NVARCHAR (5)     NOT NULL,
    [AddressLine]               NVARCHAR (255)   NOT NULL,
    [PostalCode]                NVARCHAR (50)    NOT NULL,
    [EntityName]                NVARCHAR (255)   NOT NULL,
    [EntityType]                NVARCHAR (255)   NOT NULL,
    [Exclude]                   NVARCHAR (4000)  NULL,
    [QHSESCampaigns]            NVARCHAR (10)    NULL,
    [QHSESCampaignTopic]        NVARCHAR (4000)  NULL,
    [Place]                     NVARCHAR (255)   NOT NULL,
    [DimQHSESEntityStartDateId] INT              NOT NULL,
    [DimQHSESEntityEndDateId]   INT              NOT NULL,
    [QHSESEntityStartDate]      DATE             NULL,
    [QHSESEntityEndDate]        DATE             NULL,
    [CompanyLegalForm]          NVARCHAR (255)   NOT NULL,
    [CompanyStatus]             NVARCHAR (255)   NOT NULL,
    [GIDPBW]                    NVARCHAR (10)    NULL,
    [Lead]                      NVARCHAR (10)    NULL,
    [GIRequired]                BIT              NULL,
    [GITargetStartDate]         DATE             NULL,
    [GITargetEndDate]           DATE             NULL,
    [Active]                    BIT              NULL
);
















````
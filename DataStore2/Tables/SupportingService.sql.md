# Source: `DBs/AzureSingleDB/DataStore2/Tables/SupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/SupportingService.sql`
- SHA-256 of original file: `7d169a3434c59c80ee9e29e2857f8d26608417a3df68aa7a34b3ae2c977bd90d`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[SupportingService] (
    [TibcoIdentifier]            UNIQUEIDENTIFIER NOT NULL,
    [SupportingServiceCode]      NVARCHAR (255)   NULL,
    [SupportingServiceId]        NVARCHAR (10)    NOT NULL,
    [SupportingServiceName]      NVARCHAR (255)   NULL,
    [DEME]                       NVARCHAR (32)    NOT NULL,
    [ActivityLineId]             NVARCHAR (32)    NOT NULL,
    [BusinessUnitId]             NVARCHAR (32)    NOT NULL,
    [BusinessGroupId]            NVARCHAR (32)    NOT NULL,
    [DivisionId]                 NVARCHAR (32)    NOT NULL,
    [CountryId]                  VARCHAR (4)      NOT NULL,
    [Exclude]                    NVARCHAR (10)    NOT NULL,
    [QHSESCampaigns]             NVARCHAR (10)    NOT NULL,
    [QHSESCampaignTopic]         NVARCHAR (MAX)   NOT NULL,
    [DimQHSESEndDateId]          INT              NOT NULL,
    [QHSESEndDate]               DATE             NULL,
    [GIRequired]                 BIT              NULL,
    [GITargetStartDate]          DATE             NULL,
    [GITargetEndDate]            DATE             NULL,
    [InactiveSince]              DATE             NOT NULL,
    [Management]                 NVARCHAR (255)   NOT NULL,
    [OrganisedType]              NVARCHAR (255)   NOT NULL,
    [Parent]                     NVARCHAR (255)   NOT NULL,
    [SupportingServiceNameTibco] NVARCHAR (255)   NOT NULL,
    [InTibco]                    BIT              NULL,
    [Active]                     BIT              NULL
);












````
# Source: `DBs/AzureSingleDB/DataStore2/Tables/OtherSite.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/OtherSite.sql`
- SHA-256 of original file: `1bcf4db8d6f7ddee0395f7380ee339f0bcca77421eb0ad54751089269724a8d6`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[OtherSite] (
    [OtherSiteId]         NVARCHAR (255)  NULL,
    [SharepointId]        INT             NULL,
    [DEME]                NVARCHAR (10)   NOT NULL,
    [ActivityLineId]      NVARCHAR (10)   NOT NULL,
    [ActivityLine]        NVARCHAR (255)  NOT NULL,
    [BusinessUnitId]      NVARCHAR (10)   NOT NULL,
    [BusinessGroupId]     NVARCHAR (10)   NOT NULL,
    [DivisionId]          NVARCHAR (10)   NOT NULL,
    [CountryId]           NVARCHAR (10)   NOT NULL,
    [BusinessUnitName]    VARCHAR (4)     NOT NULL,
    [CountryName]         NVARCHAR (255)  NOT NULL,
    [DivisionName]        VARCHAR (4)     NOT NULL,
    [OtherSiteName]       NVARCHAR (255)  NOT NULL,
    [QHSESCampaigns]      NVARCHAR (10)   NOT NULL,
    [QHSESCampaignTopic]  NVARCHAR (4000) NULL,
    [Exclude]             NVARCHAR (4000) NULL,
    [DimQHSESStartDateId] INT             NOT NULL,
    [DimQHSESEndDateId]   INT             NOT NULL,
    [QHSESStartDate]      DATE            NULL,
    [QHSESEndDate]        DATE            NULL,
    [GIRequired]          BIT             NULL,
    [GITargetStartDate]   DATE            NULL,
    [GITargetEndDate]     DATE            NULL
);








````
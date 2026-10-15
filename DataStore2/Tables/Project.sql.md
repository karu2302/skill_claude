# Source: `DBs/AzureSingleDB/DataStore2/Tables/Project.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/Project.sql`
- SHA-256 of original file: `e602ae83b1edc8af0bafdfd0d1c4ed5d7753579086631f04784fcbac177eb80f`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[Project] (
    [ProjectId]                     NVARCHAR (255)  NOT NULL,
    [DEME]                          NVARCHAR (32)   NOT NULL,
    [ActivityLineId]                NVARCHAR (32)   NOT NULL,
    [ActivityLine]                  NVARCHAR (255)  NOT NULL,
    [BusinessUnitId]                NVARCHAR (32)   NOT NULL,
    [BusinessGroupId]               NVARCHAR (32)   NOT NULL,
    [DivisionId]                    NVARCHAR (32)   NOT NULL,
    [CountryId]                     NVARCHAR (10)   NOT NULL,
    [BusinessUnitName]              NVARCHAR (255)  NOT NULL,
    [CountryName]                   NVARCHAR (255)  NOT NULL,
    [DivisionName]                  NVARCHAR (255)  NOT NULL,
    [ProjectName]                   NVARCHAR (255)  NOT NULL,
    [ProjectId_Name]                NVARCHAR (255)  NOT NULL,
    [StartDate]                     DATE            NULL,
    [EndDate]                       DATE            NULL,
    [ProjectWithC02]                NVARCHAR (255)  NOT NULL,
    [BudgetClosed]                  NVARCHAR (255)  NOT NULL,
    [IMpactConversionProjectNumber] NVARCHAR (255)  NOT NULL,
    [QHSEStatus]                    NVARCHAR (255)  NOT NULL,
    [DimQHSEStartDateId]            INT             NOT NULL,
    [DimQHSESEndDateId]             INT             NOT NULL,
    [QHSEStartDate]                 DATE            NULL,
    [QHSESEndDate]                  DATE            NULL,
    [QHSESCampaigns]                NVARCHAR (10)   NOT NULL,
    [Exclude]                       NVARCHAR (4000) NULL,
    [QHSESCampaignTopic]            NVARCHAR (4000) NULL,
    [DEMETurnover]                  BIGINT          NULL,
    [BudgetEuro]                    NVARCHAR (255)  NOT NULL,
    [GIRequired]                    BIT             NULL,
    [GITargetStartDate]             DATE            NULL,
    [GITargetEndDate]               DATE            NULL,
    [JointVenture]                  BIT             NULL
);










````
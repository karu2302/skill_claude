# Source: `DBs/AzureSingleDB/DataStore2/Tables/Vessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore2/Tables/Vessel.sql`
- SHA-256 of original file: `34af84dcee9db05833d687692d1346fe56e9cd80ac03da876d541c051b67c826`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DataStore2].[Vessel] (
    [VesselId]              NVARCHAR (255)  NOT NULL,
    [DEME]                  NVARCHAR (10)   NOT NULL,
    [ActivityLineId]        NVARCHAR (10)   NOT NULL,
    [ActivityLine]          NVARCHAR (255)  NOT NULL,
    [BusinessUnitId]        NVARCHAR (10)   NOT NULL,
    [BusinessGroupId]       NVARCHAR (10)   NOT NULL,
    [DivisionId]            NVARCHAR (10)   NOT NULL,
    [CountryId]             VARCHAR (4)     NOT NULL,
    [BusinessUnitName]      NVARCHAR (255)  NOT NULL,
    [CountryName]           VARCHAR (4)     NOT NULL,
    [DivisionName]          VARCHAR (4)     NOT NULL,
    [VesselName]            NVARCHAR (255)  NOT NULL,
    [VesselUnitName]        NVARCHAR (255)  NOT NULL,
    [VesselType]            NVARCHAR (255)  NOT NULL,
    [ClassificationSociety] NVARCHAR (255)  NOT NULL,
    [Exclude]               NVARCHAR (4000) NULL,
    [QHSESCampaignTopic]    NVARCHAR (4000) NULL,
    [FuelType]              NVARCHAR (255)  NOT NULL,
    [GT]                    NVARCHAR (255)  NOT NULL,
    [ISM]                   NVARCHAR (255)  NOT NULL,
    [QHSESCampaign]         NVARCHAR (5)    NULL,
    [RMPE]                  NVARCHAR (255)  NOT NULL,
    [VesselActive]          BIT             NOT NULL,
    [CharteredVessel]       BIT             NULL,
    [DimQHSESStartDateId]   INT             NOT NULL,
    [DimQHSESEndDateId]     INT             NOT NULL,
    [QHSESStartDate]        DATE            NULL,
    [QHSESEndDate]          DATE            NULL,
    [GIRequired]            BIT             NULL,
    [GITargetStartDate]     DATE            NULL,
    [GITargetEndDate]       DATE            NULL,
    [VesselLifecycleStatus] NVARCHAR (255)  NOT NULL,
    [ManagementVisitScope]  BIT             NULL,
    [CSRD]                  NVARCHAR (255)  NOT NULL,
    [VMSType]               NVARCHAR (255)  NOT NULL
);














````
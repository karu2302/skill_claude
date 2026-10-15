# Source: `DBs/AzureSingleDB/DWH/Tables/DimOtherSite.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimOtherSite.sql`
- SHA-256 of original file: `5112129e4987a433afd03aa553007ddb4ee607cd47a91dda2c51b31953b0f2cd`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimOtherSite] (
    [DimOtherSiteId]      INT             IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId]  INT             NOT NULL,
    [DimQHSESEndDateId]   INT             NOT NULL,
    [DimQHSESStartDateId] INT             NOT NULL,
    [OtherSiteId]         NVARCHAR (255)  NULL,
    [ActivityLine]        NVARCHAR (255)  NOT NULL,
    [OtherSiteName]       NVARCHAR (255)  NOT NULL,
    [QHSESCampaigns]      NVARCHAR (10)   NOT NULL,
    [Exclude]             NVARCHAR (4000) NULL,
    [QHSESCampaignTopic]  NVARCHAR (4000) NULL,
    [QHSESStartDate]      DATE            NULL,
    [QHSESEndDate]        DATE            NULL,
    [GIRequired]          BIT             NULL,
    [GITargetStartDate]   DATE            NULL,
    [GITargetEndDate]     DATE            NULL,
    [CreatedETLRunId]     INT             NOT NULL,
    [ModifiedETLRunId]    INT             NULL,
    CONSTRAINT [PK_DWH_DimOtherSite] PRIMARY KEY CLUSTERED ([DimOtherSiteId] ASC),
    CONSTRAINT [FK_DWH_DimOtherSite_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId]),
    CONSTRAINT [FK_DWH_DimOtherSite_DimQHSESEndDateId] FOREIGN KEY ([DimQHSESEndDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_DimOtherSite_DimQHSESStartDateId] FOREIGN KEY ([DimQHSESStartDateId]) REFERENCES [DWH].[DimDate] ([DimDateId])
);


GO
ALTER TABLE [DWH].[DimOtherSite] NOCHECK CONSTRAINT [FK_DWH_DimOtherSite_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimOtherSite] NOCHECK CONSTRAINT [FK_DWH_DimOtherSite_DimDEMEHierarchyId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimOtherSite]
    ON [DWH].[DimOtherSite]([OtherSiteId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'GITargetEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'GITargetStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'GIRequired';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'QHSESStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'OtherSiteName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'ActivityLine';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'OtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'DimQHSESStartDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'DimQHSESEndDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimOtherSite', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimOtherSite';


````
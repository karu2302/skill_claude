# Source: `DBs/AzureSingleDB/DWH/Tables/DimProject.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimProject.sql`
- SHA-256 of original file: `1af365cabcbb9a73d79ab6b1aae9278cfed86f892cfe3b782bc4ba5c8349b5a8`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimProject] (
    [DimProjectId]       INT             IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId] INT             NOT NULL,
    [DimQHSESEndDateId]  INT             NOT NULL,
    [DimQHSEStartDateId] INT             NOT NULL,
    [ProjectId]          NVARCHAR (255)  NOT NULL,
    [DEME]               NVARCHAR (10)   NOT NULL,
    [ActivityLineId]     NVARCHAR (10)   NOT NULL,
    [ActivityLine]       NVARCHAR (255)  NOT NULL,
    [BusinessUnitId]     NVARCHAR (10)   NOT NULL,
    [DivisionId]         NVARCHAR (10)   NOT NULL,
    [CountryId]          NVARCHAR (10)   NOT NULL,
    [BusinessGroupId]    NVARCHAR (10)   NOT NULL,
    [ProjectName]        NVARCHAR (255)  NOT NULL,
    [ProjectId_Name]     NVARCHAR (255)  NOT NULL,
    [StartDate]          DATE            NULL,
    [EndDate]            DATE            NULL,
    [ProjectWithC02]     NVARCHAR (255)  NOT NULL,
    [BudgetClosed]       NVARCHAR (255)  NOT NULL,
    [QHSEStatus]         NVARCHAR (255)  NOT NULL,
    [QHSESCampaigns]     NVARCHAR (10)   NOT NULL,
    [Exclude]            NVARCHAR (4000) NULL,
    [QHSESCampaignTopic] NVARCHAR (4000) NULL,
    [DEMETurnover]       BIGINT          NULL,
    [BudgetEuro]         NVARCHAR (255)  NOT NULL,
    [QHSEStartDate]      DATE            NULL,
    [QHSESEndDate]       DATE            NULL,
    [GIRequired]         BIT             NULL,
    [GITargetStartDate]  DATE            NULL,
    [GITargetEndDate]    DATE            NULL,
    [JointVenture]       BIT             NULL,
    [CreatedETLRunId]    INT             NOT NULL,
    [ModifiedETLRunId]   INT             NULL,
    CONSTRAINT [PK_DWH_DimProject] PRIMARY KEY CLUSTERED ([DimProjectId] ASC),
    CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId]),
    CONSTRAINT [FK_DWH_DimProject_DimQHSESEndDateId] FOREIGN KEY ([DimQHSESEndDateId]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_DimProject_DimQHSEStartDateId] FOREIGN KEY ([DimQHSEStartDateId]) REFERENCES [DWH].[DimDate] ([DimDateId])
);


GO
ALTER TABLE [DWH].[DimProject] NOCHECK CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimProject] NOCHECK CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimProject] NOCHECK CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimProject] NOCHECK CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimProject] NOCHECK CONSTRAINT [FK_DWH_DimProject_DimDEMEHierarchyId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimProject]
    ON [DWH].[DimProject]([ProjectId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'GITargetEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'GITargetStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'GIRequired';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'QHSEStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'BudgetEuro';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DEMETurnover';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'QHSEStatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'BudgetClosed';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ProjectWithC02';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'EndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'StartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ProjectId_Name';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ProjectName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ActivityLine';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DimQHSEStartDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DimQHSESEndDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimProject', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'JointVenture';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DivisionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'DEME';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'CountryId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'BusinessUnitId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'BusinessGroupId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimProject', @level2type = N'COLUMN', @level2name = N'ActivityLineId';


````
# Source: `DBs/AzureSingleDB/DWH/Tables/DimSupportingService.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DWH/Tables/DimSupportingService.sql`
- SHA-256 of original file: `288ff75bc38e3ac1d3d57a383d1e55cebf7272dc2f7ed4f1c304cfdd022c9c61`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [DWH].[DimSupportingService] (
    [DimSupportingServiceId]     INT              IDENTITY (1, 1) NOT NULL,
    [DimDEMEHierarchyId]         INT              NOT NULL,
    [DimQHSESEndDateId]          INT              NOT NULL,
    [TibcoIdentifier]            UNIQUEIDENTIFIER NOT NULL,
    [SupportingServiceId]        NVARCHAR (10)    NOT NULL,
    [SupportingServiceCode]      NVARCHAR (255)   NULL,
    [SupportingServiceName]      NVARCHAR (255)   NULL,
    [DEME]                       NVARCHAR (32)    NOT NULL,
    [ActivityLineId]             NVARCHAR (32)    NOT NULL,
    [BusinessGroupId]            NVARCHAR (32)    NOT NULL,
    [BusinessUnitId]             NVARCHAR (32)    NOT NULL,
    [DivisionId]                 NVARCHAR (32)    NOT NULL,
    [CountryId]                  VARCHAR (4)      NOT NULL,
    [Exclude]                    NVARCHAR (10)    NOT NULL,
    [QHSESCampaigns]             NVARCHAR (10)    NOT NULL,
    [QHSESCampaignTopic]         NVARCHAR (MAX)   NOT NULL,
    [QHSESEndDate]               DATE             NULL,
    [GIRequired]                 BIT              NULL,
    [GITargetEndDate]            DATE             NULL,
    [GITargetStartDate]          DATE             NULL,
    [InactiveSince]              DATE             NOT NULL,
    [Management]                 NVARCHAR (255)   NOT NULL,
    [OrganisedType]              NVARCHAR (255)   NOT NULL,
    [Parent]                     NVARCHAR (255)   NOT NULL,
    [SupportingServiceNameTibco] NVARCHAR (255)   NOT NULL,
    [InTibco]                    BIT              NULL,
    [Active]                     BIT              NULL,
    [CreatedETLRunId]            INT              NOT NULL,
    [ModifiedETLRunId]           INT              NULL,
    CONSTRAINT [PK_DWH_DimSupportingService] PRIMARY KEY CLUSTERED ([DimSupportingServiceId] ASC),
    CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId] FOREIGN KEY ([DimDEMEHierarchyId]) REFERENCES [DWH].[DimDEMEHierarchy] ([DimDEMEHierarchyId]),
    CONSTRAINT [FK_DWH_DimSupportingService_DimQHSESEndDateId] FOREIGN KEY ([DimQHSESEndDateId]) REFERENCES [DWH].[DimDate] ([DimDateId])
);


GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
ALTER TABLE [DWH].[DimSupportingService] NOCHECK CONSTRAINT [FK_DWH_DimSupportingService_DimDEMEHierarchyId];




GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_DimSupportingService]
    ON [DWH].[DimSupportingService]([TibcoIdentifier] ASC);










GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'QHSESCampaigns';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'Exclude';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'ActivityLineId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';




GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceId';










GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'DimQHSESEndDateId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'DimSupportingService', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'QHSESEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'QHSESCampaignTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'GITargetStartDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'GITargetEndDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'GIRequired';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'DivisionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'DimDEMEHierarchyId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'CountryId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'BusinessUnitId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'BusinessGroupId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'InactiveSince';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'SupportingServiceNameTibco';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'Parent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'OrganisedType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'Management';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'InTibco';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'DEME';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'TibcoIdentifier';






GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'DimSupportingService', @level2type = N'COLUMN', @level2name = N'Active';


````
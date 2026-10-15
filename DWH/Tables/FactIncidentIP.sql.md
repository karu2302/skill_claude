# Source: `DBs/AzureSingleDB/DWH/Tables/FactIncidentIP.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactIncidentIP.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `af8ff1cb287ed650d1d00ed73c104ceffc55a8b42fc52d464146312f16b1743a`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactIncidentIP] (
    [FactIncidentIPId]          INT            IDENTITY (1, 1) NOT NULL,
    [FactIncidentId]            INT            NOT NULL,
    [DimDateEndLT]              INT            NOT NULL,
    [DimDateEndRW]              INT            NOT NULL,
    [DimDateStartLT]            INT            NOT NULL,
    [DimDateStartRW]            INT            NOT NULL,
    [ActualDaysLT]              INT            NULL,
    [ActualDaysRW]              INT            NULL,
    [AdditionalCommentsInjury]  NVARCHAR (MAX) NOT NULL,
    [ClassificationInjury]      NVARCHAR (255) NOT NULL,
    [Company]                   NVARCHAR (513) NULL,
    [CompanyCountry]            NVARCHAR (255) NOT NULL,
    [ActivityLine]              NVARCHAR (4)   NOT NULL,
    [Function]                  NVARCHAR (255) NULL,
    [InjuredBodyPart]           NVARCHAR (255) NULL,
    [TypeOfInjury]              NVARCHAR (255) NOT NULL,
    [InjuryRate]                NVARCHAR (255) NOT NULL,
    [InternalEmployeeCode]      NVARCHAR (255) NOT NULL,
    [IPId]                      NVARCHAR (255) NULL,
    [LTITypeWorldwide]          NVARCHAR (255) NULL,
    [EmployeeId]                NVARCHAR (255) NOT NULL,
    [NameInjuredPersonExt]      NVARCHAR (511) NOT NULL,
    [NameInjuredPersonInt]      NVARCHAR (511) NOT NULL,
    [Nationality]               NVARCHAR (255) NULL,
    [RiskLevelRate]             NVARCHAR (255) NOT NULL,
    [WorldwideEquivalentScore]  INT            NULL,
    [WorldwideEquivalent]       BIT            NULL,
    [Age]                       INT            NOT NULL,
    [Seniority]                 INT            NOT NULL,
    [DateLTINotified]           DATE           NULL,
    [NotifiedBy]                NVARCHAR (255) NOT NULL,
    [HowNotified]               NVARCHAR (MAX) NOT NULL,
    [ReasonInjuryRateScore]     NVARCHAR (MAX) NOT NULL,
    [ReasonRiskLevelRateScore]  NVARCHAR (MAX) NOT NULL,
    [DaysWorkedLTI]             INT            NULL,
    [DaysWorkedRWC]             INT            NULL,
    [ProviderGroupId]           NVARCHAR (5)   NOT NULL,
    [ProviderGroupDescription]  NVARCHAR (50)  NOT NULL,
    [EmployeeCategorization]    NVARCHAR (255) NOT NULL,
    [UndertakingsSite]          BIT            NULL,
    [EmployeeCategory]          NVARCHAR (255) NOT NULL,
    [EmployeeSubcategory]       NVARCHAR (255) NOT NULL,
    [EmployeeSubcategoryLevel2] NVARCHAR (255) NOT NULL,
    [ClassificationInjuryCSRD]  NVARCHAR (255) NOT NULL,
    [OperationalManagerIP]      NVARCHAR (255) NOT NULL,
    [CreatedETLRunId]           INT            NOT NULL,
    [ModifiedETLRunId]          INT            NULL,
    CONSTRAINT [PK_DWH_FactIncidentIP] PRIMARY KEY CLUSTERED ([FactIncidentIPId] ASC),
    CONSTRAINT [FK_DWH_FactIncidentIP_DimDateEndLT] FOREIGN KEY ([DimDateEndLT]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactIncidentIP_DimDateEndRW] FOREIGN KEY ([DimDateEndRW]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactIncidentIP_DimDateStartLT] FOREIGN KEY ([DimDateStartLT]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactIncidentIP_DimDateStartRW] FOREIGN KEY ([DimDateStartRW]) REFERENCES [DWH].[DimDate] ([DimDateId])
);




GO





GO







GO





GO





GO







GO





GO





GO





GO







GO





GO





GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'Seniority';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'Age';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'WorldwideEquivalent';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'WorldwideEquivalentScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'RiskLevelRate';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'Nationality';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'NameInjuredPersonInt';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'NameInjuredPersonExt';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'LTITypeWorldwide';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'IPId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'InternalEmployeeCode';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'InjuryRate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'InjuredBodyPart';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'Function';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ActivityLine';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'Company';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ClassificationInjury';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'AdditionalCommentsInjury';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ActualDaysRW';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ActualDaysLT';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DimDateStartRW';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DimDateStartLT';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DimDateEndRW';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DimDateEndLT';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'FactIncidentId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'FactIncidentIPId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactIncidentIP', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ReasonRiskLevelRateScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ReasonInjuryRateScore';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'NotifiedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'HowNotified';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DaysWorkedRWC';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DaysWorkedLTI';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'DateLTINotified';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'CompanyCountry';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ProviderGroupId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ProviderGroupDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'TypeOfInjury';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'EmployeeId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'UndertakingsSite';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'EmployeeCategorization';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'EmployeeSubcategoryLevel2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'EmployeeSubcategory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'EmployeeCategory';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'ClassificationInjuryCSRD';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactIncidentIP', @level2type = N'COLUMN', @level2name = N'OperationalManagerIP';


``
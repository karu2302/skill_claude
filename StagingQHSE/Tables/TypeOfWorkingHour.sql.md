# Source: `DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql`
- SHA-256 of original file: `afd9296f2d4b64f6170e49d94b3040c4b66a410ee4ba3d6b5be905f0830f01af`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingQHSE].[TypeOfWorkingHour] (
    [TypeOfWorkingHour] NVARCHAR (50) NULL
);


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TypeOfWorkingHour', @level0type = N'SCHEMA', @level0name = N'StagingQHSE', @level1type = N'TABLE', @level1name = N'TypeOfWorkingHour', @level2type = N'COLUMN', @level2name = N'TypeOfWorkingHour';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'TypeOfWorkingHour', @level0type = N'SCHEMA', @level0name = N'StagingQHSE', @level1type = N'TABLE', @level1name = N'TypeOfWorkingHour';


````
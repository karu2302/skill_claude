# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql`
- SHA-256 of original file: `4636243e35bc1c4353c4d7b832d4bd08bd3c5f018c2426868d0350d215be3258`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql


CREATE VIEW [SSAS].[vwDimTypeOfWorkingHour]
AS
SELECT
TypeOfWorkingHour
FROM StagingQHSE.TypeOfWorkingHour
````
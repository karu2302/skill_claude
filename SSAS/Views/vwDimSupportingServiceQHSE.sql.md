# Source: `DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql`
- SHA-256 of original file: `837a255dfa74c016934e0c3964f0ab81eca7120175bf73a37e3dc5d329627170`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







CREATE VIEW [SSAS].[vwDimSupportingServiceQHSE] AS
SELECT
	  [DimSupportingServiceId]
	, [TibcoIdentifier]
	, [SupportingServiceId]
	, [SupportingServiceCode]
	, [SupportingServiceName]
	, [ActivityLineId]
	, [Exclude]
	, [QHSESCampaigns]
	--, DimQHSESStartDateId
	, DimQHSESEndDateId
	, InactiveSince
	, Active
FROM DWH.DimSupportingService
````
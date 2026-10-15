# Source: `DBs/AzureSingleDB/DataStore2/Views/vwSuccessStory.sql`

- Original repository path: `DBs/AzureSingleDB/DataStore2/Views/vwSuccessStory.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `d4651904fd04cded4fdb397a0a1c0f9ec264ad7eb956bdaa5bccc631e4a44079`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql



CREATE VIEW [DataStore2].[vwSuccessStory] AS
SELECT 
	  id																							AS SuccessStoryId
	, ISNULL(ProcessCustomId, '_N/A')																AS CustomSuccessStoryId
	, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessVesselCode, ''), '_N/A'))							AS VesselId
	, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessProjectCode, ''), '_N/A'))							AS ProjectId
	--, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessOfficeCode, ''), '_N/A'))							AS OfficeId
	, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessOtherSiteCode, ''), '_N/A'))						AS OtherSiteId
	--, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessEntityCode, ''), '_N/A'))							AS EntityBranchId
	, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessEntityCode, ''), '_N/A'))							AS EntityId
	, ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')										AS CharteredVesselId
	, CONVERT(NVARCHAR(10), ISNULL(NULLIF(ProcessSupportingServiceCode, ''), '_N/A'))				AS SupportingServiceCode
	, ISNULL(Sup.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')							AS SupportingServiceTibcoIdentifier
	, ISNULL(NULLIF(VesselLocationCode, ''), '_N/A')												AS VesselLocationCode
	, ISNULL(NULLIF(ProjectLocationCode, ''), '_N/A')												AS ProjectLocationCode
	, ISNULL(NULLIF(OfficeLocationCode, ''), '_N/A')												AS EntityLocationCode
	, ISNULL(NULLIF(OtherSiteLocationCode, ''), '_N/A')												AS OtherSiteLocationCode
	, ISNULL(V.VesselName, '_N/A')																	AS VesselName
	, ISNULL(P.ProjectName, '_N/A')																	AS ProjectName
	, ISNULL(E.EntityName, '_N/A')																	AS EntityName
	, ISNULL(OS2.OtherSiteName, '_N/A')																AS OtherSiteName
	, ISNULL(Sup.SupportingServiceName, '_N/A')														AS SupportingServiceName
	, D.DateKey																						AS DimDateId
	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessDate, 103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS SuccessStoryDateTime
	, ISNULL(NULLIF(processSubject, ''), '_N/A')													AS Subject -- task 30622
	, ISNULL(NULLIF([description], ''), '_N/A')														AS Description
	, ISNULL(NULLIF(FeedbackInput, ''), '_N/A')														AS Feedback
	, ISNULL(NULLIF(FeedbackRespondent, ''), '_N/A')												AS FeedbackRespondent
	, ISNULL(NULLIF(ProcessActivity, ''), '_N/A')													AS Activity
	, ISNULL(NULLIF(ProcessHRT, ''), '_N/A')														AS HRT
	, ISNULL(NULLIF(ProcessHRT2, ''), '_N/A')														AS HRT2
	, ISNULL(NULLIF(ProcessOriginator, ''), '_N/A')													AS Originator
	, ISNULL(NULLIF(ProcessSecondaryFactor, ''), '_N/A')											AS SecondaryFactor
--	, CONVERT(nvarchar(max), '_N/A')																AS Results
	, ISNULL(NULLIF(Results, ''), '_N/A')															AS Results
	, ISNULL(CONVERT(INT, TotalLikes), 0)															AS TotalLikes
	, ISNULL(CONVERT(INT, AverageScore), 0)															AS AverageScore
	, ISNULL(NULLIF(ImpactInlineButtons, ''), '_N/A')												AS FeedbackImpact
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(ImpactScore,',','.')), 0)							AS ImpactScore
	, ISNULL(NULLIF( EffortInlineButtons, ''), '_N/A')												AS FeedbackEffort
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(EffortScore,',','.')), 0)							AS EffortScore
	, ISNULL(NULLIF(ApplicabilityInlineButtons, ''), '_N/A')										AS FeedbackApplicability
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(ApplicabilityScore,',','.')), 0)					AS ApplicabilityScore
	, ISNULL(NULLIF(OriginalityInlineButtons, ''), '_N/A')											AS FeedbackOriginality
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(OriginalityScore,',','.')), 0)						AS OriginalityScore
	, ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(FinalScore,',','.')), 0)							AS FinalScore
	,(CASE
		WHEN ProcessDescription = '' OR ProcessDescription IS NULL THEN [description]
		ELSE ProcessDescription
		END)																						AS ProcessDescription
	,ISNULL([status], '_N/A')																		AS [status]
	,ISNULL(NULLIF( SS.[CompletedBy], ''), '_N/A')                                                   AS [CompletedBy]
    ,ISNULL(NULLIF(  SS.[CompletedDate], ''), '_N/A')                                                AS [CompletedDate]


--SELECT REPLACE(EffortScore,',','.'), CONVERT(FLOAT,REPLACE(EffortScore,',','.')), ISNULL(TRY_CONVERT(DECIMAL(18,2), REPLACE(EffortScore,',','.')), 0) aS effort, 
--ISNULL(CONVERT(FLOAT, REPLACE(ImpactScore,',','.')), 0) AS Impact



FROM StagingApprise.SuccessStory SS

CROSS APPLY ETL.F_GetDateKey(CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessDate, 103) AT TIME ZONE 'Central European Standard Time', '1900-01-01')), NULL, 0) D

LEFT JOIN DataStore2.Vessel V
	ON ProcessVesselCode = V.VesselId

LEFT JOIN DataStore2.Project P 
	ON ProcessProjectCode = P.ProjectId

LEFT JOIN DataStore2.Entity E 
	ON ProcessEntityCode = E.EntityId

LEFT JOIN DataStore2.OtherSite OS2
	ON ProcessOtherSiteCode = OS2.OtherSiteId

LEFT JOIN DataStore2.SupportingService AS Sup
		ON SS.ProcessSupportingServiceCode = Sup.SupportingServiceCode
``
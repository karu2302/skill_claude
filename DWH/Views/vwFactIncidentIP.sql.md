# Source: `DBs/AzureSingleDB/DWH/Views/vwFactIncidentIP.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Views/vwFactIncidentIP.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `289142154d9e13da3c995d04b4ee919a802fb5d4080ae2c2ba7d1946acaa88cb`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql















/****** Script for SelectTopNRows command from SSMS  ******/

CREATE VIEW [DWH].[vwFactIncidentIP] AS 
SELECT 
	IncidentId
    , ActualDaysLT
    , ActualDaysRW
    , AdditionalCommentsInjury
    , ClassificationInjury
    , Company
	, CompanyCountry
	, ActivityLine
    , DimDateEndLT
    , DimDateEndRW
    , DimDateStartLT
    , DimDateStartRW
    , [Function]
    , InjuredBodyPart
	,TypeOfInjury
    , InjuryRate
    , InternalEmployeeCode
    , IPId
--    , LTIAcceptedByInsuranceCompany
--    , LTIInsuranceNumber
    , LTITypeWorldwide
	, EmployeeId
    , NameInjuredPersonExt
    , NameInjuredPersonInt
    , Nationality
--    , ReasonInsuranceAcceptedRejected
    , RiskLevelRate
    , WorldwideEquivalentScore
    , WorldwideEquivalent
	, Age
	, Seniority
	, DateLTINotified
	, NotifiedBy
	, HowNotified
	, ReasonInjuryRateScore
	, ReasonRiskLevelRateScore
	, DaysWorkedLTI
	, DaysWorkedRWC
	, ProviderGroupId
	, ProviderGroupDescription
	, EmployeeCategorization
	, UndertakingsSite
	, EmployeeCategory
	, EmployeeSubcategory
	, EmployeeSubcategoryLevel2
	, ClassificationInjuryCSRD
	, OperationalManagerIP

  FROM DataStore4.IncidentIP
``
# Source: `DBs/AzureSingleDB/DataStore4/Views/vwIncidentIP.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore4/Views/vwIncidentIP.sql`
- SHA-256 of original file: `a045ab650493e613f643fc6b1f849b7bff2a22e6ad18a776c3cc317579a15400`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql







CREATE VIEW [DataStore4].[vwIncidentIP] AS 

SELECT
    --BUSINESS KEY
	  IIP.IPId                                                                  AS IPId

    --FOREIGN KEY
	, IIP.IncidentId                                                            AS IncidentId
    
    --ATTRIBUTES

	, ISNULL(IIP.AdditionalCommentsInjury, '_N/A')                              AS AdditionalCommentsInjury
	, ISNULL(IIP.ClassificationInjury, '_N/A')                                  AS ClassificationInjury
	, CASE WHEN ISNULL(IIP.ClassificationInjury, '_N/A') IN ('No treatment incident (NTI)', '_N/A', 'Commuting', 'Illness') THEN 0
		   WHEN IIP.ClassificationInjury = 'First Aid'						THEN 1
		   WHEN IIP.ClassificationInjury = 'Medical Treatment'				THEN 2
		   WHEN IIP.ClassificationInjury = 'Restricted Work'				THEN 3
		   WHEN IIP.ClassificationInjury IN ('Lost Time Incident', 'LTI')	THEN 4
		   WHEN IIP.ClassificationInjury = 'Fatality'						THEN 5
		   END																	AS ClassificationInjuryId
	, CASE 
		WHEN IIP.Company IS NOT NULL THEN IIP.Company
		WHEN EMP.PayrollCompanyName IS NOT NULL THEN CONCAT (EMP.PayrollCompanyCode, ' - ', EMP.PayrollCompanyName) 
		ELSE '_N/A'
		END																		AS Company
--	, COALESCE(IIP.Company, EMP.PayrollCompanyName, '_N/A')                     AS Company
	, ISNULL(EMP.Country, '_N/A')												AS CompanyCountry
	, ISNULL(EMP.ActivityLine, '_N/A')											AS ActivityLine
	, ISNULL(EMP.ProviderGroupId,'_N/A')										AS ProviderGroupId
	, ISNULL(EMP.ProviderGroupDescription,'_N/A')								AS ProviderGroupDescription
	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET,IIP.StartLTUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')		AS DimDateStartLT
 	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET,IIP.EndLTUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')		AS DimDateEndLT
 	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET,IIP.StartRWUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')		AS DimDateStartRW
 	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET,IIP.EndRWUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')		AS DimDateEndRW
	, COALESCE(IIP.[Function], EMP.JobDescription, '_N/A')                      AS [Function]
	, ISNULL(IIP.InjuredBodyPart, '_N/A')                                       AS InjuredBodyPart
	, ISNULL(IIP.TypeOfInjury, '_N/A')											AS TypeOfInjury
	, ISNULL(IIP.InjuryRate, '_N/A')                                            AS InjuryRate
	, ISNULL(IIP.InternalEmployeeCode, '_N/A')                                  AS InternalEmployeeCode
-- 10/8/2023 Task 18621	, ISNULL(IIP.LTIAcceptedByInsuranceCompany, '_N/A')                         AS LTIAcceptedByInsuranceCompany
-- 10/8/2023 Task 18621	, ISNULL(IIP.LTIInsuranceNumber, '_N/A')                                    AS LTIInsuranceNumber
	, ISNULL(EMP.EmployeeId, '_N/A')											AS EmployeeID
	, ISNULL(IIP.LTITypeWorldwide, '_N/A')                                      AS LTITypeWorldwide
	, ISNULL(IIP.NameInjuredPersonExt, '_N/A')                                  AS NameInjuredPersonExt
	, ISNULL(IIP.NameInjuredPersonInt, '_N/A')                                  AS NameInjuredPersonInt
	, COALESCE(IIP.Nationality, EMP.NationalityCode ,'_N/A')                    AS Nationality
-- 10/8/2023 Task 18621		, ISNULL(IIP.ReasonInsuranceAcceptedRejected, '_N/A')                       AS ReasonInsuranceAcceptedRejected
	, ISNULL(IIP.RiskLevelRate, '_N/A')                                         AS RiskLevelRate
	, CAST(ISNULL(IIP.WorldwideEquivalentScore, -1) AS INT)                     AS WorldwideEquivalentScore
	, CONVERT(BIT, CASE 
                    WHEN IIP.WorldwideEquivalent = 'Yes' THEN 1 
                    ELSE 0 
                   END)                                                         AS WorldwideEquivalent
	, ISNULL(DATEDIFF(YEAR, CONVERT(datetime2,EMP.BirthDate),CONVERT(datetime2,IIC.IncidentDateTime)) 
    - CASE 
        WHEN DATEADD(YEAR,DATEDIFF(YEAR, CONVERT(datetime2,EMP.BirthDate), CONVERT(datetime2,IIC.IncidentDateTime)), CONVERT(datetime2,EMP.BirthDate)) > CONVERt(datetime2,IIC.IncidentDateTime) THEN 1
		ELSE 0 
        END, 0)                                                               AS Age
	, CASE 
        WHEN DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.IncidentDateTime)) <= 0 THEN 0
		ELSE ISNULL(DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.IncidentDateTime)) 
                        - CASE 
                            WHEN DATEADD(YEAR,DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.IncidentDateTime)), CONVERT(datetime2,EMP.Seniority)) > CONVERT(datetime2,IIC.IncidentDateTime) THEN 1
		                    ELSE 0 
                           END
                     , 0) 
      END                                                                       AS Seniority

    --FACTS
    , ETL.F_QHSEConvertInt(ISNULL(IIP.ActualDaysLT, 0))                         AS ActualDaysLT
	, ETL.F_QHSEConvertInt(ISNULL(IIP.ActualDaysRW, 0))                         AS ActualDaysRW
		
	, CONVERT(DATE, ISNULL(CONVERT(DATETIMEOFFSET, IIP.DateLTINotified,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))	AS DateLTINotified
	, ISNULL(IIP.NotifiedBy, '_N/A')											AS NotifiedBy
	, ISNULL(IIP.HowNotified, '_N/A')											AS HowNotified
	, ISNULL(IIP.ReasonInjuryRateScore, '_N/A')									AS ReasonInjuryRateScore
	, ISNULL(IIP.ReasonRiskLevelRateScore, '_N/A')								AS ReasonRiskLevelRateScore
	, CAST(ISNULL(IIP.DaysWorkedLTI, 0) AS INT) 								AS DaysWorkedLTI
	, CAST(ISNULL(IIP.DaysWorkedRWC, 0) AS INT)									AS DaysWorkedRWC
	,  CASE WHEN IIP.NameInjuredPersonInt IS NULL THEN ISNULL(C.Category, '_N/A')
		   ELSE ISNULL(CSRD.CSRD, '_N/A') END									AS EmployeeCategorization --35068
	, CAST(CASE WHEN IIP.[UndertakingsSite] = 'Yes' THEN 1 ELSE 0 END AS BIT)	AS UndertakingsSite
	, CASE WHEN IIP.NameInjuredPersonInt IS NULL THEN ISNULL(C.Category, '_N/A')
		   ELSE '_N/A' END														AS EmployeeCategory
	, CASE WHEN IIP.NameInjuredPersonInt IS NULL THEN ISNULL(C.Subcategory, '_N/A')	
	       ELSE '_N/A' END														AS EmployeeSubcategory
	, CASE WHEN IIP.NameInjuredPersonInt IS NULL THEN ISNULL(C.SubcategoryLevel2, '_N/A')	
	       ELSE '_N/A' END														AS EmployeeSubcategoryLevel2
	, ISNULL(IIP.ClassificationInjuryCSRD, '_N/A')								AS ClassificationInjuryCSRD
	, ISNULL(IIP.OperationalManagerIP, '_N/A')									AS OperationalManagerIP


  FROM StagingApprise.IncidentIP IIP

	LEFT JOIN ( -- match injured person on emailaddress or name, because not all records have the emailaddress
			SELECT DISTINCT IIP.IPId 
				 , COALESCE(EMP2.FullName, EMP1.FullName) AS FullName
				 , COALESCE(EMP2.EmployeeId, EMP1.EmployeeId) AS EmployeeId
				 , COALESCE(EMP2.NationalityCode, EMP1.NationalityCode) AS NationalityCode
				 , COALESCE(EMP2.JobDescription, EMP1.JobDescription) AS JobDescription
				 , COALESCE(EMP2.PayrollCompanyName, EMP1.PayrollCompanyName) AS PayrollCompanyName
				 , COALESCE(EMP2.PayrollCompanyCode, EMP1.PayrollCompanyCode) AS PayrollCompanyCode
				 , COALESCE(EMP2.Country, EMP1.Country, '_N/A')				  AS Country
				 , COALESCE(EMP2.BirthDate, EMP1.BirthDate) AS BirthDate
				 , COALESCE(EMP2.Seniority, EMP1.Seniority) AS Seniority
				 , COALESCE(EMP2.ProviderGroupId, EMP1.ProviderGroupId) AS ProviderGroupId
				 , COALESCE(EMP2.ProviderGroupDescription, EMP1.ProviderGroupDescription) AS ProviderGroupDescription
				 , ISNULL(NULLIF(COALESCE(
					CASE 
						WHEN EMP1.DEME_ORGANIZATIONUNIT4 like 'C_DEME%' 
						THEN SUBSTRING(EMP1.DEME_ORGANIZATIONUNIT4, 3, 4)
						ELSE SUBSTRING(EMP1.DEME_ORGANIZATIONUNIT4, 3, 3)
					END,
					CASE 
						WHEN EMP2.DEME_ORGANIZATIONUNIT4 like 'C_DEME%' 
						THEN SUBSTRING(EMP2.DEME_ORGANIZATIONUNIT4, 3, 4)
						ELSE SUBSTRING(EMP2.DEME_ORGANIZATIONUNIT4, 3, 3)
					END), ''), '_N/A')													AS ActivityLine
			FROM StagingApprise.IncidentIP AS IIP
			--LEFT JOIN StagingDataMarket.Employee AS EMP1
			--	ON EMP1.FullName = IIP.NameInjuredPersonInt
			LEFT JOIN StagingDataMarket.EmployeeAll AS EMP1
				ON EMP1.FullName = IIP.NameInjuredPersonInt
			LEFT JOIN StagingDataMarket.EmployeeAll AS EMP2
				ON EMP2.BusinessEmail = IIP.NameInjuredPersonIntEmail
			WHERE IIP.NameInjuredPersonInt IS NOT NULL	
				) AS EMP
		ON EMP.IPId = IIP.IPId

	LEFT JOIN DataStore3.Incident AS IIC
		ON IIC.IncidentId = IIP.IncidentId

	LEFT JOIN StagingDataMarket.EmployeeCSRDHistory CSRD
		ON EMP.EmployeeId = CSRD.EmployeeID
		AND CSRD.CSRD IS NOT NULL
		AND IIC.IncidentDateTime >= CSRD.StartDate
		AND IIC.IncidentDateTime <= ISNULL(NULLIF(CSRD.EndDate, '1900-01-01'), '9999-01-01')


	LEFT JOIN StagingGraphAPI.CSRDCategorization C
		ON IIP.CSRDCategorizationValue = C.AppriseID


UNION ALL

SELECT
    --BUSINESS KEY
	  IIC.InjuryIllnessConsequenceId                                            AS IPId
    
    --FOREIGN KEY
	, IIC.IncidentId                                                            AS IncidentId

    --ATTRIBUTES
	, '_N/A'                                                                    AS AdditionalCommentsInjury
	, ISNULL(CASE
				WHEN INC.LostTimeIncident = 1 THEN 'Lost Time Incident'
				WHEN C.ClassificationName = 'Restricted work case' THEN 'Restricted Work'
				WHEN C.ClassificationName = 'First aid Treatment' THEN 'First Aid'
                ELSE C.ClassificationName 
             END
             , '_N/A')                                                          AS ClassificationInjury
	, CASE WHEN ISNULL(C.ClassificationName , '_N/A') IN ('No treatment incident (NTI)', '_N/A', 'Commuting', 'Illness') THEN 0
		   WHEN C.ClassificationName = 'First aid Treatment'			THEN 1
		   WHEN C.ClassificationName = 'Medical Treatment'				THEN 2
		   WHEN C.ClassificationName = 'Restricted work case'			THEN 3
		   WHEN INC.LostTimeIncident = 1 OR C.ClassificationName IN ('Lost Time Incident', 'LTI')	THEN 4
		   WHEN C.ClassificationName = 'Fatality'						THEN 5
		   END																	AS ClassificationInjuryId
	, CASE 
		WHEN IREG.IPCompany_x IS NOT NULL THEN IREG.IPCompany_x
		WHEN EMP.PayrollCompanyName IS NOT NULL THEN CONCAT (EMP.PayrollCompanyCode, ' - ', EMP.PayrollCompanyName) 
		ELSE '_N/A'
		END																		AS Company
--	, COALESCE(IREG.IPCompany_x, EMP.PayrollCompanyName,'_N/A')                 AS Company
	, ISNULL(EMP.Country, '_N/A')												AS CompanyCountry
	, ISNULL(EMP.ActivityLine, '_N/A')											AS ActivityLine
	, ISNULL(EMP.ProviderGroupId, '_N/A')										AS ProviderGroupId
	, ISNULL(EMP.ProviderGroupDescription, '_N/A')								AS ProviderGroupDescription
	
      --Date Attributes

   	, ETL.F_QHSEConvertInt(FORMAT(CASE WHEN IIC.ActualDays <> 0 THEN DATEADD(DAY, 1,  ISNULL(IIC.DateIncident, '01/01/1900')) ELSE '01/01/1900' END  , 'yyyyMMdd')) AS DimDateStartLT
    , ETL.F_QHSEConvertInt(FORMAT(CASE WHEN IIC.ActualDays <> 0 THEN DATEADD(DAY, CONVERT(INT,IIC.ActualDays),  ISNULL(IIC.DateIncident, '01/01/1900'))  ELSE '01/01/1900' END , 'yyyyMMdd')) AS DimDateEndLT
	, 19000101																	AS DimDateStartRW
	, 19000101																	AS DimDateEndRW
	


      --Other Attributes
	, ISNULL(EMP.JobDescription,'_N/A')                                         AS [Function]
	, COALESCE(IREG.InjuryLocation,
				CASE
	                WHEN IIB.BodypartName LIKE 'Arm%'       THEN 'Arm'
					WHEN IIB.BodypartName LIKE 'Chest%'     THEN 'Chest'
					WHEN IIB.BodypartName LIKE 'Eye'        THEN 'Eyes'
					WHEN IIB.BodypartName LIKE 'Feet%'      THEN 'Foot'
					WHEN IIB.BodypartName LIKE 'Hand%'      THEN 'Hand'
					WHEN IIB.BodypartName LIKE 'Head%'      THEN 'Head'
					WHEN IIB.BodypartName LIKE 'Internal%'  THEN 'Internal'
					WHEN IIB.BodypartName = 'Leg - Knee'    THEN 'Knee'
	                ELSE IIB.BodypartName 
		         END, '_N/A')                                                   AS InjuredBodyPart
	, '_N/A'																	AS TypeOfInjury
	, ISNULL(IREG.Injuryrate ,'_N/A')                                           AS InjuryRate
	, CASE 
        WHEN IIC.PersonnelType IN ('EMP', 'TEM') THEN 'DEME'
		ELSE 'External' 
      END                                                                       AS InternalEmployeeCode  
	, ISNULL(EMP.EmployeeId, '_N/A')											AS EmployeeID
--	, '_N/A'                                                                    AS LTIAcceptedByInsuranceCompany
--	, '_N/A'                                                                    AS LTIInsuranceNumber
	, CASE WHEN IREG.TypeofLTI_x IS NOT NULL THEN IREG.TypeofLTI_x
		   WHEN INC.IncidentType = 'Incident With Damage: Lost Time Incident' AND IIC.PersonnelType IN ('EMP', 'TEM') THEN 'Normal LTI'
		   ELSE '_N/A' END														AS LTITypeWorldwide
	, CASE 
        WHEN IIC.PersonnelType IN ('EMP', 'TEM') THEN '_N/A'
		ELSE ISNULL((PER.Lastname + ' ' + PER.FirstName), '_N/A') 
      END                                                                       AS NameInjuredPersonExt
	, CASE 
        WHEN IIC.PersonnelType IN ('EMP', 'TEM') THEN ISNULL((PER.Lastname + ' ' + PER.FirstName), '_N/A')
		ELSE '_N/A' 
      END                                                                       AS NameInjuredPersonInt
	, COALESCE(CO.CountryCode2, EMP.NationalityCode,'_N/A')						AS Nationality
--	, '_N/A'                                                                    AS ReasonInsuranceAcceptedRejected
	, ISNULL(IREG.Risklevelrate, '_N/A')                                        AS RiskLevelRate
	, CAST((CASE WHEN IREG.Worldwideequivalent_x0020 <> '#Name?' THEN IREG.Worldwideequivalent_x0020 ELSE -1 END) AS INT)        AS WorldwideEquivalentScore
	, CAST((CASE WHEN IREG.worldwideequivalent = 'Yes' THEN 1
				 WHEN IREG.worldwideequivalent = 'No' THEN 0
				 WHEN R.ReassignmentName = 'WW IN' THEN 1
				 ELSE 0 END) AS BIT)											AS WorldwideEquivalent
	, ISNULL(DATEDIFF(YEAR, CONVERT(datetime2,EMP.BirthDate), CONVERT(datetime2,IIC.DateIncident)) -
		CASE 
            WHEN DATEADD(YEAR,DATEDIFF(YEAR, CONVERT(datetime2,EMP.BirthDate), CONVERT(datetime2,IIC.DateIncident)), CONVERT(datetime2,EMP.BirthDate)) > CONVERT(datetime2,IIC.DateIncident) THEN 1
		    ELSE 0 
        END, 0)                                                                 AS Age
	, CASE 
        WHEN DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.DateIncident)) <= 0 THEN 0
		ELSE ISNULL(DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.DateIncident)) -
			CASE 
                WHEN DATEADD(YEAR,DATEDIFF(YEAR, CONVERT(datetime2,EMP.Seniority), CONVERT(datetime2,IIC.DateIncident)), CONVERT(datetime2,EMP.Seniority)) > CONVERT(datetime2,IIC.DateIncident) THEN 1
			    ELSE 0 
            END, 0) 
      END                                                                       AS Seniority
    --FACTS
    , ETL.F_QHSEConvertInt(ISNULL(IIC.Actualdays, 0))                           AS ActualDaysLT
	, ETL.F_QHSEConvertInt(0)                                                   AS ActualDaysRW
	, CONVERT(DATE, '01/01/1900', 105)											AS DateLTINotified
	, '_N/A'																	AS NotifiedBy
	, '_N/A'																	AS HowNotified
	, '_N/A'																	AS ReasonInjuryRateScore
	, '_N/A'																	AS ReasonRiskLevelRateScore
	, 0 																		AS DaysWorkedLTI
	, 0																			AS DaysWorkedRWC
	, '_N/A'																	AS EmployeeCategorization
	, CAST(0 AS BIT)															AS UndertakingsSite
	, '_N/A'																	AS EmployeeCategory
	, '_N/A'																	AS EmployeeSubcategory
	, '_N/A'																	AS EmployeeSubcategoryLevel2
	, '_N/A'																	AS ClassificationInjuryCSRD
	, '_N/A'																	AS OperationalManagerIP


	FROM StagingImpact.InjuryIllnessConsequence AS IIC

	LEFT JOIN StagingImpact.Classification AS C
		ON C.ClassificationId = IIC.ClassificationId

	LEFT JOIN StagingImpact.Reassignment AS R
		ON R.ReassignmentId = IIC.ReassignmentId

	LEFT JOIN StagingImpact.InjuryIllnessBodypart AS IIB
		ON IIC.InjuryIllnessConsequenceId = IIB.InjuryIllnessConsequenceId

	LEFT JOIN StagingImpact.Personnel AS PER
		ON IIC.VictimPersonnelId = PER.PersonnelId

	LEFT JOIN (
			SELECT DISTINCT 
                  EmployeeId
                , FullName
                , NationalityCode
                , JobDescription
                , PayrollCompanyName
				, PayrollCompanyCode
				, Country
                , BirthDate
                , Seniority
				, ProviderGroupId
				, ProviderGroupDescription
				, NULLIF(
					CASE 
						WHEN DEME_ORGANIZATIONUNIT4 like 'C_DEME%' 
						THEN SUBSTRING(DEME_ORGANIZATIONUNIT4, 3, 4)
						ELSE SUBSTRING(DEME_ORGANIZATIONUNIT4, 3, 3)
					END, '')											AS ActivityLine
			FROM StagingDataMarket.EmployeeAll) AS EMP
		ON EMP.EmployeeId = PER.EmployeeId

	LEFT JOIN StagingGraphAPI.IncidentRegister AS IREG
	ON IREG.IncidentId = IIC.IncidentId
	AND IREG.Source = 'Impact'	

	LEFT JOIN DataStore1.Country AS CO
	ON CO.CountryName = IREG.IPNationali0

	LEFT JOIN DataStore3.Incident AS INC
		ON INC.IncidentId = IIC.IncidentId
````
# Source: `DBs/AzureSingleDB/DataStore3/Views/vwIncident.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore3/Views/vwIncident.sql`
- SHA-256 of original file: `6ebbc863110800aae11371f793f196cf49ecfa5ceceb67def86843a7e3b705b3`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql













CREATE VIEW [DataStore3].[vwIncident] AS 

SELECT
	   CustomIncidentId
      ,I.IncidentId
      ,ProjectId
      ,EntityId
      ,VesselId
      ,OtherSiteId
	  ,CharteredVesselId
      ,SupportingServiceCode
      ,ProjectLocationCode
      ,VesselLocationCode
      ,OtherSiteLocationCode
      ,EntityLocationCode
	  ,VesselName
	  ,ProjectName
	  ,EntityName
	  ,OtherSiteName
	  ,SupportingServiceName
      ,LeadActivityLineId
      ,IncidentType
      ,IncidentTitle
      ,IncidentNotificationContains4LevelPictures
      ,IncidentRelatedTo
      ,IncidentReportTitle
      ,ActionsTakenNL
      ,ExplainProposedActions
      ,ImmediateActionsTaken
      ,Min2SMARTActionsProposed
      ,ProcessOpenActions
      ,ProcessTotalActions
      ,ActivitiesBlock4PerformedIncidentTime
      ,ActivityDetails
      ,DateAccepted
      ,DateReported
      ,DimIncidentOccuredDateId
      ,IncidentDateTime
      ,IncidentAcceptedBy
      ,ProcessCloser
      ,QualityCheckPerformedBy
      ,ReportedBy
      ,ReportedByUser
      ,ResponsibleManager
      ,DetailedDescriptionLocation
      ,LocationNL
      ,Assets
      ,People
      ,Environment
      ,Quality
      ,QualityCategory
      ,Reputation
      ,[Security]
      ,DescribeDamage
      ,PotentialRiskScore
      ,PotentialRiskScore2
      ,PotentialSeverity
      ,Probability
      ,EnvironmentalAspects
      ,SpecifyOtherEnvironmental
      ,SpecifyOtherQuality
      ,SpecifyOtherSecurity
      ,ActualDEMECostsEntered
      ,TotalCost
      ,HicoDEME
      ,HicoOverall
      ,DescriptionOfInjuryInCaseOfLTI
      ,Fatality
      ,FirstAid
      ,NumberOfInjuredPerson
      ,PotentialLTI
      ,LostTimeIncident
      ,LTITypeWorldwide
      ,HIPO
      ,ReasonChangeHIPOClassification
      ,ExtraHIPOCategory
      ,SpecifyOtherHIPOCategory
      ,ReviewDamage
      ,ReviewdamageNL
      ,ReviewDescription
      ,ReviewDescriptionNL
      ,ReviewActionsTaken
      ,CausedByThirdParty
      ,InvestigationCarriedOutByMultidisciplinaryTeam
      ,InvestigationLeader
      ,InvestigationReportContainsTimeline
      ,InvestigationReportDate
      ,Investigation
      ,InvestigationReportIsSignedOffOrApprovedByLocalManagement
      ,InvestigationUploaded
      ,InvolvedPartiesOfInvestigation
      ,InvestigationHQReview
      ,ProcessDescription
      ,ProcessError
      ,ProcessSubject
      ,Status
      ,Substatus
      ,ProcessType
      ,ProcessURLID
      ,SWAUsed
      ,AdditionalInformation
      ,CommentsClassFlag
      ,CommentsFirstNotification
      ,ConstatationsNL
      ,DeclarationAvailable
      ,HighRiskTasksPerformedAtTheTimeOfIncident
      ,HighRiskTasksPerformedAtTheTimeOfIncident2
      ,HRTReasonNA
      ,CommutingRelatedIncident
      ,NonWorkRelatedIncident
      ,NumberCausedByTP
      ,ReasonforCancellingRejecting
      ,ReasonPictureLevel1NA
      ,ReasonPictureLevel2NA
      ,ReasonPictureLevel3NA
      ,ReasonPictureLevel4NA
      ,ReOpenComments
      ,ReportableToAuthorities
      ,ReportableToClassAndFlagstate
      ,ReportedOnBehalfOfDEMEEmployee
      ,ReportedOnBehalfOfThirdParty
      ,ReportInYourOwnName
      ,RestrictedWork
      ,RootCausesAnalysisHasDefinedMin2RootCauses
      ,StatusLevel1Picture
      ,StatusLevel2Picture
      ,StatusLevel3Picture
      ,StatusLevel4Picture
      ,TDfleetHQZwijndrecht
      ,TheftOf
      ,DataSource
      ,ResDep
      ,QCSelected
      ,EIncidents
      ,RedIncidents
      ,HIPORed
      ,EIncidentRed
      ,EstimatedCost
      ,ReportedInTime
      ,TypeCommutingIncident
      ,LifeSavingRules
	  ,CriticalJob
	,ProjectLifecycle
	,QualityIncidentRelatedTo
	,RelatedToSuppliedMaterialsPartsAndActivities
	,SuppliedMaterialsPartsAndActivities
	,RelatedProcessOrActivity
	,TypeOfDeviation
	  , CONVERT(BIT, CASE WHEN IncidentRelatedTo LIKE '%Quality%'
						  OR IncidentType LIKE '%Complaint%'
						  OR IncidentType LIKE '%Non-conformity QA%'
						  OR IncidentType LIKE '%Production delay%'
						  OR IncidentType LIKE '%quality%'
						  OR Quality LIKE '%Potential%'
						  OR PotentialDamage LIKE '%Quality%' THEN 1 ELSE 0 END)									AS QIncidents
	  , CASE WHEN HighRiskTasksPerformedAtTheTimeOfIncident2 = '_N/A' THEN HighRiskTasksPerformedAtTheTimeOfIncident
			 ELSE HighRiskTasksPerformedAtTheTimeOfIncident2 END													AS HRTCombinationALE
	  -- 35667
	  , ISNULL(INP.WorldWideEquivalent, 0)																			AS WorldWideEquivalent		
	  , SupportingServiceTibcoIdentifier
	  , InvestigationThirdParty
	  , InterventionTeam5555Involved
	  
FROM
(
 SELECT DISTINCT -- Apprise
	-- PK
	  ISNULL(INC.CustomProcessID, '_N/A')                                                                           AS CustomIncidentId --  IS NULL  sometimes
	, INC.IncidentId                                                                                                AS IncidentId -- PK
	
	-- POVO FK's
	, ISNULL(NULLIF(ProcessProjectcode, 'none'),  '_N/A')                                                           AS ProjectId
	--, ISNULL(NULLIF(EntityCode, 'none'), '_N/A')                                                                    AS LegalEntityId
	, ISNULL(NULLIF(EntityCode, 'none'), '_N/A')                                                                    AS EntityId
	--, ISNULL(NULLIF(ProcessOfficeCode, 'none'), '_N/A')                                                             AS OfficeId
	, ISNULL(NULLIF(ProcessVesselCode, 'none'), '_N/A')                                                             AS VesselId
	, ISNULL(NULLIF(ProcessOtherSiteCode, 'none'), '_N/A')                                                          AS OtherSiteId -- Descriptions in the Code column => will be screening errors
    , ISNULL(NULLIF(processCharteredVesselCode, ''), '_N/A')														AS CharteredVesselId
	, ISNULL(INC.SupportingServiceCode,'_N/A')                                                                          AS SupportingServiceCode
	, ISNULL(ProjectLocation	, '_N/A')							                                                AS ProjectLocationCode 
	, ISNULL(VesselLocation		, '_N/A')							                                                AS VesselLocationCode
	, ISNULL(OtherSiteLocation	, '_N/A')							                                                AS OtherSiteLocationCode
	, ISNULL(OfficeLocation, '_N/A')								                                                AS EntityLocationCode
	, ISNULL(V2.VesselName, '_N/A')																					AS VesselName
	, ISNULL(PA1.ProjectName, '_N/A')																				AS ProjectName
	, ISNULL(EB1.EntityName, '_N/A')																				AS EntityName
	, ISNULL(OtherSiteName, '_N/A')																					AS OtherSiteName
	, ISNULL(S.SupportingServiceName, '_N/A')																		AS SupportingServiceName
	-- Hierarchy FK's                           
	, ISNULL(LeadActivityLine, '_N/A')                                                                              AS LeadActivityLineId -- Hierarchy:  Vessel, Project , ...(TBA by DEME) . Forced logic in Apprise via rule
	-- Keep the staging line                            

	-- Incident Attributes                          
	, ISNULL(IncidentType  , '_N/A')                                                                                AS IncidentType
	, ISNULL(IncidentTitle , '_N/A')                                                                                AS IncidentTitle
	--, ISNULL(IncidentDescription , '_N/A')                                                                          AS IncidentDescription
	, CONVERT(BIT, CASE                             
                        WHEN IncidentNotificationContains4LevelPictures = 'Yes' THEN 1                          
                        ELSE 0                          
                   END)                                                                                             AS IncidentNotificationContains4LevelPictures
	, ISNULL(IncidentRelatedTo , '_N/A')                                                                            AS IncidentRelatedTo
	, ISNULL(IncidentReportTitle , '_N/A')                                                                          AS IncidentReportTitle 

	 --Action Attributes                            
	, ISNULL(ActionsTakenNL  , '_N/A')                                                                              AS ActionsTakenNL
	, ISNULL(Explainproposedactions , '_N/A')                                                                       AS ExplainProposedActions
	, ISNULL(ImmediateActionsTaken , '_N/A')                                                                        AS ImmediateActionsTaken
	, ISNULL(Min2SMARTActionsProposed, '_N/A')                                                                      AS Min2SMARTActionsProposed
	, ISNULL(ProcessOpenActions, '_N/A')                                                                            AS ProcessOpenActions
	, ETL.F_QHSEConvertInt(ISNULL(ProcessTotalActions, 0))                                                          AS ProcessTotalActions
	, ISNULL(ActivitiesBlock4PerformedIncidentTime , '_N/A')                                                        AS ActivitiesBlock4PerformedIncidentTime
	, ISNULL(ActivityDetails  , '_N/A')                                                                             AS ActivityDetails

	-- Date Attributes                          
 --	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, DateAcceptedUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))							AS DateAccepted
 --	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, DateReportedUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))							AS DateReported
	--, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATE,CONVERT(DATETIMEOFFSET,ProcessDateUTC,103) AT TIME ZONE 'Central European Standard Time'),'yyyyMMdd')),'19000101')		AS DimIncidentOccuredDateId
 --	, CONVERT(DATETIME, ISNULL(CONVERT(DATETIMEOFFSET, ProcessDateUTC,103) AT TIME ZONE 'Central European Standard Time', '1900-01-01'))							AS IncidentDateTime

	, CONVERT(DATETIME, ISNULL(DateAccepted, '1900-01-01'),103)														AS DateAccepted
    , CONVERT(DATETIME, ISNULL(DateReported, '1900-01-01'),103)														AS DateReported
	, ISNULL(CONVERT(INT,FORMAT(CONVERT(DATETIME,ProcessDate,103),'yyyyMMdd')),'19000101')							AS DimIncidentOccuredDateId
 	, CONVERT(DATETIME, ISNULL(ProcessDate, '1900-01-01'),103)														AS IncidentDateTime

	--Employee Attributes                           
	, ISNULL(Incidentacceptedby , '_N/A')                                                                           AS IncidentAcceptedBy
	, ISNULL(ProcessCloser , '_N/A')                                                                                AS ProcessCloser -- need employeeid instead of name: email
	, ISNULL(QualityCheckPerformedBy , '_N/A')                                                                      AS QualityCheckPerformedBy
	, ISNULL(ReportedBy , '_N/A')                                                                                   AS ReportedBy
	, ISNULL(ReportedByUser , '_N/A')                                                                               AS ReportedByUser
	, ISNULL(ResponsibleManager, '_N/A')                                                                            AS ResponsibleManager

	--Location Attributes                           

	, ISNULL(DetailedDescriptionLocation , '_N/A')                                                                  AS DetailedDescriptionLocation
	, ISNULL(LocationNL, '_N/A')																					AS LocationNL

	-- Damage Attributes                            
	, ISNULL(Assets , '_N/A')                                                                                       AS Assets
	, ISNULL(People , '_N/A')                                                                                       AS People
	, ISNULL(Environment  , '_N/A')                                                                                 AS Environment 
	, ISNULL(Quality , '_N/A')                                                                                      AS Quality
	, ISNULL(QualityCategory, '_N/A')																				AS QualityCategory
	, ISNULL(Reputation , '_N/A')                                                                                   AS Reputation
	, ISNULL(Security , '_N/A')                                                                                     AS [Security]
	, ISNULL(DescribeDamage , '_N/A')                                                                               AS DescribeDamage
	, ISNULL(PotentialRiskScore , '_N/A')                                                                           AS PotentialRiskScore
	, CONVERT(INT, ISNULL(PotentialRiskScore2 , 0))																	AS PotentialRiskScore2
	, ISNULL(PotentialSeverity , '_N/A')                                                                            AS PotentialSeverity 
	, ISNULL(Probability , 0)                                                                                       AS Probability
	, ISNULL(EnvironmentalImpact, '_N/A')																			AS EnvironmentalAspects
	, ISNULL(SpecifyOtherEnvironmental , '_N/A')                                                                    AS SpecifyOtherEnvironmental
	, ISNULL(SpecifyOtherQuality , '_N/A')                                                                          AS SpecifyOtherQuality
	, CONVERT(NVARCHAR(255), ISNULL(SpecifyOtherSecurity , '_N/A'))                                                 AS SpecifyOtherSecurity

	--Cost Attributes                       
	, CONVERT(NUMERIC(19,2), ISNULL(ActualDEMEcostsentered, 0))                                                     AS ActualDEMECostsEntered
	, CONVERT(NUMERIC(19,2), ISNULL(TotalCost, 0))                                                                  AS TotalCost
	, CASE WHEN HicoDEME IS NULL THEN '_N/A'
		   WHEN (IncidentType LIKE '%illness%'
				OR IncidentType LIKE '%non-work%'
				OR IncidentType LIKE '%commuting%') THEN 'Not Applicable'
		   ELSE HicoDEME END																						AS HicoDEME
	, ISNULL(HicoOverall, '_N/A')                                                                                   AS HicoOverall

	-- IP Attributes                            
	, ISNULL(DescriptionOfInjuryInCaseOfLTI , -1)                                                                   AS DescriptionOfInjuryInCaseOfLTI
	, CONVERT(BIT, CASE WHEN Fatality = 'Yes' THEN 1 ELSE 0 END)                                                    AS Fatality
	, CONVERT(BIT, CASE WHEN FirstAid = 'Yes' THEN 1 ELSE 0 END)                                                    AS FirstAid
	, ETL.F_QHSEConvertInt(ISNULL(NumberOfInjuredPersons  , 0))                                                     AS NumberOfInjuredPerson --link to IP table? just count of details table
	, CONVERT(BIT, CASE WHEN PotentialLTI = 'Yes' THEN 1 ELSE 0 END)                                                AS PotentialLTI	
	, CONVERT( BIT, CASE WHEN LostTimeIncident = 'Yes' THEN 1 ELSE 0 END)                                           AS LostTimeIncident 
	, ISNULL(LTI.LTITypeWorldwide, '_N/A')																			AS LTITypeWorldwide

	--HIPO Attributes                           
	, CONVERT(BIT, CASE WHEN HIPO = 'Yes' THEN 1 ELSE 0 END)							                            AS HIPO
	, ISNULL(ReasonchangeofHIPOclassification , '_N/A') 								                            AS ReasonChangeHIPOClassification
	, ISNULL(ExtraHIPOCategory , '_N/A') 												                            AS ExtraHIPOCategory
	, ISNULL(SpecifyOtherHIPOCategory , '_N/A') 										                            AS SpecifyOtherHIPOCategory

	--Review Attributes                         
	, ISNULL(ReviewDamage , '_N/A') 													                            AS ReviewDamage
	, ISNULL(ReviewdamageNL , '_N/A') 													                            AS ReviewdamageNL
	, ISNULL(ReviewDescription , '_N/A') 												                            AS ReviewDescription
	, ISNULL(ReviewDescriptionNL , '_N/A') 												                            AS ReviewDescriptionNL
	, ISNULL(ReviewActionsTaken , '_N/A') 												                            AS ReviewActionsTaken 

	-- Investigation Attributes
	, CONVERT(BIT, CASE WHEN CausedByThirdParty  = 'YES' THEN 1 ELSE 0 END) 										AS CausedByThirdParty
	, ISNULL(InvestigationCarriedOutByMultidisciplinaryTeam, '_N/A')									 			AS InvestigationCarriedOutByMultidisciplinaryTeam
	, ISNULL(InvestigationLeader , '_N/A') 																			AS InvestigationLeader
	, ISNULL(InvestigationReportContainsTimeline, '_N/A')									 						AS InvestigationReportContainsTimeline
 	, CONVERT(DATETIME, ISNULL(InvestigationReportDate, '1900-01-01'),103)											AS InvestigationReportDate
	, CONVERT(BIT, CASE WHEN InvestigationReportDate IS NULL THEN 0 ELSE 1 END) 									AS Investigation
	, ISNULL(InvestigationReportIsSignedOffOrApprovedByLocalManagement, '_N/A')										AS InvestigationReportIsSignedOffOrApprovedByLocalManagement
	, CONVERT(BIT, CASE WHEN InvestigationUploaded = 'Yes' THEN 1 ELSE 0 END ) 										AS InvestigationUploaded
	, ISNULL(InvolvedPartiesOfInvestigation, '_N/A')								 								AS InvolvedPartiesOfInvestigation
	, ISNULL(InvestigationHQReview, '_N/A')																			AS InvestigationHQReview

	--Process Attributes
	, ISNULL(ProcessDescription , '_N/A') 												                            AS ProcessDescription
	, ISNULL(ProcessError , '_N/A') 													                            AS ProcessError	
	, ISNULL(ProcessSubject , '_N/A') 													                            AS ProcessSubject
	, ISNULL(Status , '_N/A') 															                            AS Status   
	, ISNULL(ProcessSubstatus , '_N/A') 												                            AS Substatus     
	, ISNULL(ProcessType , '_N/A') 														                            AS ProcessType
	, ISNULL(ProcessUrlID   , '_N/A') 													                            AS ProcessURLID  
	, ISNULl(INC_YN_SWAUsed, '_N/A')																				AS SWAUsed

	--QHSE Attributes                           
	-- SPLIT CS Fields                          

	--Other Attributes	                            
	, ISNULL(AdditionalInformation , '_N/A') 											                            AS AdditionalInformation
	, ISNULL(CommentsClassFlag , '_N/A') 												                            AS CommentsClassFlag
	, ISNULL(CommentsFirstNotification , '_N/A') 										                            AS CommentsFirstNotification
	, ISNULL(ConstatationsNL , '_N/A') AS  ConstatationsNL                         
	, CONVERT(BIT, CASE WHEN DeclarationAvailable = 'Yes' THEN 1 ELSE 0 END) 			                            AS DeclarationAvailable 
	, ISNULL(HighRiskTasksPerformedAtTheTimeOfIncident , '_N/A') 						                            AS HighRiskTasksPerformedAtTheTimeOfIncident
	, ISNULL(HighRiskTasksPerformedAtTheTimeOfIncident2 , '_N/A') 						                            AS HighRiskTasksPerformedAtTheTimeOfIncident2
	, ISNULL(HRTReasonNA , '_N/A') 														                            AS HRTReasonNA   
-- 10/8/2023 Task 18397: split commutingorothernonworkrelatedincident into 2 fields
	, CONVERT(BIT, CASE
					WHEN commutingorothernonworkrelatedincident = 'Yes' THEN 1
					ELSE 0
				   END) 																                            AS CommutingRelatedIncident
	, CONVERT(BIT, CASE
					WHEN NonWorkRelated = 'Yes' THEN 1
					ELSE 0
				   END) 																                            AS NonWorkRelatedIncident	
	, ISNULL(NumberCausedByTP , '0') 													                            AS NumberCausedByTP
	, ISNULL(Reasonforcancellingrejecting , '_N/A') 									                            AS ReasonforCancellingRejecting
	, ISNULL(ReasonPictureLevel1NA , '_N/A') 											                            AS ReasonPictureLevel1NA
	, ISNULL(ReasonPictureLevel2NA , '_N/A') 											                            AS ReasonPictureLevel2NA
	, ISNULL(ReasonPictureLevel3NA , '_N/A') 											                            AS ReasonPictureLevel3NA
	, ISNULL(ReasonPictureLevel4NA , '_N/A') 											                            AS ReasonPictureLevel4NA
	, ISNULL(ReOpenComments , '_N/A') 													                            AS ReOpenComments
	, CONVERT(BIT, CASE WHEN ReportableToAuthorities = 'Yes' THEN 1 ELSE 0 END) 		                            AS ReportableToAuthorities
	, CONVERT(BIT, CASE WHEN ReportableToClassAndFlagstate = 'Yes' THEN 1 ELSE 0 END ) 	                            AS ReportableToClassAndFlagstate
	, ISNULL(ReportedOnBehalfOfDEMEEmployee , '_N/A') 									                            AS ReportedOnBehalfOfDEMEEmployee
	, CONVERT(BIT, CASE WHEN ReportedOnBehalfOfThirdParty = 'Yes' THEN 1 ELSE 0 END) 	                            AS ReportedOnBehalfOfThirdParty
	, CONVERT(BIT, CASE WHEN ReportInYourOwnName = 'Yes' THEN 1 ELSE 0 END)  			                            AS ReportInYourOwnName	
	, CONVERT(BIT, CASE WHEN RestrictedWork  = 'Yes' THEN 1 ELSE 0 END) 				                            AS RestrictedWork 	
	, ISNULL(RootCausesAnalysisHasDefinedMin2RootCauses, '_N/A')						                            AS RootCausesAnalysisHasDefinedMin2RootCauses
	, CASE WHEN StatusLevel1Picture = 'NOK' THEN 'No'
		   WHEN StatusLevel1Picture = 'OK' THEN 'Yes'
		   ELSE ISNULL(StatusLevel1Picture , '_N/A') END															AS StatusLevel1Picture
	, CASE WHEN StatusLevel2Picture = 'NOK' THEN 'No'
		   WHEN StatusLevel2Picture = 'OK' THEN 'Yes'
		   ELSE ISNULL(StatusLevel2Picture , '_N/A') END															AS StatusLevel2Picture
	, CASE WHEN StatusLevel3Picture = 'NOK' THEN 'No'
		   WHEN StatusLevel3Picture = 'OK' THEN 'Yes'
		   ELSE ISNULL(StatusLevel3Picture , '_N/A') END															AS StatusLevel3Picture
	, CASE WHEN StatusLevel4Picture = 'NOK' THEN 'No'
		   WHEN StatusLevel4Picture = 'OK' THEN 'Yes'
		   ELSE ISNULL(StatusLevel4Picture , '_N/A') END															AS StatusLevel4Picture
	, ISNULL(TDfleetHQZwijndrecht , '_N/A') 											                            AS TDfleetHQZwijndrecht
	, ISNULL(TheftOf , '_N/A') 															                            AS TheftOf
	, 'Apprise' 																		                            AS DataSource
	, '_N/A'																										AS ResDep
	, CONVERT(BIT, 0)																								AS QCSelected
--	, CONVERT(BIT, CASE WHEN Environment = 'Damage'
--						  OR Environment= 'Potential'
--						  OR IncidentType = 'Incident with damage: Environmental Damage'
--						  OR IDC.PotentialDamage = 'Environment' THEN 1 ELSE 0 END)									AS EIncidents
	, CONVERT(BIT, CASE WHEN IncidentRelatedTo LIKE '%Environment%'
						  OR IDC.PotentialDamage = 'Environment' THEN 1 ELSE 0 END)									AS EIncidents
	, CONVERT(BIT, CASE WHEN CONVERT(INT, ISNULL(PotentialRiskScore2, 0))>15
						  OR INC.HicoDEME LIKE 'HICO Cat 4 %'
						  OR INC.HicoDEME LIKE 'HICO Cat 5 %'
						  OR INC.HicoDEME LIKE 'HICO Cat 6 %'
						  OR IIP.WorldwideEquivalent = 'Yes' THEN 1 ELSE 0 END)										AS RedIncidents
	, CASE WHEN CONVERT(INT, ISNULL(PotentialRiskScore2, 0))>15 AND HIPO = 'Yes' THEN 'HIPO Red'
		   WHEN HIPO = 'Yes' THEN 'HIPO' ELSE 'No' END																AS HIPORed
--	, CASE WHEN ISNULL(IncidentRelatedTo, '_N/A') NOT LIKE '%Environment%'
--				AND ISNULL( IDC.PotentialDamage, '_N/A') <> 'Environment' THEN 'No'
--		   WHEN IDC.HIPOCalc >= 16 AND (INC.HicoDEME LIKE 'HICO Cat 4 %'
--									 OR INC.HicoDEME LIKE 'HICO Cat 5 %'
--									 OR INC.HicoDEME LIKE 'HICO Cat 6 %') THEN 'E-HIPO-RedHICO'
--		   WHEN IDC.HIPOCalc >= 12 AND (INC.HicoDEME LIKE 'HICO Cat 3 %' 
--									 OR	INC.HicoDEME LIKE 'HICO Cat 4 %'
--									 OR INC.HicoDEME LIKE 'HICO Cat 5 %'
--									 OR INC.HicoDEME LIKE 'HICO Cat 6 %') THEN 'E-HIPO-HICO'
--		   ELSE 'E-Incident' END																					AS EIncidentRed
-- Change 12/1/22 (Injin):
	, CASE WHEN ISNULL(IncidentRelatedTo, '_N/A') NOT LIKE '%Environment%'
				AND ISNULL( IDC.PotentialDamage, '_N/A') <> 'Environment' THEN 'No'
		   WHEN IDC.HIPOCalc >= 16 AND (INC.HicoDEME LIKE 'HICO Cat 4 %'
									 OR INC.HicoDEME LIKE 'HICO Cat 5 %'
									 OR INC.HicoDEME LIKE 'HICO Cat 6 %') THEN 'E-HIPO-RedHICO'
		   WHEN IDC.HIPOCalc >= 12  THEN 'E-HIPO-HICO'
		   ELSE 'E-Incident' END																					AS EIncidentRed
	, CONVERT(INT, CASE WHEN INC.IncidentType LIKE '%illness%'
						OR INC.IncidentType LIKE '%non-work%'
						OR INC.IncidentType LIKE '%commuting%' THEN 0
						WHEN INC.HicoDEME LIKE 'HICO Cat 1 %' THEN 500
						WHEN INC.HicoDEME LIKE 'HICO Cat 2 %' THEN 4500
						WHEN INC.HicoDEME LIKE 'HICO Cat 3 %' THEN 45000
						WHEN INC.HicoDEME LIKE 'HICO Cat 4 %' THEN 200000
						WHEN INC.HicoDEME LIKE 'HICO Cat 5 %' THEN 2000000
						WHEN INC.HicoDEME LIKE 'HICO Cat 6 %' THEN 10000000
						ELSE 0 END)																					AS EstimatedCost
	,  CASE 
			WHEN DATEDIFF(
							HOUR, 
							CONVERT(DATETIME, ISNULL(ProcessDate, '1900-01-01'),103), 
							CONVERT(DATETIME, ISNULL(DateReported, '1900-01-01'),103)
							) <= 24 THEN 1 
			ELSE 0 
		END																											AS ReportedInTime
	, ISNULL(INC.TypeCommutingIncident, '_N/A')																		AS TypeCommutingIncident
	, ISNULL(INC.LifeSavingRules, '_N/A')																			AS LifeSavingRules
	, IDC.PotentialDamage																							AS PotentialDamage
	, ISNULL(S.TibcoIdentifier, '00000000-0000-0000-0000-000000000000')												AS SupportingServiceTibcoIdentifier
	, CAST(CASE WHEN INC.INC_YN_InvestigationThirdParties = 'Yes' THEN 1 ELSE 0 END AS BIT)							AS InvestigationThirdParty
	, CAST(CASE WHEN INC.Involvement5555 = 'Yes' THEN 1 ELSE 0 END AS BIT)											AS InterventionTeam5555Involved 
	, ISNULL(CriticalJob,'_N/A')																					AS CriticalJob
	, ISNULL(t4.Title,'_N/A')																						AS ProjectLifecycle
	, ISNULL(t1.Title,'_N/A')																						AS QualityIncidentRelatedTo
	, ISNULL(RelatedToSuppliedMaterialsPartsAndActivities, '_N/A')													AS RelatedToSuppliedMaterialsPartsAndActivities
	, ISNULL(t2.Title,'_N/A')																						AS SuppliedMaterialsPartsAndActivities
	, ISNULL(t3.Title,'_N/A')																						AS RelatedProcessOrActivity
	, ISNULL(t5.Title,'_N/A')																						AS TypeOfDeviation

	FROM StagingApprise.Incident AS INC

	LEFT JOIN (SELECT DISTINCT IncidentId
							, PotentialDamage
							, ETL.F_QHSEConvertInt(ISNULL(SafetyProbability, 0)) * ETL.F_QHSEConvertInt(ISNULL(Severity, 0)) AS HIPOCalc
				FROM StagingApprise.IncidentDamageClassification
				WHERE PotentialDamage = 'Environment') AS IDC
		ON IDC.IncidentId = INC.IncidentId

	LEFT JOIN (SELECT DISTINCT IncidentId, WorldwideEquivalent
				FROM StagingApprise.IncidentIP
				WHERE WorldwideEquivalent = 'Yes') AS IIP
		ON IIP.IncidentId = INC.IncidentId
	LEFT JOIN
		(
			SELECT 
				  IncidentId
				, RIGHT(MIN(LTITypeWorldwide), LEN(MIN(LTITypeWorldwide)) - 2) AS LTITypeWorldwide
			FROM (
					SELECT 
						  IncidentId,
						  CASE 
--	10/8/2023 Task 18397		WHEN LTITypeWorldwide = 'Normal LTI'						THEN '1 Normal LTI'
--								WHEN LTITypeWorldwide = 'Pending'							THEN '2 Pending'
--								WHEN LTITypeWorldwide = 'Third parties (SC, client, JV...)' THEN '3 Third parties (SC, client, JV...)'
--								WHEN LTITypeWorldwide = 'JV'								THEN '4 JV'
--								WHEN LTITypeWorldwide = 'Disapproved (No LTI)'				THEN '5 Disapproved (No LTI)'
--								ELSE '6 _N/A' 
								-- WHEN LTITypeWorldwide = 'Accepted' THEN '1 Accepted'
								WHEN LTITypeWorldwide = 'Accepted' OR LTITypeWorldwide = 'Normal LTI' THEN '1 Accepted' -- 13/08/2024 Task 31975
								WHEN LTITypeWorldwide = 'Pending' THEN '2 Pending'
								WHEN LTITypeWorldwide = 'Third parties (SC, client, JV...)' THEN '3 Third parties (SC, client, JV...)'
								WHEN LTITypeWorldwide = 'status not known' THEN '4 Status not known'
								WHEN LTITypeWorldwide = 'Disapproved' THEN '5 Disapproved'
								ELSE '6 _N/A'

						  END																AS LTITypeWorldwide

					FROM StagingApprise.IncidentIP
				) SQ
			GROUP BY IncidentId
		) LTI
		ON INC.IncidentId = LTI.IncidentId

	LEFT JOIN DataStore2.OtherSite OS1
		ON NULLIF(INC.ProcessOtherSiteCode, 'none') = OS1.OtherSiteId

	LEFT JOIN DataStore2.Entity EB1
		ON NULLIF(EntityCode, 'none') = EB1.EntityId

	LEFT JOIN DataStore2.Project AS PA1
		ON NULLIF(ProcessProjectcode, 'none') = PA1.ProjectId

	LEFT JOIN DataStore2.Vessel V2
		ON NULLIF(ProcessVesselCode, 'none') = V2.VesselId

	LEFT JOIN DataStore2.SupportingService S
		ON INC.SupportingServiceCode = S.SupportingServiceCode

	LEFT JOIN (select GUID,title from StagingGraphAPI.Topics) t1
		ON INC.QualityIncidentRelatedTo = t1.GUID

	LEFT JOIN (select GUID,title from StagingGraphAPI.Topics) t2
		ON INC.SuppliedMaterialsPartsAndActivities = t2.GUID

	LEFT JOIN (select GUID,title from StagingGraphAPI.Topics) t3
		ON INC.RelatedProcessOrActivity = t3.GUID

	LEFT JOIN (select GUID,title from StagingGraphAPI.Topics) t4
		ON INC.ProjectLifecycle = t4.GUID

	LEFT JOIN (select GUID,title from StagingGraphAPI.Topics) t5
		ON INC.TypeOfDeviation = t5.GUID

UNION ALL

SELECT DISTINCT -- Impact
    --BUSINESS KEYS
	  INC.IncidentId                                                                                                AS CustomIncidentId
	, INC.IncidentId                                                                                                AS IncidentId
	
    --FOREIGN KEYS
	, COALESCE(PA1.ProjectId, INC.Project,  '_N/A')                                                                 AS ProjectId
	--, CASE WHEN O1.OfficeId IS NOT NULL THEN ISNULL(EB1.EntityBranchId, '_N/A') ELSE '_N/A' END                     AS LegalEntityId
	, CASE 
		WHEN COALESCE(PA1.ProjectId, INC.Project, NULLIF(ICD.VesselID, 'Not Available'),OS1.OtherSiteId) IS NULL 
		THEN ISNULL(EB1.EntityId, '_N/A' )	
		ELSE '_N/A'
	  END																								AS EntityId
	--, COALESCE(O1.OfficeId, '_N/A')																					AS OfficeId
	, COALESCE(NULLIF(ICD.VesselID, 'Not Available'), '_N/A')                                                       AS VesselId 
	, ISNULL(OS1.OtherSiteId, '_N/A')                                                                               AS OtherSiteId
	, '_N/A'																										AS CharteredVesselId
    , '_N/A'                                                                                                        AS SupportingServiceCode
	, '_N/A'                                                                                                        AS ProjectLocationCode
	, '_N/A'                                                                                                        AS VesselLocationCode
	, '_N/A'                                                                                                        AS OtherSiteLocationCode
	, '_N/A'                                                                                                        AS EntityLocationCode
	, ISNULL(V2.VesselName, '_N/A')																					AS VesselName
	, ISNULL(PA1.ProjectName, '_N/A')																				AS ProjectName
	, ISNULL(EB1.EntityName, '_N/A')																				AS EntityName
	, ISNULL(OtherSiteName, '_N/A')																					AS OtherSiteName
	, '_N/A'																										AS SupportingServiceName
	,  COALESCE(AL.ActivityLineId, /* DSO.ActivityLineId*/  V2.ActivityLineId, PA1.ActivityLineId, '_N/A' )         AS LeadActivityLineId --  fill with Activity Line of the POVO

	, COALESCE(IREG.Typeofincident
               , CASE WHEN IIC.Injuryillnessclass = 'Illness' THEN 'Non-work related incident: Illness'
                     WHEN SEVT.SeverityTypeName = 'Commuting' THEN 'Non-work related incident: Commuting Accident'
                     WHEN SEVT.SeverityTypeName = 'Non-work related' THEN CONCAT('Non-work related incident: ', C.ClassificationName)
					 WHEN SEVT.SeverityTypeName = 'Work related' THEN CONCAT(IT.IncidentTypeName,': ', C.ClassificationName)
                     ELSE '_N/A' END 
			   , '_N/A')                                                                                            AS IncidentType
	, ISNULL(IREG.Incidenttitle, '_N/A')                                                                            AS IncidentTitle
	--, ISNULL(IREG.Description, '_N/A')                                                                              AS IncidentDescription
	, 0                                                                                                             AS IncidentNotificationContains4LevelPictures
	, '_N/A'                                                                                                        AS IncidentRelatedTo
	, '_N/A'                                                                                                        AS IncidentReportTitle
	, ISNULL(IREG.ActionsTakenNL, '_N/A')                                                                           AS ActionsTakenNL
	, '_N/A'                                                                                                        AS ExplainProposedActions
	, ISNULL(IREG.Actionstaken_x0028, '_N/A')                                                                       AS ImmediateActionsTaken
	, ISNULL(IREG.QCMin_x002e, '_N/A')									                                            AS Min2SMARTActionsProposed
	, '_N/A'                                                                                                        AS ProcessOpenActions
	, CONVERT(INT,0)			                                                                                    AS ProcessTotalActions
	, ISNULL(IREG.HIPOActivit,'_N/A')                                                                               AS ActivitiesBlock4PerformedIncidentTime
	, '_N/A'                                                                                                        AS ActivityDetails
	, CONVERT(DATETIME, '01/01/1900', 105)                                                                          AS DateAccepted
	, CONVERT(DATETIME, ISNULL(INC.DateReported, '01/01/1900'))                                                     AS DateReported
	, FORMAT(CONVERT(DATETIME, ISNULL(INC.DateIncident, '01/01/1900')),'yyyyMMdd')                                  AS DateIncidentOccured
	, CONVERT(DATETIME, ISNULL(INC.DateIncident , '01/01/1900') )                                                   AS EventDateTime 
	, '_N/A'                                                                                                        AS IncidentAcceptedBy
	, '_N/A'                                                                                                        AS ProcessCloser
	, ISNULL(IREG.Qualitycheckperfor, '_N/A')                                                                       AS QualityCheckPerformedBy
	, '_N/A'                                                                                                        AS ReportedBy
	, '_N/A'                                                                                                        AS ReportedByUser
	, ISNULL(ResponsibleManager, '_N/A')                                                                            AS ResponsibleManager
	, ISNULL(IREG.Detailedlocation, '_N/A')                                                                         AS DetailedDescriptionLocation
	, '_N/A'																										AS LocationNL
	, '_N/A'                                                                                                        AS Assets
	, '_N/A'                                                                                                        AS People
	, '_N/A'                                                                                                        AS Environment
	, '_N/A'                                                                                                        AS Quality
	, '_N/A'																										AS QualityCategory
	, '_N/A'                                                                                                        AS Reputation
	, '_N/A'                                                                                                        AS [Security]
	, ISNULL(IREG.Descriptiondamagei, '_N/A')                                                                       AS DescribeDamage
	, ISNULL(IR.RiskDescription,'_N/A')                                                                             AS PotentialRiskScore
	, CONVERT(INT, CASE WHEN IREG.Potentialriskscore = '#Name?' THEN 0 ELSE ISNULL(IREG.Potentialriskscore, 0) END)	AS PotentialRiskScore2
	, ISNULL(IREG.Severity, '_N/A')                                                                                 AS PotentialSeverity
	, ISNULL(IREG.Probability, '_N/A')                                                                              AS Probability
	, ISNULL(REPLACE(REPLACE(REPLACE(IREG.EnvironmentalAspects,'',''),'',''),'"',''), '_N/A')   					AS EnvironmentalAspects
	, '_N/A'                                                                                                        AS SpecifyOtherEnvironmental
	, '_N/A'                                                                                                        AS SpecifyOtherQuality
	, '_N/A'                                                                                                        AS SpecifyOtherSecurity
	, CONVERT(NUMERIC(19,2), ISNULL(IREG.HICODEMECost, 0))															AS ActualDEMECostsEntered  
	, CONVERT(NUMERIC(19,2), 0)																						AS TotalCost
	, CASE WHEN IREG.Typeofincident NOT LIKE '%Illness%'
			AND IREG.Typeofincident NOT LIKE '%Commuting%'
			AND IREG.Typeofincident NOT LIKE '%Non-wor%'
			AND IREG.Typeofincident IS NOT NULL
			AND IREG.HICODEME_x0 IS NOT NULL THEN IREG.HICODEME_x0
		  WHEN IREG.Typeofincident LIKE '%Illness%'
			OR IREG.Typeofincident LIKE '%Commuting%'
			OR IREG.Typeofincident LIKE '%Non-work%' THEN 'Not Applicable'
		  WHEN IREG.IncidentId IS NOT NULL THEN ISNULL(IREG.HICODEME_x0, '_N/A')
		  WHEN IIC.Injuryillnessclass = 'Illness' THEN 'Not Applicable'
		  WHEN SEVT.SeverityTypeName = 'Commuting' THEN 'Not Applicable'
		  WHEN SEVT.SeverityTypeName = 'Non-work related' THEN 'Not Applicable'
		  WHEN C.ClassificationName = 'Commuting' THEN 'Not Applicable'
		  ELSE '_N/A' END																							AS HicoDEME
	, ISNULL(IREG.HICOoverall, '_N/A')                                                                              AS HicoOverall
	, '_N/A'                                                                                                        AS DescriptionOfInjuryInCaseOfLTI
	, CONVERT(BIT, 0)                                                                                               AS Fatality
	, CONVERT(BIT, 0)                                                                                               AS FirstAid
	, ETL.F_QHSEConvertInt(0)                                                                                       AS NumberOfInjuredPerson
	, CONVERT(BIT, 0)                                                                                               AS PotentialLTI
	, CONVERT(BIT, CASE WHEN IREG.Typeofincident LIKE '%Lost Time Incident' THEN 1
						WHEN IIC.Injuryillnessclass = 'Illness' THEN 0
						WHEN SEVT.SeverityTypeName = 'Commuting' THEN 0
						WHEN C.ClassificationName = 'Lost Time Incident' THEN 1
						ELSE 0 END)																					AS LostTimeIncident
	, '_N/A'																										AS LTITypeWorldwide
	, CONVERT(BIT, CASE WHEN IREG.HIPO = 'Yes' THEN 1 
						WHEN IREG.HIPO = 'No' THEN 0
						WHEN INC.HIPO = 'Yes' THEN 1
						ELSE 0 END)																					AS HIPO
	, '_N/A'                                                                                                        AS ReasonChangeHIPOClassification
	, ISNULL(IREG.HIPOExtra, '_N/A')                                                                                AS ExtraHIPOCategory
	, '_N/A'                                                                                                        AS SpecifyOtherHIPOCategory
	, '_N/A'                                                                                                        AS ReviewDamage
	, ISNULL(IREG.DamageDescNL , '_N/A')                                                                            AS ReviewDamageNL
	, '_N/A'                                                                                                        AS ReviewDescription
	, ISNULL(IREG.DescriptionNL,'_N/A')                                                                             AS ReviewDescriptionNL
	, '_N/A'                                                                                                        AS ReviewActionsTaken
	, CONVERT(BIT, 0)                                                                                               AS CausedByThirdParty
	, ISNULL(IREG.QCMultidisc, '_N/A')									                                            AS InvestigationCarriedOutByMultidisciplinaryTeam
	, '_N/A'                                                                                                        AS InvestigationLeader
	, ISNULL(IREG.QCTimeline, '_N/A')									                                            AS InvestigationReportContainsTimeline
	, CONVERT(DATETIME, '01/01/1900', 105)																			AS InvestigationReportDate
	, CONVERT(BIT, CASE WHEN INV.IncidentId IS NULL THEN 0 ELSE 1 END)												AS Investigation
	, ISNULL(IREG.QCInvestiga, '_N/A')									                                            AS InvestigationReportIsSignedOffOrApprovedByLocalManagement
	, CONVERT(BIT, 0)                                                                                               AS InvestigationUploaded
	, ISNULL(IREG.QCinvolved_, '_N/A')									                                            AS InvolvedPartiesOfInvestigation
	, '_N/A'																										AS InvestigationHQReview
	, '_N/A'                                                                                                        AS ProcessDescription
	, '_N/A'                                                                                                        AS ProcessError
	, '_N/A'                                                                                                        AS ProcessSubject
	,  ISNULL(
                CASE WHEN ST.StatusName = 'Draft' THEN 'Pending Acceptance'
                     WHEN ST.StatusName in ('Open', 'QHSE-S Review', 'In progress') THEN  'Pending'
                     ELSE ST.StatusName 
                END
             , '_N/A')                                                                                              AS Status
	, '_N/A'                                                                                                        AS Substatus
	,  ISNULL(
                CASE WHEN IT.IncidentTypeName = 'Near miss / Dangerous situation' THEN 'Near-miss'
					 WHEN IT.IncidentTypeName =  'Incident With Damage' THEN 'Incident with damage'
                     ELSE IT.IncidentTypeName 
                END
             , '_N/A')                                                                                              AS ProcessType
	, INC.IncidentId                                                                                                AS ProcessURLID
	, '_N/A'																										AS SWAUsed
	, ISNULL(IREG.[Remarks/additional_], '_N/A')																	AS AdditionalInformation
	, '_N/A'                                                                                                        AS CommentsClassFlag
	, '_N/A'                                                                                                        AS CommentsFirstNotification
	, '_N/A'                                                                                                        AS ConstatationsNL
	, CONVERT(BIT, 0)                                                                                               AS DeclarationAvailable
	, ISNULL(IREG.HIPOActivit0, '_N/A')                                                                             AS HighRiskTasksPerformedAtTheTimeOfIncident
	, ISNULL(IREG.HIPOActivit1, '_N/A')                                                                             AS HighRiskTasksPerformedAtTheTimeOfIncident2
	, '_N/A'                                                                                                        AS HRTReasonNA
	, CONVERT(BIT, 0)                                                                                               AS CommutingRelatedIncident
	, CONVERT(BIT, 0)                                                                                               AS NonWorkRelatedIncident
	, '_N/A'                                                                                                        AS NumberCausedByTP
	, '_N/A'                                                                                                        AS ReasonforCancellingRejecting
	, '_N/A'                                                                                                        AS ReasonPictureLevel1NA
	, '_N/A'                                                                                                        AS ReasonPictureLevel2NA
	, '_N/A'                                                                                                        AS ReasonPictureLevel3NA
	, '_N/A'                                                                                                        AS ReasonPictureLevel4NA
	, '_N/A'                                                                                                        AS ReOpenComments
	, 0                                                                                                             AS ReportableToAuthorities
	, 0                                                                                                             AS ReportableToClassAndFlagstate
	, '_N/A'                                                                                                        AS ReportedOnBehalfOfDEMEEmployee
	, CONVERT(BIT, 0)                                                                                               AS ReportedOnBehalfOfThirdParty
	, 0                                                                                                             AS ReportInYourOwnName
	, 0                                                                                                             AS RestrictedWork
	, ISNULL(IREG.QCMin_x002e0, '_N/A')									                                            AS RootCausesAnalysisHasDefinedMin2RootCauses
	, ISNULL(IREG.Picturelevel1, '_N/A')                                                                            AS StatusLevel1Picture
	, ISNULL(IREG.Picturelevel2, '_N/A')                                                                            AS StatusLevel2Picture
	, ISNULL(IREG.Picturelevel3, '_N/A')                                                                            AS StatusLevel3Picture
	, ISNULL(IREG.Picturelevel4, '_N/A')                                                                            AS StatusLevel4Picture
	, ISNULL(IREG.TD, '_N/A')																						AS TDfleetHQZwijndrecht
	, '_N/A'                                                                                                        AS TheftOf
	, 'Impact'                                                                                                      AS DataSource
	, ISNULL(ICD.ImpactDepartmentName, '_N/A' )																		AS ResDep
	, CONVERT(BIT, CASE WHEN IREG.QCSelected = 'True' THEN 1 ELSE 0 END)											AS QCSelected
	, CONVERT(BIT, CASE WHEN IREG.Eincident = 'Yes' THEN 1 ELSE 0 END)												AS EIncidents
	, CONVERT(BIT, CASE WHEN IREG.REDIncident = 'Yes' THEN 1 ELSE 0 END)											AS RedIncidents
	, CASE WHEN CONVERT(INT, CASE WHEN IREG.Potentialriskscore = '#Name?' THEN 0 ELSE ISNULL(IREG.Potentialriskscore, 0) END)>15 AND IREG.HIPO = 'Yes' THEN 'HIPO Red'
		   WHEN IREG.HIPO = 'No' THEN 'No'
		   WHEN CONVERT(INT, CASE WHEN IREG.Potentialriskscore = '#Name?' THEN 0 ELSE ISNULL(IREG.Potentialriskscore, 0) END)>15 AND INC.HIPO = 'Yes' THEN 'HIPO Red'
		   WHEN IREG.HIPO = 'Yes' THEN 'HIPO'
		   WHEN INC.HIPO = 'Yes' THEN 'HIPO'
		   ELSE 'No' END																							AS HIPORed
	, CASE WHEN ISNULL(IREG.Eincident, '_N/A') <> 'Yes' THEN 'No'
		   WHEN COALESCE(IREG.HIPO, INC.HIPO, '_N/A') = 'Yes' AND IREG.Eincident = 'Yes'
				AND IREG.Typeofincident NOT LIKE '%Illness%'
				AND IREG.Typeofincident NOT LIKE '%Commuting%'
				AND IREG.Typeofincident NOT LIKE '%Non-wor%'
				AND IREG.Typeofincident IS NOT NULL
				AND (IREG.HICODEME_x0 LIKE 'HICO Cat 4 %'
					OR IREG.HICODEME_x0 LIKE 'HICO Cat 5 %'
					OR IREG.HICODEME_x0 LIKE 'HICO Cat 6 %') THEN 'E-HIPO-RedHICO'
			WHEN COALESCE(IREG.HIPO, INC.HIPO, '_N/A') = 'Yes' AND IREG.Eincident = 'Yes'
				AND IREG.Typeofincident NOT LIKE '%Illness%'
				AND IREG.Typeofincident NOT LIKE '%Commuting%'
				AND IREG.Typeofincident NOT LIKE '%Non-wor%'
				AND IREG.Typeofincident IS NOT NULL
				AND IREG.HICODEME_x0 LIKE 'HICO Cat 3 %' THEN 'E-HIPO-HICO'
			WHEN IREG.Eincident = 'Yes' THEN 'E-Incident'
			ELSE 'No' END																							AS EIncidentRed

	, CONVERT(INT, CASE WHEN IREG.Typeofincident LIKE '%Illness%'
							OR IREG.Typeofincident LIKE '%Commuting%'
							OR IREG.Typeofincident LIKE '%Non-work%' THEN 0
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 1 %' THEN 500
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 2 %' THEN 4500
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 3 %' THEN 45000
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 4 %' THEN 200000
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 5 %' THEN 2000000
						WHEN IREG.HICODEME_x0 LIKE 'HICO Cat 6 %' THEN 10000000
						ELSE 0 END)																					AS EstimatedCost
	, CONVERT(BIT, CASE WHEN DATEDIFF(HOUR, INC.DateIncident, INC.DateReported) <= 24 THEN 1 ELSE 0 END)			AS ReportedInTime
	, '_N/A'																										AS TypeCommutingIncident
	, '_N/A'																										AS LifeSavingRules
	, '_N/A'																										AS PotentialDamage
	, CONVERT(UNIQUEIDENTIFIER, '00000000-0000-0000-0000-000000000000')												AS SupportingServiceTibcoIdentifier		
	, CAST(0 AS BIT)																								AS InvestigationThirdParty
	, CAST(0 AS BIT)																								AS InterventionTeam5555Involved 
	, '_N/A'																										AS CriticalJob
	, '_N/A'																										AS ProjectLifecycle
	, '_N/A'																										AS QualityIncidentRelatedTo
	, '_N/A'																										AS RelatedToSuppliedMaterialsPartsAndActivities
	, '_N/A'																										AS SuppliedMaterialsPartsAndActivities
	, '_N/A'																										AS RelatedProcessOrActivity
	, '_N/A'																										AS TypeOfDeviation

	FROM StagingImpact.Incident AS INC
	
	LEFT JOIN StagingImpact.Status AS ST
		ON ST.StatusId = INC.StatusId

	LEFT JOIN StagingImpact.IncidentType AS IT
		ON INC.IncidentTypeId = IT.IncidentTypeId

	LEFT JOIN StagingImpact.SeverityType AS SEVT
		ON INC.SeverityTypeId = SEVT.SeverityTypeId

	LEFT JOIN (
		SELECT DISTINCT IncidentId
			FROM StagingImpact.Investigation
			) AS INV
		ON INC.IncidentId = INV.IncidentId

	LEFT JOIN (
		SELECT DISTINCT IIC1.IncidentId, IIC1.ClassificationId, IIC1.Injuryillnessclass
			FROM StagingImpact.InjuryIllnessConsequence AS IIC1
		INNER JOIN (
			SELECT MIN(InjuryIllnessConsequenceId) OVER (PARTITION BY IncidentId) AS MinInjuryIllnessConsequenceId
				FROM StagingImpact.InjuryIllnessConsequence
			) AS IIC2
			ON IIC2.MinInjuryIllnessConsequenceId = IIC1.InjuryIllnessConsequenceId
		) AS IIC
		ON IIC.IncidentId = INC.IncidentId

	LEFT JOIN (
		SELECT ClassificationId
			 , CASE WHEN ClassificationName = 'LTI' THEN 'Lost Time Incident' 
			 		WHEN ClassificationName = 'First aid Treatment' THEN 'First Aid Case'
					WHEN ClassificationName = 'Restricted work case' THEN 'Restricted Work Case'
					ELSE ClassificationName END AS ClassificationName
			FROM StagingImpact.Classification
			) AS C
		ON C.ClassificationId = IIC.ClassificationId

	LEFT JOIN StagingImpact.IncidentRisk AS IR
		ON IR.RiskId = INC.RiskId
	
	LEFT JOIN StagingGraphAPI.ImpactConversionData ICD
		ON INC.ResponsibleDepartmentId = ICD.ImpactDepartmentId

	--LEFT JOIN StagingGraphAPI.Offices O1
	--	ON ICD.OfficeId = O1.SharepointId

	LEFT JOIN DataStore2.OtherSite OS1
		ON ICD.OtherSiteId = OS1.SharepointId

	LEFT JOIN Datastore2.Entity EB1
		ON ICD.EntityBranchId = EB1.SharepointId

	LEFT JOIN DataStore2.Project AS PA1
		ON INC.Project = PA1.IMpactConversionProjectNumber

	LEFT JOIN DataStore2.Vessel V2
		ON ICD.VesselId = V2.VesselId

	LEFT JOIN DataStore2.ActivityLine AL
	ON  COALESCE(EB1.ActivityLineId, OS1.ActivityLineId) = AL.ActivityLineId

	LEFT JOIN StagingGraphAPI.IncidentRegister AS IREG
	ON IREG.IncidentId = INC.IncidentId
	AND IREG.source = 'Impact'
) I


-- 35667

LEFT JOIN (
	SELECT IncidentId, CONVERT(BIT, MAX(WorldWideEquivalent)) AS WorldWideEquivalent
	FROM (
		SELECT IIP.IncidentId											AS IncidentId
				, CASE WHEN IIP.WorldwideEquivalent = 'Yes' THEN 1 
					   ELSE 0 END										AS WorldwideEquivalent
		FROM StagingApprise.IncidentIP IIP
		UNION ALL
		SELECT IIC.IncidentId											AS IncidentId
				, CASE WHEN IREG.worldwideequivalent = 'Yes' THEN 1
					   WHEN IREG.worldwideequivalent = 'No' THEN 0
					   WHEN R.ReassignmentName = 'WW IN' THEN 1
					   ELSE 0 END										AS WorldwideEquivalent
		FROM StagingImpact.InjuryIllnessConsequence AS IIC
		LEFT JOIN StagingImpact.Reassignment AS R
			ON R.ReassignmentId = IIC.ReassignmentId
		LEFT JOIN StagingGraphAPI.IncidentRegister AS IREG
			ON IREG.IncidentId = IIC.IncidentId
			AND IREG.Source = 'Impact'	
		) INP
		GROUP BY IncidentId
	) INP
	ON I.IncidentId = INP.IncidentId
````
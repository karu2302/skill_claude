# Source: `DBs/AzureSingleDB/DataStore1/Views/vwVesselPassportVessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore1/Views/vwVesselPassportVessel.sql`
- SHA-256 of original file: `f15cd0aa7f4dbc4f4944b0c75fa4d777e574a8e7d3a3006d7c75928832b36a63`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql





CREATE VIEW [DataStore1].[vwVesselPassportVessel] AS
SELECT 
	  CONVERT(uniqueidentifier, V.tibcoIdentifier)																				AS VesselUID
	, CONVERT(NVARCHAR(10), ISNULL(V.UnitCode, '_N/A'))																			AS VesselId
	, ISNULL(V.vesselName, '_N/A')																								AS VesselName
	, ISNULL(V.principalParticulars_identifiers_previousVesselName, '_N/A')														AS PreviousVesselName
	, CONVERT(NVARCHAR(10), ISNULL(V.vesselType_, '_N/A'))																		AS VesselType
	, ISNULL(CONVERT(NVARCHAR(255), VT.VesselType), '_N/A')																		AS VesselTypeFull
	, CASE 
		WHEN CONVERT(NVARCHAR(255), VT.VesselType) IS NULL 
		THEN '_N/A'
		ELSE CONCAT(CONVERT(NVARCHAR(255), VT.VesselType),' (', CONVERT(NVARCHAR(10), V.vesselType_), ')') 
	  END																														AS VesselTypeFilter 
	, CONVERT(NVARCHAR(10), ISNULL(V.principalParticulars_identifiers_callSign, '_N/A'))										AS CallSign
	, ISNULL(CONVERT(INT, V.principalParticulars_identifiers_imoNumber), -1)													AS IMONumber
	, ISNULL(CONVERT(INT, V.principalParticulars_identifiers_mmsiNumber), -1)													AS MMSINumber
	, ISNULL(OS.Abbrevation, '_N/A')																							AS ActivityLineId
	, ISNULL(OS.LongDescription, '_N/A')																						AS ActivityLineName
	, ISNULL(V.publicationStatus, '_N/A')																						AS PublicationStatus
	, ISNULL(CONVERT(date, dateLastUpdate), '1900-01-01')																		AS DateLastUpdate
	, ISNULL(CONVERT(date, dateLastUpdateByOwner), '1900-01-01')																AS DateLastUpdateByOwner
	, ISNULL(CONVERT(date, principalParticulars_Dates_ServiceDates_inServiceDate), '1900-01-01')								AS InServiceDate
	, ISNULL(CONVERT(date, principalParticulars_Dates_ServiceDates_outOfServiceDate), '1900-01-01')								AS OutOfServiceDate
	, ISNULL(CONVERT(date, principalParticulars_Dates_ProcessDates_dateLastVesselDataVerification), '1900-01-01')				AS DateLastVesselDataVerification
	, CASE 
		WHEN V.internalVessel = 1 THEN 'Yes' 
		WHEN V.internalVessel = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS IsInternalVessel
	--, CONVERT(NVARCHAR(10), ISNULL(LE.CompanyCode, '_N/A'))																		AS ManagingCompanyCode
	--, ISNULL(LE.CompanyName, '_N/A')																							AS ManagingCompany

	--Planning
	, ISNULL(CONVERT(DATE, V.principalParticulars_flagState_classRenewalDateLastDone), '1900-01-01')							AS ClassRenewalDateLastDone
	, ISNULL(CONVERT(DATE, V.principalParticulars_flagState_classRenewalDateNextLimit), '1900-01-01')							AS ClassRenewalDateNextLimit
	, ISNULL(CONVERT(DATE, V.principalParticulars_flagState_classIntermediate), '1900-01-01')									AS ClassIntermediateDate
	, ISNULL(CONVERT(DATE, V.NavigationCommunication_DynamicPositioning_dpTrialsDate), '1900-01-01')							AS DynamicPositioningTrialsDate
	, CASE 
		WHEN V.principalParticulars_constructionParticulars_iceClass = 1 THEN 'Yes' 
		WHEN V.principalParticulars_constructionParticulars_iceClass = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS IceClass
	, ISNULL(CONVERT(DATE, V.principalParticulars_constructionParticulars_lastSpecialService), '1900-01-01')					AS LastSpecialSurveyDate
	, CASE 
		WHEN V.principalParticulars_flagState_dualClass = 1 THEN 'Yes' 
		WHEN V.principalParticulars_flagState_dualClass = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS DualClass
	
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_upperPivotConfigurationMaxDepth, 0))									AS LadderUpperMaxDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_upperPivotConfigurationMinDepth, 0))									AS LadderUpperMinDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_lowerPivotConfigurationMaxDepth, 0))									AS LadderLowerMaxDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_lowerPivotConfigurationMinDepth, 0))									AS LadderLowerMinDepth
	, CASE 
		WHEN V.mainEquipment_ladder_crushingBypassInstalled = 1 THEN 'Yes' 
		WHEN V.mainEquipment_ladder_crushingBypassInstalled = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS LadderCrushingBypassInstalled
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_maximumDredgingDepth, 0))											AS LadderMaximumDredgingDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_minimumDredgingDepth, 0))											AS LadderMinimumDredgingDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_suctionDiameter, 0))													AS LadderSuctionDiameter
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_weightLadderExcludingCutter, 0))										AS WeightLadderExcludingCutter
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_ladder_weightLadderIncludingCutter, 0))										AS WeightLadderIncludingCutter
	 
	, ISNULL(SS.spuddingSystem, '_N/A')																							AS SpuddingSystem
	, ISNULL(OM.openingMechanism, '_N/A')																						AS OpeningMechanism
	, CONVERT(DECIMAL(18,2), ISNULL(V.operationalParticulars_SailingLimits_maxHs, 0))											AS SailingLimitsMaxHs


	--Auxiliary Equipment
	, CASE 
		WHEN V.auxiliaryEquipment_anchor_positioningAnchors = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_anchor_positioningAnchors = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS PositioningAnchors
	, CONVERT(NVARCHAR(50), ISNULL(FW.freshWaterMaker, '_N/A'))																	AS FreshWaterMaker
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_bladeRacks = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_bladeRacks = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BladeRacks
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_compressor = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_compressor = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS Compressor
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_coshhContainer = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_coshhContainer = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS COSHHContainer
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_gangway = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_gangway = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS Gangway
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_gripper = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_gripper = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS Gripper
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_hammerSeafastening = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_hammerSeafastening = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS HammerSeafastening
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_mpSeafastening = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_mpSeafastening = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS MPSeafastening
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_nacelleSeafastening = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_nacelleSeafastening = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS NacelleSeafastening
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_towerSeafastening = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_towerSeafastening = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS TowerSeafastening
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_tpSeafastening = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_tpSeafastening = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS TPSeafastening
	, ISNULL(V.auxiliaryEquipment_dedicatedMulticat, '_N/A')																	AS DedicatedMulticat

	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_rovSpread = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_rovSpread = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ROVSpread
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_generatorsTrencherSpread = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_generatorsTrencherSpread = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS GeneratorsTrencherSpread
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_cableJointingContainer = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_cableJointingContainer = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS CableJointingContainer
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_cableCuttingContainer = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_cableCuttingContainer = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS CableCuttingContainer
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_boatlanding = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_boatlanding = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BoatLanding
	, ISNULL(V.auxiliaryEquipment_MissionEquipment_additionalME, '_N/A')														AS AdditionalME
	, CASE 
		WHEN V.auxiliaryEquipment_MissionEquipment_massFlowExcavation = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_MissionEquipment_massFlowExcavation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS MassFlowExcavation
	, CASE 
		WHEN V.mainEquipment_cutter_cutterheadWorkshopOnboard = 1 THEN 'Yes' 
		WHEN V.mainEquipment_cutter_cutterheadWorkshopOnboard = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS CutterheadWorkshopOnboard
	, CASE 
		WHEN V.mainEquipment_hopper_Overflow_dismountableRingOverflowAvailable = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_Overflow_dismountableRingOverflowAvailable = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS DismountableRingOverflowAvailable

	--, operationalParticulars_location_location_????
	
	--Flag State
	, ISNULL(V.principalParticulars_flagState_mainClassSymbols, '_N/A')															AS MainClassSymbols
	, ISNULL(V.principalParticulars_flagState_classificationSociety_, '_N/A')													AS ClassificationSociety
	, ISNULL(V.principalParticulars_flagState_additionalClassNotation, '_N/A')													AS AdditionalClassNotation
	, ISNULL(V.principalParticulars_flagState_navigationNotations, '_N/A')														AS NavigationNotations
	, CONVERT(NVARCHAR(50), ISNULL(V.principalParticulars_flagState_classNumber, '_N/A'))										AS ClassNumber
	, ISNULL(P.Port, '_N/A')																									AS PortOfRegistry
	, ISNULL(C.CountryName, '_N/A')																								AS Flag
	

	--Construction Particulars
	, ISNULL(V.principalParticulars_constructionParticulars_buildingYard, '_N/A')												AS BuildingYard
	, CONVERT(INT, ISNULL(V.principalParticulars_constructionParticulars_constructionYear, 1900))								AS ConstructionYear
	, ISNULL(SC.sizeClass, '_N/A')																								AS SizeClass
	, 'General Arrangement Plan'																								AS GeneralArrangementPlan
	--, ISNULL(V.principalParticulars_constructionParticulars_generalArrangementPlan, '_N/A')										AS GeneralArrangementPlanURL
	

	--Personnel
	, ISNULL(CONVERT(INT, V.personnel_crew_maximumPersonsOnBoard), 0)															AS MaximumPersonsOnBoard
	, ISNULL(CONVERT(INT, V.personnel_crew_minimumStandbyManning), 0)															AS MinimumStandbyManning
	, ISNULL(CONVERT(INT, V.personnel_crew_hrAgreedManning), 0)																	AS HRAgreedManning
	, ISNULL(CONVERT(INT, V.personnel_crew_minimumOperationalManning), 0)														AS MinimumOperationalManning
	, ISNULL(CONVERT(BIT, V.personnel_crew_highVoltageVessel), 0)																AS CrewHighVoltageVessel
	--Spud System
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_spudCarrierDynamicLoad, 0))										AS SpudCarrierDynamicLoad
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_spudCarrierSpeedFullLoad, 0))									AS SpudCarrierSpeedFullLoad
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_spudCarrierSpeedIdleReturn, 0))									AS SpudCarrierSpeedIdleReturn
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_spudCarrierStaticCylinderLoad, 0))								AS SpudCarrierStaticCylinderLoad
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_spudCarrierStrokeEffective, 0))									AS SpudCarrierStrokeEffective
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spudCarrier_stepLength, 0))													AS SpudCarrierStepLength
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spud_maximumDepthSpudsBelowWaterline, 0))									AS MaxDepthSpudsBelowWaterLine
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spud_minimumDepthSpudsBelowHull, 0))										AS MinDepthSpudsBelowHull
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_spud_distanceSpudTipBottomSheave, 0))										AS DistanceSpudTipBottomSheave
	
	--Project
	, ISNULL(V.operationalParticulars_project_vesselLifecycleStatus_, '_N/A')													AS VesselLifecycleStatus
	, ISNULL(V.operationalParticulars_project_vesselOperationalPlanningStatus_, '_N/A')											AS VesselOperationalPlanningStatus

	--DimensionWeight	
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_breadthOverall, 0))									AS BreadthOverall
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_breadthOverallWithFenders, 0))						AS breadthOverallWithFenders
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_breadthHull, 0))									AS BreadthHull
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_depth, 0))											AS Depth
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_grossTonnage, 0))									AS GrossTonnage
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_netTonnage, 0))										AS NetTonnage
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lengthBetweenPerpendiculars, 0))					AS LengthBetween
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lengthOverall, 0))									AS LengthOverall
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lengthHull, 0))										AS LengthHull
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lengthIncludingProjectEquipment, 0))				AS LengthIncludingProjectEquipment
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_Legs_maxLegLengthBelowHull, 0))										AS MaxLegLengthBelowHull
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_widthIncludingProjectEquipment, 0))					AS WidthIncludingProjectEquipment
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lightshipWeight, 0))								AS LightShipWeight
--	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_lightshipWeightCIRIA, 0))							AS LightshipWeightCIRIA
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_airDraft, 0))										AS AirDraft
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_airDraftRetractedSpuds, 0))							AS AirDraftRetractedSpuds
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_airDraftTiltedSpuds, 0))							AS AirDraftTiltedSpuds
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_deadWeight15MileDredgeMark, 0))						AS DeadWeight15MileDredgeMark
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_deadWeight8MileDredgeMark, 0))						AS DeadWeight8MileDredgeMark
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_deadWeightAtDraught6_4M, 0))						AS DeadWeightAtDraught6_4M
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_deadWeightAtDraught7M, 0))							AS DeadWeightAtDraught7M

	--Draught
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtDesign, 0))									AS DraughtDesign
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtDredgeMark, 0))								AS DraughtDredgeMark
	----, principalParticulars_dimensionsWeight_draughtDredgingWorksMinimum
	----, principalParticulars_dimensionsWeight_draughtIncreaseRetractableThruster
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtLightShipWeight, 0))							AS DraughtLightShipWeight
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtMaximumElevatedWeight, 0))					AS DraughtMaximumElevatedWeight
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtOperationalEmpty, 0))						AS DraughtOperationalEmpty
	--, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_draughtOperationalLoaded, 0))						AS DraughtOperationalLoaded
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_maximumAirgap, 0))									AS MaximumAirgap
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_minimumWaterDepthRequired, 0))						AS MinimumWaterDepthRequired
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_nominalSwingWidth, 0))								AS NominalSwingWidth
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_stoneBunkerCapacitySummer, 0))						AS StoneBunkerCapacitySummer
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_stoneBunkerCapacityWinter, 0))						AS StoneBunkerCapacityWinter
	, CONVERT(DECIMAL(18,2), ISNULL(V.principalParticulars_dimensionsWeight_underHullClearanceExcludingRetractables, 0))		AS UnderHullClearanceExcludingRetractables
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_harborLoadingParameters_distanceEdgeHoldQuayWall, 0))						AS HarborLoadingDistanceEdgeHoldQuayWall
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_harborLoadingParameters_heightTopCoamingMainDeck, 0))						AS HarborLoadingHeightTopCoamingMainDeck
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_harborLoadingParameters_maximumLoadingSpeed, 0))							AS MaximumLoadingSpeed
	--Hull accommodation
	, CONVERT(INT, ISNULL(V.hull_accommodation_cinema, 0))																		AS Cinema
	, CASE 
		WHEN V.hull_accommodation_deckOffice = 1 THEN 'Yes' 
		WHEN V.hull_accommodation_deckOffice = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS DeckOffice
	, CONVERT(INT, ISNULL(V.hull_accommodation_designatedSmokingArea, 0))														AS DesignatedSmokingArea
	, CONVERT(INT, ISNULL(V.hull_accommodation_galley, 0))																		AS Galley
	, CONVERT(INT, ISNULL(V.hull_accommodation_hospital, 0))																	AS Hospital
	, CONVERT(INT, ISNULL(V.hull_accommodation_laundryRoom, 0))																	AS LaundryRoom
	, CONVERT(INT, ISNULL(V.hull_accommodation_meetingRoom, 0))																	AS MeetingRoom
	, CONVERT(INT, ISNULL(V.hull_accommodation_messroom, 0))																	AS MessRoom
	, CONVERT(INT, ISNULL(V.hull_accommodation_office, 0))																		AS Office
	, CONVERT(INT, ISNULL(V.hull_accommodation_recreationRoom, 0))																AS RecreationRoom
	, CONVERT(INT, ISNULL(V.hull_accommodation_singleBerthCabin, 0))															AS SingleBerthCabin
	, CONVERT(INT, ISNULL(V.hull_accommodation_sportRoom, 0))																	AS SportRoom
	, CONVERT(INT, ISNULL(V.hull_accommodation_twinBerthCabin, 0))																AS TwinBerthCabin
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_cargoHold = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_cargoHold = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS CargoHold
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_chemicalStore = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_chemicalStore = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ChemicalStore
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_clientWorkshop = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_clientWorkshop = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ClientWorkshop
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_electricalAndToolStore = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_electricalAndToolStore = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ElectricalAndToolStore
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_palletStore = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_palletStore = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS PalletStore
	, CASE 
		WHEN V.hull_dedicatedClientFacilities_storekeeperOffice = 1 THEN 'Yes' 
		WHEN V.hull_dedicatedClientFacilities_storekeeperOffice = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS StorekeeperOffice

	--Hull Deck
	, CONVERT(DECIMAL(18,2), ISNULL(V.hull_Deck_freeArea, 0))																	AS FreeArea												
	, CASE 
		WHEN V.hull_Deck_moonpool = 1 THEN 'Yes' 
		WHEN V.hull_Deck_moonpool = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS Moonpool
	, CASE 
		WHEN V.hull_Deck_pumpStation = 1 THEN 'Yes' 
		WHEN V.hull_Deck_pumpStation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS PumpStation
	, CONVERT(DECIMAL(18,2), ISNULL(V.hull_Deck_uniformDeckload, 0))															AS UniformDeckload
	, CASE 
		WHEN V.hull_Deck_Helideck_certification = 1 THEN 'Yes' 
		WHEN V.hull_Deck_Helideck_certification = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS HeliDeckCertification
	, CONVERT(DECIMAL(18,2), ISNULL(V.hull_Deck_Helideck_dValue, 0))															AS HeliDeckDValue
	, CASE 
		WHEN V.hull_Deck_Helideck_floatingModeOperation = 1 THEN 'Yes' 
		WHEN V.hull_Deck_Helideck_floatingModeOperation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS HeliDeckFloatingModeOperation
	, CONVERT(DECIMAL(18,2), ISNULL(V.hull_Deck_Helideck_maximumTakeOffWeight, 0))												AS HeliDeckMaximumTakeOffWeight
	--, CASE 
	--	WHEN V.hull_other_thermalAntiFoulingBoxCoolers = 1 THEN 'Yes' 
	--	WHEN V.hull_other_thermalAntiFoulingBoxCoolers = 0 THEN 'No'
	--	ELSE '_N/A'
	--  END																														AS ThermalAntiFoulingBoxCoolers
	, CASE 
		WHEN V.auxiliaryEquipment_sewageTreatmentPlant = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_sewageTreatmentPlant = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SewageTreatmentPlant
	, CASE 
		WHEN V.mainMachinery_pump_backflushingConfiguration = 1 THEN 'Yes' 
		WHEN V.mainMachinery_pump_backflushingConfiguration = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BackFlushingConfiguration

	--, 'Tank Plan'																												AS TankPlan
	--, ISNULL(V.hull_tanks_tankPlan, '_N/A')																						AS TankPlanURL

	--Discharge
	, CONVERT(NVARCHAR(100), ISNULL(DS.dischargeSystem, '_N/A'))																AS DischargeSystem
	, CASE 
		WHEN V.mainEquipment_Discharge_bargeLoadingPortside = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_bargeLoadingPortside = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BargeLoadingPortside
	, CASE 
		WHEN V.mainEquipment_Discharge_bargeLoadingStarboard = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_bargeLoadingStarboard = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BargeLoadingStarboard
	, CASE 
		WHEN V.mainEquipment_Discharge_BowCoupling_bowCouplingAvailableOB = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_BowCoupling_bowCouplingAvailableOB = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BowCouplingAvailableOB
	, ISNULL(V.mainEquipment_Discharge_BowCoupling_bowCouplingType, '_N/A')														AS BowCouplingType
	, CASE 
		WHEN V.mainEquipment_Discharge_BowCoupling_clickinAvailableOB = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_BowCoupling_clickinAvailableOB = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ClickinAvailableOB
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Discharge_BowCoupling_diameterBowCoupling, 0))								AS DiameterBowCoupling
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Discharge_BowCoupling_diameterRainbowNozzle, 0))							AS DiameterRainbowNozzle
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Discharge_BowCoupling_maxAllowedDischargePressure, 0))						AS MaxAllowedDischargePressure
	, CASE 
		WHEN V.mainEquipment_Discharge_BowCoupling_rainbowThroughBowCoupling = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_BowCoupling_rainbowThroughBowCoupling = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS RainbowThroughBowCoupling
	, CASE 
		WHEN V.mainEquipment_Discharge_BowCoupling_ypieceNozzleAvailable = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Discharge_BowCoupling_ypieceNozzleAvailable = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS YPieceNozzleAvailable
	--, ISNULL(V.mainEquipment_Discharge_compatibleBarges_, '_N/A')																AS CompatibleBarges
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Discharge_diameterDischargePipe, 0))										AS DiameterDischargePipe
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Discharge_hydraulicQuickReleasePipeCoupling, 0))							AS HydraulicQuickReleasePipeCoupling

	--, CONVERT(DECIMAL(18,2), ISNULL(V.electrical_powerGenerationAndSupply_shorePowerCapacityInstalledOnboard, 0))				AS ShorePowerCapacityInstalledOnboard
	--, CONVERT(DECIMAL(18,2), ISNULL(V.electrical_powerGenerationAndSupply_shorePowerRequiredForOperations, 0))					AS ShorePowerRequiredForOperations

	--Hopper
	, ISNULL(V.mainEquipment_hopper_amobLocation, '_N/A')																		AS AMOBLocation
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_breadthHopper, 0))													AS BreadthHopper
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_deeploaders, 0))																AS DeepLoaders
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_designSpecificDensity, 0))											AS DesignSpecificDensity
	, CASE 
		WHEN V.mainEquipment_hopper_Discharge_dewateringInstallation = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_Discharge_dewateringInstallation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS DewateringInstallation
	, CASE 
		WHEN V.mainEquipment_hopper_Discharge_jetsInHopper = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_Discharge_jetsInHopper = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS JetsInHopper
	, CASE 
		WHEN V.mainEquipment_hopper_Discharge_preDumpingDoors = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_Discharge_preDumpingDoors = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS PreDumpingDoors
	, CASE 
		WHEN V.mainEquipment_hopper_Discharge_selfEmptyingChannel = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_Discharge_selfEmptyingChannel = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SelfEmptyingChannel	
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_hexagonalDiffusors, 0))														AS HexagonalDiffusors
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_hopperCapacityMaxOverflow, 0))										AS HopperCapacityMaxOverflow
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_hopperCapacityMinOverflow, 0))										AS HopperCapacityMinOverflow
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_hopperCapacityTopCoaming, 0))										AS HopperCapacityTopCoaming
	, CASE 
		WHEN V.mainEquipment_hopper_hopperProtection = 1 THEN 'Yes' 
		WHEN V.mainEquipment_hopper_hopperProtection = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS HopperProtection
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_lengthHopper, 0))													AS LengthHopper
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_maximalOpeningAngle00, 0))											AS MaximalOpeningAngle
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_maximumHopperLoad, 0))												AS MaximumHopperLoad
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_numberOfDoors, 0))																AS NumberOfDoors	
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_numberPredumpingDoors, 0))														AS NumberPredumpingDoors
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_Overflow_numberOfGreenValves, 0))												AS NumberOfGreenValves
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_Overflow_numberOfOverflows, 0))												AS NumberOfOverflows
	, CONVERT(INT, ISNULL(V.mainEquipment_hopper_Overflow_numberOfPlumigators, 0))												AS NumberOfPlumigators	
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_overflowDiameter, 0))												AS OverflowDiameter
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_hopper_pressureSplitCylinders, 0))											AS PressureSplitCylinders
	--, CASE 
	--	WHEN V.mainEquipment_hopper_sievingInstallation = 1 THEN 'Yes' 
	--	WHEN V.mainEquipment_hopper_sievingInstallation = 0 THEN 'No'
	--	ELSE '_N/A'
	--  END																														AS SievingInstallation

	--Jacking
	, ISNULL(JL.jackingLegType, '_N/A')																							AS JackingLegType
	, ISNULL(JS.jackingSystemType, '_N/A')																						AS JackingSystemType
	, ISNULL(JSM.manufacturerName, '_N/A')																						AS JackingSystemManufacturer
	, ISNULL(ST.spudcanType, '_N/A')																							AS SpudcanType
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_Legs_legLength, 0))													AS LegLength
	, CONVERT(NVARCHAR(100), ISNULL(V.mainEquipment_Jacking_Spudcans_spudcanDimension00, '_N/A'))								AS SpudcanDimension
	, CASE 
		WHEN V.mainEquipment_Jacking_Spudcans_spudcanExtension = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Jacking_Spudcans_spudcanExtension = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SpudcanExtension
	, ISNULL(V.mainEquipment_Jacking_Spudcans_spudcanExtensionDimension00, '_N/A')												AS SpudcanExtensionDimension
	, CASE 
		WHEN V.mainEquipment_Jacking_jettingSystemAvailable = 1 THEN 'Yes' 
		WHEN V.mainEquipment_Jacking_jettingSystemAvailable = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS JettingSystemAvailable
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_maximumElevatedWeight00, 0))										AS MaximumElevatedWeight
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_Legs_maximumPreLoadPerLeg00, 0))									AS MaximumPreLoadPerLeg
	, CONVERT(decimal(18,2), ISNULL(V.mainEquipment_Jacking_speedUp, 0))														AS JackingSpeedUp
	, CONVERT(decimal(18,2), ISNULL(V.mainEquipment_Jacking_speedDown, 0))														AS JackingSpeedDown
	, CONVERT(decimal(18,2), ISNULL(mainEquipment_Jacking_speed_legHandlingSpeedUp, 0))											AS LegHandlingSpeedUp
	, CONVERT(decimal(18,2), ISNULL(mainEquipment_Jacking_speed_legHandlingSpeedDown, 0))										AS LegHandlingSpeedDown
		--Limits
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_JackingLimits_associatedWavePeriod, 0))								AS AssociatedWavePeriod
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_JackingLimits_surfaceCurrent, 0))									AS SurfaceCurrent
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_JackingLimits_waveHeight, 0))										AS WaveHeight
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Jacking_JackingLimits_windSpeed, 0))										AS WindSpeed
	
	--Propulsion and Steering
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_maxSpeedSailingEconomical, 0))						AS MaxSpeedSailingEconomical
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_speedMaximum, 0))										AS SpeedMaximum
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_speedEmpty, 0))										AS SpeedEmpty
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_speedLoaded, 0))										AS SpeedLoadedSailing
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_totalPropulsionPowerFreeSailing, 0))					AS TotalPropulsionPowerFreeSailing	
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_propulsionAndSteering_totalPropulsionPowerTrailing, 0))						AS TotalPropulsionPowerTrailing

	--Navigation Communication
	, ISNULL(DP.dynamicPositioningClass, '_N/A')																				AS DynamicPositioningClass
	, ISNULL(GMDS.gmdssSeaArea, '_N/A')																							AS GMDSSSeaArea
	, CONVERT(DECIMAL(18,2), ISNULL(V.NavigationCommunication_Internet_internetAvailableForPOB, 0))								AS InternetAvailableForPOB
	, ISNULL(V.NavigationCommunication_Internet_internetProvider, '_N/A')														AS InternetProvider										
	, CONVERT(DECIMAL(18,2), ISNULL(V.NavigationCommunication_Internet_uploadLimit, 0))											AS InternetUploadLimit
	, ISNULL(DPM.manufacturerName, '_N/A')																						AS DPManufacturer 
	--, ISNULL(V.NavigationCommunication_DynamicPositioning_make, '_N/A')															AS DynamicPositioningMake
	, ISNULL(V.NavigationCommunication_contactInformation_globalSatPhone1, '_N/A')												AS GlobalSatPhone1
	, ISNULL(V.NavigationCommunication_contactInformation_globalSatPhone2, '_N/A')												AS GlobalSatPhone2
	, ISNULL(V.NavigationCommunication_contactInformation_emailCaptain, '_N/A')													AS EmailCaptain
	, ISNULL(V.NavigationCommunication_contactInformation_emailChiefEngineer, '_N/A')											AS EmailChiefEngineer
	, CONVERT(BIT, ISNULL(V.NavigationCommunication_contactInformation_vsatOnboard, 0))											AS VSatOnBoard
	, ISNULL(V.NavigationCommunication_contactInformation_vsatPhone1, '_N/A')													AS VSatPhone1
	, ISNULL(V.NavigationCommunication_contactInformation_vsatPhone2, '_N/A')													AS VSatPhone2

	--Software
	, CASE 
		WHEN V.operationalParticulars_software_dtps = 1 THEN 'Yes' 
		WHEN V.operationalParticulars_software_dtps = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SoftwareDTPS
	, CASE 
		WHEN V.operationalParticulars_software_loadComputer = 1 THEN 'Yes' 
		WHEN V.operationalParticulars_software_loadComputer = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SoftwareLoadComputer
	, CASE 
		WHEN V.operationalParticulars_software_piOnboard = 1 THEN 'Yes' 
		WHEN V.operationalParticulars_software_piOnboard = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SoftwarePiOnBoard
	, ISNULL(V.operationalParticulars_software_shipBehaviourMonitoringSystem, '_N/A')											AS SoftwareShipBehaviourMonitoringSystem
	, CASE 
		WHEN V.operationalParticulars_software_workabilityTool = 1 THEN 'Yes' 
		WHEN V.operationalParticulars_software_workabilityTool = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SoftwareWorkabilityTool
	
	--QHSE Sustainability
	, CASE 
		WHEN V.QHSES_sustainability_biodegradableOil = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_biodegradableOil = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BiodegradableOil
	, CASE 
		WHEN V.QHSES_sustainability_biodegradableGrease = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_biodegradableGrease = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BiodegradableGrease
	, CASE 
		WHEN V.QHSES_sustainability_energyRecuperation = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_energyRecuperation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS EnergyRecuperation
	, CASE 
		WHEN V.QHSES_sustainability_greenPassport = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_greenPassport = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS GreenPassport
	, CASE 
		WHEN V.QHSES_sustainability_h2sInstallation = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_h2sInstallation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS H2sInstallation
	, CASE 
		WHEN V.QHSES_sustainability_inventoryHazardousMaterials = 1 THEN 'Yes' 
		WHEN V.QHSES_sustainability_inventoryHazardousMaterials = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS InventoryHazardousMaterials
	, CASE 
		WHEN V.QHSES_safety_safetyCase = 1 THEN 'Yes' 
		WHEN V.QHSES_safety_safetyCase = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SafetyCase
	, ISNULL(CONVERT(Date, QHSES_audit_lastCmid), '1900-01-01')																	AS AuditLastCmid
	, ISNULL(CONVERT(Date, QHSES_audit_lastOvid), '1900-01-01')																	AS AuditLastOvid


	, ISNULL(QHSES_regulatoryCompliance_ism, '_N/A')																			AS RegulatoryComplianceISM
	, ISNULL(QHSES_regulatoryCompliance_isps, '_N/A')																			AS RegulatoryComplianceISPS
	, ISNULL(QHSES_regulatoryCompliance_mlc, '_N/A')																			AS RegulatoryComplianceMLC
	, ISNULL(QHSES_internalCompliance_vms, '_N/A')																				AS InternalComplianceVMS
	, ISNULL(QHSES_internalCompliance_fuelOilApp, '_N/A')																		AS InternalComplianceFuelOilApp
	--Other
	--, ISNULL(V.principalParticulars_other_owner00, '_N/A')																		AS Owner
	, CASE 
		WHEN V.principalParticulars_other_seaGoing = 1 THEN 'Yes' 
		WHEN V.principalParticulars_other_seaGoing = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SeaGoing
	, CASE 
		WHEN V.principalParticulars_other_selfPropelled = 1 THEN 'Yes' 
		WHEN V.principalParticulars_other_selfPropelled = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SelfPropelled
	, CASE 
		WHEN V.mainMachinery_pump_degassingInstallation = 1 THEN 'Yes' 
		WHEN V.mainMachinery_pump_degassingInstallation = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS DegassingInstallation
	, CASE 
		WHEN V.auxiliaryEquipment_multibeam = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_multibeam = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS MultibeamInstalled
	, CASE 
		WHEN V.auxiliaryEquipment_piracyOutfitting = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_piracyOutfitting = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS PiracyOutfitting
	, CASE 
		WHEN V.auxiliaryEquipment_incinerator = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_incinerator = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS IncineratorAvailable
	, CASE 
		WHEN V.auxiliaryEquipment_oilBurnerOperational = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_oilBurnerOperational = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS OilBurnerOperational
	, CASE 
		WHEN V.auxiliaryEquipment_wasteCompactor = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_wasteCompactor = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS WasteCompactorAvailable

	, CASE 
		WHEN V.principalParticulars_other_beaching = 1 THEN 'Yes' 
		WHEN V.principalParticulars_other_beaching = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS Beaching
	--Engine
	, CONVERT(NVARCHAR(50), ISNULL(V.mainMachinery_combustionEngine_mainCoolingMedium, '_N/A'))									AS MainCoolingMedium
	, CONVERT(NVARCHAR(50), ISNULL(V.mainMachinery_combustionEngine_fuelAutonomySea, '_N/A'))									AS FuelAutonomySea
	--Fallpipe
	, ISNULL(FPM.manufacturerName, '_N/A')																						AS FallpipeROVManufacturer
	, ISNULL(V.mainEquipment_Fallpipe_bucketsOB, '_N/A')																		AS BucketsOB
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_FallpipeWires_lengthOnBoardFPWires, 0))							AS LengthOnBoardFPWires
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_FallpipeWires_totalAvailableLengthFPWires, 0))						AS TotalAvailableLengthFPWires
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_ROV_amplitudeAutomaticHeaveCompensation, 0))						AS AmplitudeAutomaticHeaveCompensation
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_ROV_powerROV, 0))													AS PowerROV
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_ROV_rovLengthOB, 0))												AS ROVLengthOB
	, ISNULL(V.mainEquipment_Fallpipe_ROV_thrustersROV, '_N/A')																	AS ThrustersROV
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_Fallpipe_ROV_totalAvailableLengthROV, 0))									TotalAvailableLengthROV
	--Pump
	, CASE 
		WHEN V.mainMachinery_pump_conversionRequiredToBypassBoosterPump = 1 THEN 'Yes' 
		WHEN V.mainMachinery_pump_conversionRequiredToBypassBoosterPump = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS ConversionRequiredToBypassBoosterPump						
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainMachinery_pump_nominalFlowRateDuringPumpingAshore, 0))								AS PumpNominalFlowRateDuringPumpingAshore

	--Trencher Spread
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterPower, 0))				AS ChainCutterPower
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterWidth, 0))				AS ChainCutterWidth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumCuttingDepthChainCutter, 0))	AS MaximumCuttingDepthChainCutter
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumSoilHardnessChainCutter, 0))	AS MaximumSoilHardnessChainCutter
	--, ISNULL(V.mainEquipment_TrencherSpread_BurialTools_JetTool_jetToolLocation_, '_N/A')										AS JetToolLocation
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_JetTool_jetToolPower, 0))						AS JetToolPower
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_JetTool_trenchDepth, 0))							AS TrenchDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_BurialTools_overallDesignMaximumProductOutsideDiameter, 0))	AS MaximumProductOutsideDiameter
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_height, 0))									AS TrencherSpreadHeight
	, CONVERT(DECIMAL(18,2), ISNULL( V.mainEquipment_TrencherSpread_MainParticulars_length, 0))									AS TrencherSpreadLength
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_weight, 0))									AS TrencherSpreadWeight
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_width, 0))									AS TrencherSpreadWidth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_lengthWithoutJetTool, 0))					AS LengthWithoutJetTool
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMax, 0))						AS SpeedNoBurialMax
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMin, 0))						AS SpeedNoBurialMin
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMax, 0))						AS SpeedTrenchingMax
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMin, 0))						AS SpeedTrenchingMin
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorMaximumOperatingDepth, 0))			AS TractorMaximumOperatingDepth
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorPowerMax, 0))							AS TractorPowerMax
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorPowerMin, 0))							AS TractorPowerMin
	, ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorType, '_N/A')												AS TractorType
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMax, 0))					AS TractorTrackWidthMax
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMin, 0))					AS TractorTrackWidthMin
	--Cable Installation spread
	--, ISNULL(V.mainEquipment_CableInstallationSpread_Chute_chuteLocation_, '_N/A')												AS ChuteLocation
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_Chute_maximumFleetAngle, 0))						AS ChuteMaximumFleetAngle
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_Chute_minimumBendingRadiusChute, 0))				AS ChuteMinimumBendingRadius
	--, ISNULL(V.mainEquipment_CableInstallationSpread_LengthBufferSystem_lengthBufferSystemLocation_, '_N/A')					AS LengthBufferSystemLocation
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_LengthBufferSystem_maximumLengthBuffered, 0))		AS MaximumLengthBuffered
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_LengthBufferSystem_maximumProductDiameter, 0))		AS MaximumProductDiameter
	--, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_LengthBufferSystem_minimumBendingRadiusLengthBuffer, 0))	AS MinimumBendingRadiusLengthBuffer
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_Quadrant_minimumBendingRadiusQuadrant, 0))			AS MinimumBendingRadiusQuadrant
	, CONVERT(DECIMAL(18,2), ISNULL(V.mainEquipment_CableInstallationSpread_Quadrant_weightQuadrant, 0))						AS WeightQuadrant
	--anchor
	, CASE 
		WHEN V.auxiliaryEquipment_anchor_boxAnchorsAvailable = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_anchor_boxAnchorsAvailable = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS BoxAnchorsAvailable
	, CONVERT(DECIMAL(18,2), ISNULL(V.auxiliaryEquipment_anchor_maximumAnchorBoomLiftCapacity, 0))								AS MaxAnchorBoomLiftCapacity
	, CASE 
		WHEN V.auxiliaryEquipment_anchor_sideWirePontoonsAvailable = 1 THEN 'Yes' 
		WHEN V.auxiliaryEquipment_anchor_sideWirePontoonsAvailable = 0 THEN 'No'
		ELSE '_N/A'
	  END																														AS SideWirePontoonsAvailable
	, CONVERT(DECIMAL(18,2), ISNULL(V.auxiliaryEquipment_sidewires_maximumPullingForce, 0))										AS MaximumPullingForce
	, CONVERT(DECIMAL(18,2), ISNULL(V.auxiliaryEquipment_sidewires_maximumSwingSpeed, 0))										AS MaximumSwingSpeed
	, CONVERT(DECIMAL(18,2), ISNULL(V.auxiliaryEquipment_sidewires_nominalPullingForce, 0))										AS NominalPullingForce
	, CONVERT(DECIMAL(18,2), ISNULL(V.auxiliaryEquipment_sidewires_nominalSwingSpeed, 0))										AS NominalSwingSpeed
	
FROM StagingDataMarket.VesselPassport_Vessel V

LEFT JOIN StagingDataMarket.VesselType VT
	ON V.vesselType_ = VT.Abbreviation

LEFT JOIN StagingDataMarket.VesselPassport_PortOfRegistry P
	ON V.principalParticulars_flagState_portOfRegistry_= P.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_Dynamic_Positioning_Class DP
	ON V.NavigationCommunication_DynamicPositioning_dpClass_ = DP.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_GMDSSSeaArea GMDS
	ON V.NavigationCommunication_gmdssSeaArea_ = GMDS.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_JackingLegType JL
	ON V.mainEquipment_Jacking_Legs_typeLeg_ = JL.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_JackingSystemType JS
	ON V.mainEquipment_Jacking_jackingSystemType_ = JS.tibcoIdentifier

--LEFT JOIN StagingDataMarket.VesselPassport_Ladder_Configuration LC
--	ON V.mainEquipment_ladder_configuration_ = LC.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_SpudcanType ST
	ON V.mainEquipment_Jacking_Spudcans_spudcansType_ = ST.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_SpuddingSystem SS
	ON V.mainEquipment_spudCarrier_spuddingSystem_ = SS.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_Opening_Mechanism OM
	ON V.mainEquipment_hopper_Discharge_OpeningMechanismSelfEmptyingChannel_ = OM.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_Size_Class SC
	ON V.principalParticulars_constructionParticulars_sizeClass_ = SC.tibcoIdentifier

LEFT JOIN StagingDataMarket.Country C
	ON V.principalParticulars_flagState_flag_ = C.CodeAlpha3

LEFT JOIN StagingDataMarket.VesselPassport_FreshWaterMaker FW
	ON V.auxiliaryEquipment_freshWaterMaker_ = FW.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_DischargeSystem DS
	ON V.mainEquipment_hopper_Discharge_dischargeSystem_ = DS.tibcoIdentifier

--LEFT JOIN StagingDataMarket.VesselPassport_Vessel V2
--	ON V.DaqaMetaData_ClusterId = V2.DaqaMetaData_ClusterId
--	AND V.unitCode = V2.unitCode
--	AND V2.sourceSystem_ = 'EBX'

LEFT JOIN StagingDataMarket.VesselPassport_Manufacturer FPM
	ON V.mainEquipment_Fallpipe_ROV_manufacturerROV_ = FPM.tibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_Manufacturer JSM
	ON V.mainEquipment_Jacking_jackingSystemManufacturer_ = JSM.tibcoIdentifier

LEFT JOIN StagingDataMarket.OrganisationalStructure OS
	ON V.principalParticulars_identifiers_activityLine_ = OS.TIBCOIndetifierUUID

--LEFT JOIN StagingDataMarket.LegalEntities LE
--	ON V.principalParticulars_identifiers_managingCompany_ = LE.TibcoIdentifier

LEFT JOIN StagingDataMarket.VesselPassport_Manufacturer DPM
	ON V.NavigationCommunication_DynamicPositioning_dpManufacturer_ = DPM.tibcoIdentifier
````
# Source: `DBs/AzureSingleDB/StagingDataMarket/Tables/VesselPassport_Vessel.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/StagingDataMarket/Tables/VesselPassport_Vessel.sql`
- SHA-256 of original file: `65b4096f39debb53298307bb8cd45f1266e614c29f82110da515a762ba66de34`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE TABLE [StagingDataMarket].[VesselPassport_Vessel] (
    [auxiliaryEquipment_anchor_boxAnchorsAvailable]                                       NVARCHAR (255)  NULL,
    [auxiliaryEquipment_anchor_maximumAnchorBoomLiftCapacity]                             NVARCHAR (255)  NULL,
    [auxiliaryEquipment_anchor_positioningAnchors]                                        NVARCHAR (255)  NULL,
    [auxiliaryEquipment_anchor_sideWirePontoonsAvailable]                                 NVARCHAR (255)  NULL,
    [auxiliaryEquipment_dedicatedMulticat]                                                NVARCHAR (255)  NULL,
    [auxiliaryEquipment_freshWaterMaker_]                                                 NVARCHAR (255)  NULL,
    [auxiliaryEquipment_incinerator]                                                      NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_additionalME]                                    NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_bladeRacks]                                      NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_boatlanding]                                     NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_cableCuttingContainer]                           NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_cableJointingContainer]                          NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_compressor]                                      NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_coshhContainer]                                  NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_gangway]                                         NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_generatorsTrencherSpread]                        NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_gripper]                                         NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_hammerSeafastening]                              NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_massFlowExcavation]                              NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_mpSeafastening]                                  NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_nacelleSeafastening]                             NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_rovSpread]                                       NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_towerSeafastening]                               NVARCHAR (255)  NULL,
    [auxiliaryEquipment_MissionEquipment_tpSeafastening]                                  NVARCHAR (255)  NULL,
    [auxiliaryEquipment_multibeam]                                                        NVARCHAR (255)  NULL,
    [auxiliaryEquipment_oilBurnerOperational]                                             NVARCHAR (255)  NULL,
    [auxiliaryEquipment_piracyOutfitting]                                                 NVARCHAR (255)  NULL,
    [auxiliaryEquipment_sewageTreatmentPlant]                                             NVARCHAR (255)  NULL,
    [auxiliaryEquipment_sidewires_maximumPullingForce]                                    NVARCHAR (255)  NULL,
    [auxiliaryEquipment_sidewires_maximumSwingSpeed]                                      NVARCHAR (255)  NULL,
    [auxiliaryEquipment_sidewires_nominalPullingForce]                                    NVARCHAR (255)  NULL,
    [auxiliaryEquipment_sidewires_nominalSwingSpeed]                                      NVARCHAR (255)  NULL,
    [auxiliaryEquipment_wasteCompactor]                                                   NVARCHAR (255)  NULL,
    [dateLastUpdate]                                                                      NVARCHAR (255)  NULL,
    [dateLastUpdateByOwner]                                                               NVARCHAR (255)  NULL,
    [hull_accommodation_cinema]                                                           NVARCHAR (255)  NULL,
    [hull_accommodation_deckOffice]                                                       NVARCHAR (255)  NULL,
    [hull_accommodation_designatedSmokingArea]                                            NVARCHAR (255)  NULL,
    [hull_accommodation_galley]                                                           NVARCHAR (255)  NULL,
    [hull_accommodation_hospital]                                                         NVARCHAR (255)  NULL,
    [hull_accommodation_laundryRoom]                                                      NVARCHAR (255)  NULL,
    [hull_accommodation_meetingRoom]                                                      NVARCHAR (255)  NULL,
    [hull_accommodation_messroom]                                                         NVARCHAR (255)  NULL,
    [hull_accommodation_office]                                                           NVARCHAR (255)  NULL,
    [hull_accommodation_recreationRoom]                                                   NVARCHAR (255)  NULL,
    [hull_accommodation_singleBerthCabin]                                                 NVARCHAR (255)  NULL,
    [hull_accommodation_sportRoom]                                                        NVARCHAR (255)  NULL,
    [hull_accommodation_twinBerthCabin]                                                   NVARCHAR (255)  NULL,
    [hull_Deck_freeArea]                                                                  NVARCHAR (255)  NULL,
    [hull_Deck_Helideck_certification]                                                    NVARCHAR (255)  NULL,
    [hull_Deck_Helideck_dValue]                                                           NVARCHAR (255)  NULL,
    [hull_Deck_Helideck_floatingModeOperation]                                            NVARCHAR (255)  NULL,
    [hull_Deck_Helideck_maximumTakeOffWeight]                                             NVARCHAR (255)  NULL,
    [hull_Deck_moonpool]                                                                  NVARCHAR (255)  NULL,
    [hull_Deck_pumpStation]                                                               NVARCHAR (255)  NULL,
    [hull_Deck_uniformDeckload]                                                           NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_cargoHold]                                            NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_chemicalStore]                                        NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_clientWorkshop]                                       NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_electricalAndToolStore]                               NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_palletStore]                                          NVARCHAR (255)  NULL,
    [hull_dedicatedClientFacilities_storekeeperOffice]                                    NVARCHAR (255)  NULL,
    [internalVessel]                                                                      NVARCHAR (255)  NULL,
    [mainEquipment_CableInstallationSpread_Quadrant_minimumBendingRadiusQuadrant]         NVARCHAR (255)  NULL,
    [mainEquipment_CableInstallationSpread_Quadrant_weightQuadrant]                       NVARCHAR (255)  NULL,
    [mainEquipment_cutter_cutterheadWorkshopOnboard]                                      NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_bargeLoadingPortside]                                        NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_bargeLoadingStarboard]                                       NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_bowCouplingAvailableOB]                          NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_bowCouplingType]                                 NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_clickinAvailableOB]                              NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_diameterBowCoupling]                             NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_diameterRainbowNozzle]                           NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_maxAllowedDischargePressure]                     NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_rainbowThroughBowCoupling]                       NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_BowCoupling_ypieceNozzleAvailable]                           NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_diameterDischargePipe]                                       NVARCHAR (255)  NULL,
    [mainEquipment_Discharge_hydraulicQuickReleasePipeCoupling]                           NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_bucketsOB]                                                    NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_FallpipeWires_lengthOnBoardFPWires]                           NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_FallpipeWires_totalAvailableLengthFPWires]                    NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_amplitudeAutomaticHeaveCompensation]                      NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_manufacturerROV_]                                         NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_powerROV]                                                 NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_rovLengthOB]                                              NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_thrustersROV]                                             NVARCHAR (255)  NULL,
    [mainEquipment_Fallpipe_ROV_totalAvailableLengthROV]                                  NVARCHAR (255)  NULL,
    [mainEquipment_harborLoadingParameters_distanceEdgeHoldQuayWall]                      NVARCHAR (255)  NULL,
    [mainEquipment_harborLoadingParameters_heightTopCoamingMainDeck]                      NVARCHAR (255)  NULL,
    [mainEquipment_harborLoadingParameters_maximumLoadingSpeed]                           NVARCHAR (255)  NULL,
    [mainEquipment_hopper_amobLocation]                                                   NVARCHAR (255)  NULL,
    [mainEquipment_hopper_breadthHopper]                                                  NVARCHAR (255)  NULL,
    [mainEquipment_hopper_deeploaders]                                                    NVARCHAR (255)  NULL,
    [mainEquipment_hopper_designSpecificDensity]                                          NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_dewateringInstallation]                               NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_dischargeSystem_]                                     NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_jetsInHopper]                                         NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_OpeningMechanismSelfEmptyingChannel_]                 NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_preDumpingDoors]                                      NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Discharge_selfEmptyingChannel]                                  NVARCHAR (255)  NULL,
    [mainEquipment_hopper_hexagonalDiffusors]                                             NVARCHAR (255)  NULL,
    [mainEquipment_hopper_hopperCapacityMaxOverflow]                                      NVARCHAR (255)  NULL,
    [mainEquipment_hopper_hopperCapacityMinOverflow]                                      NVARCHAR (255)  NULL,
    [mainEquipment_hopper_hopperCapacityTopCoaming]                                       NVARCHAR (255)  NULL,
    [mainEquipment_hopper_hopperProtection]                                               NVARCHAR (255)  NULL,
    [mainEquipment_hopper_lengthHopper]                                                   NVARCHAR (255)  NULL,
    [mainEquipment_hopper_maximalOpeningAngle00]                                          NVARCHAR (255)  NULL,
    [mainEquipment_hopper_maximumHopperLoad]                                              NVARCHAR (255)  NULL,
    [mainEquipment_hopper_numberOfDoors]                                                  NVARCHAR (255)  NULL,
    [mainEquipment_hopper_numberPredumpingDoors]                                          NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Overflow_dismountableRingOverflowAvailable]                     NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Overflow_numberOfGreenValves]                                   NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Overflow_numberOfOverflows]                                     NVARCHAR (255)  NULL,
    [mainEquipment_hopper_Overflow_numberOfPlumigators]                                   NVARCHAR (255)  NULL,
    [mainEquipment_hopper_overflowDiameter]                                               NVARCHAR (255)  NULL,
    [mainEquipment_hopper_pressureSplitCylinders]                                         NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_JackingLimits_associatedWavePeriod]                            NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_JackingLimits_surfaceCurrent]                                  NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_JackingLimits_waveHeight]                                      NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_JackingLimits_windSpeed]                                       NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_jackingSystemManufacturer_]                                    NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_jackingSystemType_]                                            NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_jettingSystemAvailable]                                        NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Legs_legLength]                                                NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Legs_maximumPreLoadPerLeg00]                                   NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Legs_maxLegLengthBelowHull]                                    NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Legs_typeLeg_]                                                 NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_maximumElevatedWeight00]                                       NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_speed_legHandlingSpeedDown]                                    NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_speed_legHandlingSpeedUp]                                      NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_speedDown]                                                     NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_speedUp]                                                       NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Spudcans_spudcanDimension00]                                   NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Spudcans_spudcanExtension]                                     NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Spudcans_spudcanExtensionDimension00]                          NVARCHAR (255)  NULL,
    [mainEquipment_Jacking_Spudcans_spudcansType_]                                        NVARCHAR (255)  NULL,
    [mainEquipment_ladder_crushingBypassInstalled]                                        NVARCHAR (255)  NULL,
    [mainEquipment_ladder_lowerPivotConfigurationMaxDepth]                                NVARCHAR (255)  NULL,
    [mainEquipment_ladder_lowerPivotConfigurationMinDepth]                                NVARCHAR (255)  NULL,
    [mainEquipment_ladder_maximumDredgingDepth]                                           NVARCHAR (255)  NULL,
    [mainEquipment_ladder_minimumDredgingDepth]                                           NVARCHAR (255)  NULL,
    [mainEquipment_ladder_suctionDiameter]                                                NVARCHAR (255)  NULL,
    [mainEquipment_ladder_upperPivotConfigurationMaxDepth]                                NVARCHAR (255)  NULL,
    [mainEquipment_ladder_upperPivotConfigurationMinDepth]                                NVARCHAR (255)  NULL,
    [mainEquipment_ladder_weightLadderExcludingCutter]                                    NVARCHAR (255)  NULL,
    [mainEquipment_ladder_weightLadderIncludingCutter]                                    NVARCHAR (255)  NULL,
    [mainEquipment_spud_distanceSpudTipBottomSheave]                                      NVARCHAR (255)  NULL,
    [mainEquipment_spud_maximumDepthSpudsBelowWaterline]                                  NVARCHAR (255)  NULL,
    [mainEquipment_spud_minimumDepthSpudsBelowHull]                                       NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spudCarrierDynamicLoad]                                    NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spudCarrierSpeedFullLoad]                                  NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spudCarrierSpeedIdleReturn]                                NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spudCarrierStaticCylinderLoad]                             NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spudCarrierStrokeEffective]                                NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_spuddingSystem_]                                           NVARCHAR (255)  NULL,
    [mainEquipment_spudCarrier_stepLength]                                                NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterPower]               NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterWidth]               NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumCuttingDepthChainCutter] NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumSoilHardnessChainCutter] NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_BurialTools_overallDesignMaximumProductOutsideDiameter] NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_height]                                 NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_length]                                 NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_lengthWithoutJetTool]                   NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMax]                       NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMin]                       NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMax]                      NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMin]                      NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorMaximumOperatingDepth]           NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorPowerMax]                        NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorPowerMin]                        NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMax]                   NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMin]                   NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_tractorType]                            NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_weight]                                 NVARCHAR (255)  NULL,
    [mainEquipment_TrencherSpread_MainParticulars_width]                                  NVARCHAR (255)  NULL,
    [mainMachinery_combustionEngine_fuelAutonomySea]                                      NVARCHAR (255)  NULL,
    [mainMachinery_combustionEngine_mainCoolingMedium]                                    NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_maxSpeedSailingEconomical]                       NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_speedEmpty]                                      NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_speedLoaded]                                     NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_speedMaximum]                                    NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_totalPropulsionPowerFreeSailing]                 NVARCHAR (255)  NULL,
    [mainMachinery_propulsionAndSteering_totalPropulsionPowerTrailing]                    NVARCHAR (255)  NULL,
    [mainMachinery_pump_backflushingConfiguration]                                        NVARCHAR (255)  NULL,
    [mainMachinery_pump_conversionRequiredToBypassBoosterPump]                            NVARCHAR (255)  NULL,
    [mainMachinery_pump_degassingInstallation]                                            NVARCHAR (255)  NULL,
    [mainMachinery_pump_nominalFlowRateDuringPumpingAshore]                               NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_emailCaptain]                             NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_emailChiefEngineer]                       NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_globalSatPhone1]                          NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_globalSatPhone2]                          NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_vsatOnboard]                              NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_vsatPhone1]                               NVARCHAR (255)  NULL,
    [NavigationCommunication_contactInformation_vsatPhone2]                               NVARCHAR (255)  NULL,
    [NavigationCommunication_DynamicPositioning_dpClass_]                                 NVARCHAR (255)  NULL,
    [NavigationCommunication_DynamicPositioning_dpManufacturer_]                          NVARCHAR (255)  NULL,
    [NavigationCommunication_DynamicPositioning_dpTrialsDate]                             NVARCHAR (255)  NULL,
    [NavigationCommunication_gmdssSeaArea_]                                               NVARCHAR (255)  NULL,
    [NavigationCommunication_Internet_internetAvailableForPOB]                            NVARCHAR (255)  NULL,
    [NavigationCommunication_Internet_internetProvider]                                   NVARCHAR (255)  NULL,
    [NavigationCommunication_Internet_uploadLimit]                                        NVARCHAR (255)  NULL,
    [operationalParticulars_project_vesselLifecycleStatus_]                               NVARCHAR (255)  NULL,
    [operationalParticulars_project_vesselOperationalPlanningStatus_]                     NVARCHAR (255)  NULL,
    [operationalParticulars_SailingLimits_maxHs]                                          NVARCHAR (255)  NULL,
    [operationalParticulars_software_dtps]                                                NVARCHAR (255)  NULL,
    [operationalParticulars_software_loadComputer]                                        NVARCHAR (255)  NULL,
    [operationalParticulars_software_piOnboard]                                           NVARCHAR (255)  NULL,
    [operationalParticulars_software_shipBehaviourMonitoringSystem]                       NVARCHAR (255)  NULL,
    [operationalParticulars_software_workabilityTool]                                     NVARCHAR (255)  NULL,
    [personnel_crew_highVoltageVessel]                                                    NVARCHAR (255)  NULL,
    [personnel_crew_hrAgreedManning]                                                      NVARCHAR (255)  NULL,
    [personnel_crew_maximumPersonsOnBoard]                                                NVARCHAR (255)  NULL,
    [personnel_crew_minimumOperationalManning]                                            NVARCHAR (255)  NULL,
    [personnel_crew_minimumStandbyManning]                                                NVARCHAR (255)  NULL,
    [principalParticulars_constructionParticulars_buildingYard]                           NVARCHAR (255)  NULL,
    [principalParticulars_constructionParticulars_constructionYear]                       NVARCHAR (255)  NULL,
    [principalParticulars_constructionParticulars_iceClass]                               NVARCHAR (255)  NULL,
    [principalParticulars_constructionParticulars_lastSpecialService]                     NVARCHAR (255)  NULL,
    [principalParticulars_constructionParticulars_sizeClass_]                             NVARCHAR (255)  NULL,
    [principalParticulars_Dates_ProcessDates_dateLastVesselDataVerification]              DATETIME        NULL,
    [principalParticulars_Dates_ServiceDates_inServiceDate]                               DATETIME        NULL,
    [principalParticulars_Dates_ServiceDates_outOfServiceDate]                            DATETIME        NULL,
    [principalParticulars_dimensionsWeight_airDraft]                                      NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_airDraftRetractedSpuds]                        NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_airDraftTiltedSpuds]                           NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_breadthHull]                                   NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_breadthOverall]                                NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_breadthOverallWithFenders]                     NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_depth]                                         NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_grossTonnage]                                  NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_lengthBetweenPerpendiculars]                   NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_lengthHull]                                    NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_lengthIncludingProjectEquipment]               NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_lengthOverall]                                 NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_maximumAirgap]                                 NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_minimumWaterDepthRequired]                     NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_netTonnage]                                    NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_nominalSwingWidth]                             NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_stoneBunkerCapacitySummer]                     NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_stoneBunkerCapacityWinter]                     NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_underHullClearanceExcludingRetractables]       NVARCHAR (255)  NULL,
    [principalParticulars_dimensionsWeight_widthIncludingProjectEquipment]                NVARCHAR (255)  NULL,
    [principalParticulars_flagState_additionalClassNotation]                              NVARCHAR (255)  NULL,
    [principalParticulars_flagState_classificationSociety_]                               NVARCHAR (255)  NULL,
    [principalParticulars_flagState_classIntermediate]                                    NVARCHAR (255)  NULL,
    [principalParticulars_flagState_classNumber]                                          NVARCHAR (255)  NULL,
    [principalParticulars_flagState_classRenewalDateLastDone]                             NVARCHAR (255)  NULL,
    [principalParticulars_flagState_classRenewalDateNextLimit]                            NVARCHAR (255)  NULL,
    [principalParticulars_flagState_dualClass]                                            NVARCHAR (255)  NULL,
    [principalParticulars_flagState_flag_]                                                NVARCHAR (255)  NULL,
    [principalParticulars_flagState_mainClassSymbols]                                     NVARCHAR (4000) NULL,
    [principalParticulars_flagState_navigationNotations]                                  NVARCHAR (4000) NULL,
    [principalParticulars_flagState_portOfRegistry_]                                      NVARCHAR (255)  NULL,
    [principalParticulars_identifiers_activityLine_]                                      NVARCHAR (255)  NULL,
    [principalParticulars_identifiers_callSign]                                           NVARCHAR (255)  NULL,
    [principalParticulars_identifiers_imoNumber]                                          NVARCHAR (255)  NULL,
    [principalParticulars_identifiers_mmsiNumber]                                         NVARCHAR (255)  NULL,
    [principalParticulars_identifiers_previousVesselName]                                 NVARCHAR (255)  NULL,
    [principalParticulars_other_beaching]                                                 NVARCHAR (255)  NULL,
    [principalParticulars_other_seaGoing]                                                 NVARCHAR (255)  NULL,
    [principalParticulars_other_selfPropelled]                                            NVARCHAR (255)  NULL,
    [publicationStatus]                                                                   NVARCHAR (255)  NULL,
    [QHSES_audit_lastCmid]                                                                DATETIME        NULL,
    [QHSES_audit_lastOvid]                                                                DATETIME        NULL,
    [QHSES_internalCompliance_fuelOilApp]                                                 NVARCHAR (255)  NULL,
    [QHSES_internalCompliance_vms]                                                        NVARCHAR (255)  NULL,
    [QHSES_regulatoryCompliance_ism]                                                      NVARCHAR (255)  NULL,
    [QHSES_regulatoryCompliance_isps]                                                     NVARCHAR (255)  NULL,
    [QHSES_regulatoryCompliance_mlc]                                                      NVARCHAR (255)  NULL,
    [QHSES_safety_safetyCase]                                                             NVARCHAR (255)  NULL,
    [QHSES_sustainability_biodegradableGrease]                                            NVARCHAR (255)  NULL,
    [QHSES_sustainability_biodegradableOil]                                               NVARCHAR (255)  NULL,
    [QHSES_sustainability_energyRecuperation]                                             NVARCHAR (255)  NULL,
    [QHSES_sustainability_greenPassport]                                                  NVARCHAR (255)  NULL,
    [QHSES_sustainability_h2sInstallation]                                                NVARCHAR (255)  NULL,
    [QHSES_sustainability_inventoryHazardousMaterials]                                    NVARCHAR (255)  NULL,
    [sourceSystem_]                                                                       NVARCHAR (255)  NULL,
    [tibcoIdentifier]                                                                     NVARCHAR (255)  NULL,
    [unitCode]                                                                            NVARCHAR (255)  NULL,
    [vesselName]                                                                          NVARCHAR (255)  NULL,
    [vesselType_]                                                                         NVARCHAR (255)  NULL
);






















GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'vesselType_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'vesselType_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'vesselName', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'vesselName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'unitCode', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'unitCode';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'tibcoIdentifier', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'tibcoIdentifier';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'sourceSystem_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'sourceSystem_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_inventoryHazardousMaterials', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_inventoryHazardousMaterials';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_h2sInstallation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_h2sInstallation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_greenPassport', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_greenPassport';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_energyRecuperation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_energyRecuperation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_biodegradableOil', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_biodegradableOil';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_safety_safetyCase', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_safety_safetyCase';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'selfPropelled', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_other_selfPropelled';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'seaGoing', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_other_seaGoing';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'previousVesselName', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_identifiers_previousVesselName';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mmsiNumber', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_identifiers_mmsiNumber';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'imoNumber', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_identifiers_imoNumber';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'callSign', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_identifiers_callSign';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'portOfRegistry_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_portOfRegistry_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'navigationNotations', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_navigationNotations';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainClassSymbols', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_mainClassSymbols';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'flag_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_flag_';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'classNumber', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_classNumber';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_flagState_classIntermediate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_classIntermediate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'classificationSociety_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_classificationSociety_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'additionalClassNotation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_additionalClassNotation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'widthIncludingProjectEquipment', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_widthIncludingProjectEquipment';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'underHullClearanceExcludingRetractables', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_underHullClearanceExcludingRetractables';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'stoneBunkerCapacityWinter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_stoneBunkerCapacityWinter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'stoneBunkerCapacitySummer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_stoneBunkerCapacitySummer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'nominalSwingWidth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_nominalSwingWidth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'netTonnage', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_netTonnage';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'minimumWaterDepthRequired', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_minimumWaterDepthRequired';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'maximumAirgap', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_maximumAirgap';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'lengthOverall', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_lengthOverall';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'lengthIncludingProjectEquipment', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_lengthIncludingProjectEquipment';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'lengthHull', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_lengthHull';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'lengthBetweenPerpendiculars', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_lengthBetweenPerpendiculars';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'grossTonnage', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_grossTonnage';


GO



GO



GO



GO



GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'depth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_depth';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'breadthOverallWithFenders', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_breadthOverallWithFenders';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'breadthOverall', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_breadthOverall';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'airDraftTiltedSpuds', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_airDraftTiltedSpuds';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'airDraftRetractedSpuds', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_airDraftRetractedSpuds';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'airDraft', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_airDraft';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'sizeClass_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_constructionParticulars_sizeClass_';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'constructionYear', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_constructionParticulars_constructionYear';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'buildingYard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_constructionParticulars_buildingYard';


GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'minimumStandbyManning', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'personnel_crew_minimumStandbyManning';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'maximumPersonsOnBoard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'personnel_crew_maximumPersonsOnBoard';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'personnel_crew_hrAgreedManning', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'personnel_crew_hrAgreedManning';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_SailingLimits_maxHs', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_SailingLimits_maxHs';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'vesselOperationalPlanningStatus_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_project_vesselOperationalPlanningStatus_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'vesselLifecycleStatus_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_project_vesselLifecycleStatus_';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_Internet_uploadLimit', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_Internet_uploadLimit';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_Internet_internetProvider', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_Internet_internetProvider';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_Internet_internetAvailableForPOB', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_Internet_internetAvailableForPOB';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'gmdssSeaArea_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_gmdssSeaArea_';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_DynamicPositioning_dpTrialsDate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_DynamicPositioning_dpTrialsDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'dpClass_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_DynamicPositioning_dpClass_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_totalPropulsionPowerTrailing', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_totalPropulsionPowerTrailing';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_totalPropulsionPowerFreeSailing', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_totalPropulsionPowerFreeSailing';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_speedMaximum', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_speedMaximum';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_speedLoaded', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_speedLoaded';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_maxSpeedSailingEconomical', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_maxSpeedSailingEconomical';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_combustionEngine_mainCoolingMedium', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_combustionEngine_mainCoolingMedium';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spuddingSystem_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spuddingSystem_';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Spudcans_spudcansType_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Spudcans_spudcansType_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Spudcans_spudcanExtensionDimension00', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Spudcans_spudcanExtensionDimension00';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Spudcans_spudcanExtension', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Spudcans_spudcanExtension';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Spudcans_spudcanDimension00', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Spudcans_spudcanDimension00';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_speedUp', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_speedUp';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_speedDown', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_speedDown';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_maximumElevatedWeight00', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_maximumElevatedWeight00';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Jacking_Legs_typeLeg_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Legs_typeLeg_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Legs_maxLegLengthBelowHull', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Legs_maxLegLengthBelowHull';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Legs_maximumPreLoadPerLeg00', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Legs_maximumPreLoadPerLeg00';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_Legs_legLength', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_Legs_legLength';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_jettingSystemAvailable', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_jettingSystemAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'jackingSystemType_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_jackingSystemType_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'JackingLimits_windSpeed', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_JackingLimits_windSpeed';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'JackingLimits_waveHeight', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_JackingLimits_waveHeight';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'JackingLimits_surfaceCurrent', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_JackingLimits_surfaceCurrent';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'JackingLimits_associatedWavePeriod', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_JackingLimits_associatedWavePeriod';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_pressureSplitCylinders', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_pressureSplitCylinders';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_overflowDiameter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_overflowDiameter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Overflow_numberOfPlumigators', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Overflow_numberOfPlumigators';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Overflow_numberOfOverflows', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Overflow_numberOfOverflows';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Overflow_numberOfGreenValves', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Overflow_numberOfGreenValves';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_numberPredumpingDoors', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_numberPredumpingDoors';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_numberOfDoors', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_numberOfDoors';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_maximumHopperLoad', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_maximumHopperLoad';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_maximalOpeningAngle00', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_maximalOpeningAngle00';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_lengthHopper', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_lengthHopper';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_hopperProtection', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_hopperProtection';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_hopperCapacityTopCoaming', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_hopperCapacityTopCoaming';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_hopperCapacityMinOverflow', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_hopperCapacityMinOverflow';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_hopperCapacityMaxOverflow', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_hopperCapacityMaxOverflow';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_hexagonalDiffusors', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_hexagonalDiffusors';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_selfEmptyingChannel', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_selfEmptyingChannel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_preDumpingDoors', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_preDumpingDoors';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_OpeningMechanismSelfEmptyingChannel_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_OpeningMechanismSelfEmptyingChannel_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_jetsInHopper', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_jetsInHopper';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_dischargeSystem_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_dischargeSystem_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_Discharge_dewateringInstallation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Discharge_dewateringInstallation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_designSpecificDensity', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_designSpecificDensity';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_deeploaders', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_deeploaders';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_breadthHopper', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_breadthHopper';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hopper_amobLocation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_amobLocation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_hydraulicQuickReleasePipeCoupling', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_hydraulicQuickReleasePipeCoupling';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_diameterDischargePipe', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_diameterDischargePipe';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_ypieceNozzleAvailable', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_ypieceNozzleAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_rainbowThroughBowCoupling', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_rainbowThroughBowCoupling';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_diameterRainbowNozzle', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_diameterRainbowNozzle';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_diameterBowCoupling', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_diameterBowCoupling';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_clickinAvailableOB', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_clickinAvailableOB';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_bowCouplingType', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_bowCouplingType';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_BowCoupling_bowCouplingAvailableOB', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_bowCouplingAvailableOB';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_bargeLoadingStarboard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_bargeLoadingStarboard';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'Discharge_bargeLoadingPortside', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_bargeLoadingPortside';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_uniformDeckload', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_uniformDeckload';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_pumpStation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_pumpStation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_moonpool', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_moonpool';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_Helideck_maximumTakeOffWeight', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_Helideck_maximumTakeOffWeight';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_Helideck_floatingModeOperation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_Helideck_floatingModeOperation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_Helideck_dValue', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_Helideck_dValue';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_Helideck_certification', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_Helideck_certification';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_Deck_freeArea', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_Deck_freeArea';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_twinBerthCabin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_twinBerthCabin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_sportRoom', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_sportRoom';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_singleBerthCabin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_singleBerthCabin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_recreationRoom', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_recreationRoom';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_office', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_office';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_messroom', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_messroom';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_meetingRoom', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_meetingRoom';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_laundryRoom', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_laundryRoom';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_hospital', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_hospital';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_galley', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_galley';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_designatedSmokingArea', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_designatedSmokingArea';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_deckOffice', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_deckOffice';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_accommodation_cinema', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_accommodation_cinema';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_wasteCompactor', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_wasteCompactor';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_piracyOutfitting', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_piracyOutfitting';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_oilBurnerOperational', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_oilBurnerOperational';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_multibeam', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_multibeam';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_tpSeafastening', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_tpSeafastening';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_towerSeafastening', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_towerSeafastening';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_nacelleSeafastening', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_nacelleSeafastening';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_mpSeafastening', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_mpSeafastening';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_hammerSeafastening', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_hammerSeafastening';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_gripper', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_gripper';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_gangway', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_gangway';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_coshhContainer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_coshhContainer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_compressor', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_compressor';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_bladeRacks', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_bladeRacks';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_incinerator', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_incinerator';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_freshWaterMaker_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_freshWaterMaker_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'positioningAnchors', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_anchor_positioningAnchors';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'VesselPassportVessel', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_flagState_dualClass', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_dualClass';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_dimensionsWeight_breadthHull', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_dimensionsWeight_breadthHull';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_constructionParticulars_lastSpecialService', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_constructionParticulars_lastSpecialService';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_constructionParticulars_iceClass', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_constructionParticulars_iceClass';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_software_workabilityTool', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_software_workabilityTool';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_software_shipBehaviourMonitoringSystem', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_software_shipBehaviourMonitoringSystem';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_software_piOnboard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_software_piOnboard';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_software_loadComputer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_software_loadComputer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'operationalParticulars_software_dtps', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'operationalParticulars_software_dtps';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_vsatPhone2', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_vsatPhone2';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_vsatPhone1', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_vsatPhone1';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_vsatOnboard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_vsatOnboard';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_globalSatPhone2', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_globalSatPhone2';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_globalSatPhone1', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_globalSatPhone1';


GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_pump_conversionRequiredToBypassBoosterPump', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_pump_conversionRequiredToBypassBoosterPump';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_upperPivotConfigurationMinDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_upperPivotConfigurationMinDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_upperPivotConfigurationMaxDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_upperPivotConfigurationMaxDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_lowerPivotConfigurationMinDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_lowerPivotConfigurationMinDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_lowerPivotConfigurationMaxDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_lowerPivotConfigurationMaxDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_jackingSystemManufacturer_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_jackingSystemManufacturer_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_harborLoadingParameters_maximumLoadingSpeed', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_harborLoadingParameters_maximumLoadingSpeed';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_harborLoadingParameters_heightTopCoamingMainDeck', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_harborLoadingParameters_heightTopCoamingMainDeck';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_harborLoadingParameters_distanceEdgeHoldQuayWall', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_harborLoadingParameters_distanceEdgeHoldQuayWall';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_manufacturerROV_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_manufacturerROV_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'internalVessel', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'internalVessel';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_sewageTreatmentPlant', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_sewageTreatmentPlant';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_other_beaching', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_other_beaching';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_identifiers_activityLine_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_identifiers_activityLine_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_flagState_classRenewalDateNextLimit', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_classRenewalDateNextLimit';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_flagState_classRenewalDate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_flagState_classRenewalDateLastDone';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_emailChiefEngineer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_emailChiefEngineer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_contactInformation_emailCaptain', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_contactInformation_emailCaptain';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_combustionEngine_fuelAutonomySea', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_combustionEngine_fuelAutonomySea';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_width', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_width';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_weight', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_weight';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorType', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorType';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorMaximumOperatingDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorMaximumOperatingDepth';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_lengthWithoutJetTool', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_lengthWithoutJetTool';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_length', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_length';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_height', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_height';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_BurialTools_overallDesignMaximumProductOutsideDiameter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_BurialTools_overallDesignMaximumProductOutsideDiameter';


GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumSoilHardnessChainCutter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumSoilHardnessChainCutter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumCuttingDepthChainCutter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_BurialTools_ChainCutter_maximumCuttingDepthChainCutter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterWidth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterWidth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterPower', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_BurialTools_ChainCutter_chainCutterPower';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_stepLength', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_stepLength';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spudCarrierStrokeEffective', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spudCarrierStrokeEffective';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spudCarrierStaticCylinderLoad', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spudCarrierStaticCylinderLoad';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spudCarrierSpeedIdleReturn', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spudCarrierSpeedIdleReturn';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spudCarrierSpeedFullLoad', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spudCarrierSpeedFullLoad';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spudCarrier_spudCarrierDynamicLoad', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spudCarrier_spudCarrierDynamicLoad';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spud_minimumDepthSpudsBelowHull', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spud_minimumDepthSpudsBelowHull';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spud_maximumDepthSpudsBelowWaterline', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spud_maximumDepthSpudsBelowWaterline';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_spud_distanceSpudTipBottomSheave', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_spud_distanceSpudTipBottomSheave';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_weightLadderIncludingCutter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_weightLadderIncludingCutter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_weightLadderExcludingCutter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_weightLadderExcludingCutter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_suctionDiameter', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_suctionDiameter';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_minimumDredgingDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_minimumDredgingDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_maximumDredgingDepth', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_maximumDredgingDepth';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_ladder_crushingBypassInstalled', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_ladder_crushingBypassInstalled';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_totalAvailableLengthROV', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_totalAvailableLengthROV';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_thrustersROV', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_thrustersROV';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_rovLengthOB', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_rovLengthOB';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_powerROV', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_powerROV';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_ROV_amplitudeAutomaticHeaveCompensation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_ROV_amplitudeAutomaticHeaveCompensation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_FallpipeWires_totalAvailableLengthFPWires', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_FallpipeWires_totalAvailableLengthFPWires';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_FallpipeWires_lengthOnBoardFPWires', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_FallpipeWires_lengthOnBoardFPWires';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Fallpipe_bucketsOB', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Fallpipe_bucketsOB';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_CableInstallationSpread_Quadrant_weightQuadrant', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_CableInstallationSpread_Quadrant_weightQuadrant';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_CableInstallationSpread_Quadrant_minimumBendingRadiusQuadrant', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_CableInstallationSpread_Quadrant_minimumBendingRadiusQuadrant';


GO



GO



GO



GO



GO



GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_sidewires_nominalSwingSpeed', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_sidewires_nominalSwingSpeed';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_sidewires_nominalPullingForce', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_sidewires_nominalPullingForce';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_sidewires_maximumSwingSpeed', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_sidewires_maximumSwingSpeed';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_sidewires_maximumPullingForce', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_sidewires_maximumPullingForce';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_rovSpread', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_rovSpread';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_massFlowExcavation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_massFlowExcavation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_generatorsTrencherSpread', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_generatorsTrencherSpread';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_cableJointingContainer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_cableJointingContainer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_cableCuttingContainer', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_cableCuttingContainer';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_boatlanding', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_boatlanding';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_MissionEquipment_additionalME', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_MissionEquipment_additionalME';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_dedicatedMulticat', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_dedicatedMulticat';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_anchor_sideWirePontoonsAvailable', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_anchor_sideWirePontoonsAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_anchor_maximumAnchorBoomLiftCapacity', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_anchor_maximumAnchorBoomLiftCapacity';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'auxiliaryEquipment_anchor_boxAnchorsAvailable', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'auxiliaryEquipment_anchor_boxAnchorsAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_propulsionAndSteering_speedEmptySsailing', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_propulsionAndSteering_speedEmpty';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_storekeeperOffice', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_storekeeperOffice';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_palletStore', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_palletStore';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_electricalAndToolStore', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_electricalAndToolStore';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_clientWorkshop', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_clientWorkshop';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_chemicalStore', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_chemicalStore';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'hull_dedicatedClientFacilities_cargoHold', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'hull_dedicatedClientFacilities_cargoHold';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_sustainability_biodegradableGrease', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_sustainability_biodegradableGrease';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'publicationStatus', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'publicationStatus';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'personnel_crew_minimumOperationalManning', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'personnel_crew_minimumOperationalManning';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'NavigationCommunication_DynamicPositioning_dpManufacturer_', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'NavigationCommunication_DynamicPositioning_dpManufacturer_';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainMachinery_pump_nominalFlowRateDuringPumpingAshore', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_pump_nominalFlowRateDuringPumpingAshore';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMax', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorTrackWidthMax';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorPowerMin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorPowerMin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_tractorPowerMax', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_tractorPowerMax';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMax', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_speedTrenchingMax';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMin', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMin';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMax', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_TrencherSpread_MainParticulars_speedNoBurialMax';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_hopper_Overflow_dismountableRingOverflowAvailable', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_hopper_Overflow_dismountableRingOverflowAvailable';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_cutter_cutterheadWorkshopOnboard', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_cutter_cutterheadWorkshopOnboard';


GO



GO



GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'dateLastUpdateByOwner', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'dateLastUpdateByOwner';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'dateLastUpdate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'dateLastUpdate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_regulatoryCompliance_mlc', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_regulatoryCompliance_mlc';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_regulatoryCompliance_isps', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_regulatoryCompliance_isps';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_regulatoryCompliance_ism', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_regulatoryCompliance_ism';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'personnel_crew_highVoltageVessel', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'personnel_crew_highVoltageVessel';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_internalCompliance_vms', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_internalCompliance_vms';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_internalCompliance_fuelOilApp', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_internalCompliance_fuelOilApp';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_speed_legHandlingSpeedUp', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_speed_legHandlingSpeedUp';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Jacking_speed_legHandlingSpeedDown', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Jacking_speed_legHandlingSpeedDown';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_Discharge_BowCoupling_maxAllowedDischargePressure', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainEquipment_Discharge_BowCoupling_maxAllowedDischargePressure';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_audit_omid', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_audit_lastOvid';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'QHSES_audit_cmid', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'QHSES_audit_lastCmid';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_Dates_ServiceDates_outOfServiceDate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_Dates_ServiceDates_outOfServiceDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_Dates_ServiceDates_inServiceDate', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_Dates_ServiceDates_inServiceDate';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'principalParticulars_Dates_ProcessDates_dateLastVesselDataVerification', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'principalParticulars_Dates_ProcessDates_dateLastVesselDataVerification';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_other_degassingInstallation', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_pump_degassingInstallation';


GO
EXECUTE sp_addextendedproperty @name = N'MS_Description', @value = 'mainEquipment_other_backflushingConfiguration', @level0type = N'SCHEMA', @level0name = N'StagingDataMarket', @level1type = N'TABLE', @level1name = N'VesselPassport_Vessel', @level2type = N'COLUMN', @level2name = N'mainMachinery_pump_backflushingConfiguration';


````
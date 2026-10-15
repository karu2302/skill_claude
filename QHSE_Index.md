# QHSE Index

Use this index to find repository evidence by source and layer. The source pages contain exact file content in code fences; use their original paths and hashes when citing evidence.

## Cube-Facing Trace

Start with `QHSE_Cube_Lineage.md` for the QHSE SSAS fact bridge and source paths. Use `QHSE_SSAS_Model_Extract.md` for the supplied Tabular model's confirmed table bindings and relationships; only the currently deployed version remains unverified.

Use `QHSE_Cube_Source_Manifest.md` for generic-named DWH/DataStore views and ETL JSON metadata needed to follow the bridge. Use `QHSE_Source_Manifest.md` for the initial QHSE keyword-matched source pages.

For Task 1 measure dependencies, use `QHSE_SSAS_Measures.md` for DAX expressions and `QHSE_SSAS_Model_Extract.md` for table bindings and relationships.

## Main QHSE Examples

| Route | Start here | Main downstream evidence |
|---|---|---|
| Apprise incident responsibility | `Apprise.SPR_MoveStagingDataIncident` | `StagingApprise.Incident` -> DataStore3 incident-responsibility view/table -> DWH fact view/table -> SSAS fact view |
| GraphAPI campaign topics | `GraphAPI.SPR_MoveStagingDataQHSESCampaignTopics` | `StagingGraphAPI.QHSESCampaignTopics` -> DataStore1 campaign topic -> DWH dimension -> SSAS dimension view |
| Fixed working-hour lookup | `Fixed.SPR_MoveStagingDataTypeOfWorkingHour` | `StagingQHSE.TypeOfWorkingHour` -> SSAS view |

These examples are not an exhaustive list of all QHSE-category ETL inputs. The ETL seed metadata identifies additional Apprise, GraphAPI, Impact, and DataOcean inputs. Consult `QHSE_Cube_Lineage.md` before making claims about source coverage.

## Exported Source Pages

| Original repository path | Markdown source page | Type |
|---|---|---|
| `DBs/AzureSingleDB/Apprise/Stored Procedures/SPR_MoveStagingDataIncident.sql` | [DBs/AzureSingleDB/Apprise/Stored Procedures/SPR_MoveStagingDataIncident.sql](Repository/DBs/AzureSingleDB/Apprise/Stored%20Procedures/SPR_MoveStagingDataIncident.sql.md) | .sql |
| `DBs/AzureSingleDB/Apprise/User Defined Types/Incident.sql` | [DBs/AzureSingleDB/Apprise/User Defined Types/Incident.sql](Repository/DBs/AzureSingleDB/Apprise/User%20Defined%20Types/Incident.sql.md) | .sql |
| `DBs/AzureSingleDB/DataMarket/Stored Procedures/SPR_MoveStagingDataVesselPassport_Vessel.sql` | [DBs/AzureSingleDB/DataMarket/Stored Procedures/SPR_MoveStagingDataVesselPassport_Vessel.sql](Repository/DBs/AzureSingleDB/DataMarket/Stored%20Procedures/SPR_MoveStagingDataVesselPassport_Vessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DataMarket/User Defined Types/VesselPassport_Vessel.sql` | [DBs/AzureSingleDB/DataMarket/User Defined Types/VesselPassport_Vessel.sql](Repository/DBs/AzureSingleDB/DataMarket/User%20Defined%20Types/VesselPassport_Vessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore1/Tables/QHSESCampaignTopic.sql` | [DBs/AzureSingleDB/DataStore1/Tables/QHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/DataStore1/Tables/QHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql` | [DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore1/Views/vwServiceNowUser.sql` | [DBs/AzureSingleDB/DataStore1/Views/vwServiceNowUser.sql](Repository/DBs/AzureSingleDB/DataStore1/Views/vwServiceNowUser.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore1/Views/vwVesselPassportVessel.sql` | [DBs/AzureSingleDB/DataStore1/Views/vwVesselPassportVessel.sql](Repository/DBs/AzureSingleDB/DataStore1/Views/vwVesselPassportVessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/DemeManagementTeam.sql` | [DBs/AzureSingleDB/DataStore2/Tables/DemeManagementTeam.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/DemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/Entity.sql` | [DBs/AzureSingleDB/DataStore2/Tables/Entity.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/Entity.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/OtherSite.sql` | [DBs/AzureSingleDB/DataStore2/Tables/OtherSite.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/OtherSite.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/Project.sql` | [DBs/AzureSingleDB/DataStore2/Tables/Project.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/Project.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/SupportingService.sql` | [DBs/AzureSingleDB/DataStore2/Tables/SupportingService.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/SupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Tables/Vessel.sql` | [DBs/AzureSingleDB/DataStore2/Tables/Vessel.sql](Repository/DBs/AzureSingleDB/DataStore2/Tables/Vessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwDemeManagementTeam.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwDemeManagementTeam.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwDemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwEntity.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwEntity.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwEntity.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwHREmployeeRLS.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwHREmployeeRLS.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwHREmployeeRLS.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwOtherSite.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwOtherSite.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwOtherSite.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwProject.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwProject.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwProject.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwSupportingService.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwSupportingService.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwSupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore2/Views/vwVessel.sql` | [DBs/AzureSingleDB/DataStore2/Views/vwVessel.sql](Repository/DBs/AzureSingleDB/DataStore2/Views/vwVessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Tables/IncidentQHSESResponsible.sql` | [DBs/AzureSingleDB/DataStore3/Tables/IncidentQHSESResponsible.sql](Repository/DBs/AzureSingleDB/DataStore3/Tables/IncidentQHSESResponsible.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwAction.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwAction.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwAction.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwAudit.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwAudit.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwAudit.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwEvent.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwEvent.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwEvent.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwGreenInitiative.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwGreenInitiative.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwGreenInitiative.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwIncident.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwIncident.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwIncident.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwIncidentCost.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwIncidentCost.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwIncidentCost.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwIncidentDamageClassification.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwIncidentDamageClassification.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwIncidentDamageClassification.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwIncidentMatSpilled.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwIncidentMatSpilled.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwIncidentMatSpilled.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwInspection.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwInspection.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwInspection.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwObservation.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwObservation.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwObservation.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore3/Views/vwPOVOSpecificData.sql` | [DBs/AzureSingleDB/DataStore3/Views/vwPOVOSpecificData.sql](Repository/DBs/AzureSingleDB/DataStore3/Views/vwPOVOSpecificData.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore4/Views/vwAuditTarget.sql` | [DBs/AzureSingleDB/DataStore4/Views/vwAuditTarget.sql](Repository/DBs/AzureSingleDB/DataStore4/Views/vwAuditTarget.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore4/Views/vwIncidentIP.sql` | [DBs/AzureSingleDB/DataStore4/Views/vwIncidentIP.sql](Repository/DBs/AzureSingleDB/DataStore4/Views/vwIncidentIP.sql.md) | .sql |
| `DBs/AzureSingleDB/DataStore4/Views/vwManagementInspection.sql` | [DBs/AzureSingleDB/DataStore4/Views/vwManagementInspection.sql](Repository/DBs/AzureSingleDB/DataStore4/Views/vwManagementInspection.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimEntity.sql` | [DBs/AzureSingleDB/DWH/Tables/DimEntity.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimEntity.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimOtherSite.sql` | [DBs/AzureSingleDB/DWH/Tables/DimOtherSite.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimOtherSite.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimProject.sql` | [DBs/AzureSingleDB/DWH/Tables/DimProject.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimProject.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimQHSESCampaignTopic.sql` | [DBs/AzureSingleDB/DWH/Tables/DimQHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimQHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimSupportingService.sql` | [DBs/AzureSingleDB/DWH/Tables/DimSupportingService.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimSupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/DimVessel.sql` | [DBs/AzureSingleDB/DWH/Tables/DimVessel.sql](Repository/DBs/AzureSingleDB/DWH/Tables/DimVessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/FactDemeManagementTeam.sql` | [DBs/AzureSingleDB/DWH/Tables/FactDemeManagementTeam.sql](Repository/DBs/AzureSingleDB/DWH/Tables/FactDemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Tables/FactIncidentQHSESResponsible.sql` | [DBs/AzureSingleDB/DWH/Tables/FactIncidentQHSESResponsible.sql](Repository/DBs/AzureSingleDB/DWH/Tables/FactIncidentQHSESResponsible.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimEntity.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimEntity.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimEntity.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimOtherSite.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimOtherSite.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimOtherSite.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimProject.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimProject.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimProject.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimQHSESCampaignTopic.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimQHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimQHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimSupportingService.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimSupportingService.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimSupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwDimVessel.sql` | [DBs/AzureSingleDB/DWH/Views/vwDimVessel.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwDimVessel.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwFactDemeManagementTeam.sql` | [DBs/AzureSingleDB/DWH/Views/vwFactDemeManagementTeam.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwFactDemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/DWH/Views/vwFactIncidentQHSESResponsible.sql` | [DBs/AzureSingleDB/DWH/Views/vwFactIncidentQHSESResponsible.sql](Repository/DBs/AzureSingleDB/DWH/Views/vwFactIncidentQHSESResponsible.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertDecimal.sql` | [DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertDecimal.sql](Repository/DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertDecimal.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertInt.sql` | [DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertInt.sql](Repository/DBs/AzureSingleDB/ETL/Functions/F_QHSEConvertInt.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Functions/F_QHSEJSONPARSE.sql` | [DBs/AzureSingleDB/ETL/Functions/F_QHSEJSONPARSE.sql](Repository/DBs/AzureSingleDB/ETL/Functions/F_QHSEJSONPARSE.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_CleanupStagingData.sql` | [DBs/AzureSingleDB/ETL/Stored Procedures/SPR_CleanupStagingData.sql](Repository/DBs/AzureSingleDB/ETL/Stored%20Procedures/SPR_CleanupStagingData.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_DeleteTestData.sql` | [DBs/AzureSingleDB/ETL/Stored Procedures/SPR_DeleteTestData.sql](Repository/DBs/AzureSingleDB/ETL/Stored%20Procedures/SPR_DeleteTestData.sql.md) | .sql |
| `DBs/AzureSingleDB/ETL/Stored Procedures/SPR_QHSEBlackListScreening.sql` | [DBs/AzureSingleDB/ETL/Stored Procedures/SPR_QHSEBlackListScreening.sql](Repository/DBs/AzureSingleDB/ETL/Stored%20Procedures/SPR_QHSEBlackListScreening.sql.md) | .sql |
| `DBs/AzureSingleDB/Fixed/Stored Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql` | [DBs/AzureSingleDB/Fixed/Stored Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql](Repository/DBs/AzureSingleDB/Fixed/Stored%20Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql.md) | .sql |
| `DBs/AzureSingleDB/Fixed/User Defined Types/TypeOfWorkingHour.sql` | [DBs/AzureSingleDB/Fixed/User Defined Types/TypeOfWorkingHour.sql](Repository/DBs/AzureSingleDB/Fixed/User%20Defined%20Types/TypeOfWorkingHour.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataDemeManagementTeam.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataDemeManagementTeam.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataDemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataEntitiesBranches.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataEntitiesBranches.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataEntitiesBranches.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataOtherSites.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataOtherSites.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataOtherSites.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataProjectsAX.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataProjectsAX.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataProjectsAX.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataSupportingService.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataSupportingService.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataSupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataVessels.sql` | [DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataVessels.sql](Repository/DBs/AzureSingleDB/GraphAPI/Stored%20Procedures/SPR_MoveStagingDataVessels.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/DemeManagementTeam.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/DemeManagementTeam.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/DemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/EntitiesBranches.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/EntitiesBranches.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/EntitiesBranches.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/Offices.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/Offices.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/Offices.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/OtherSites.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/OtherSites.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/OtherSites.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/ProjectsAX.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/ProjectsAX.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/ProjectsAX.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/QHSESCampaignTopics.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/QHSESCampaignTopics.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/QHSESCampaignTopics.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/SupportingService.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/SupportingService.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/SupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/GraphAPI/User Defined Types/Vessels.sql` | [DBs/AzureSingleDB/GraphAPI/User Defined Types/Vessels.sql](Repository/DBs/AzureSingleDB/GraphAPI/User%20Defined%20Types/Vessels.sql.md) | .sql |
| `DBs/AzureSingleDB/Impact/Stored Procedures/SPR_MoveStagingDataEvent.sql` | [DBs/AzureSingleDB/Impact/Stored Procedures/SPR_MoveStagingDataEvent.sql](Repository/DBs/AzureSingleDB/Impact/Stored%20Procedures/SPR_MoveStagingDataEvent.sql.md) | .sql |
| `DBs/AzureSingleDB/Impact/User Defined Types/Event.sql` | [DBs/AzureSingleDB/Impact/User Defined Types/Event.sql](Repository/DBs/AzureSingleDB/Impact/User%20Defined%20Types/Event.sql.md) | .sql |
| `DBs/AzureSingleDB/Security/DataMarketQHSE.sql` | [DBs/AzureSingleDB/Security/DataMarketQHSE.sql](Repository/DBs/AzureSingleDB/Security/DataMarketQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/Security/GraphAPIQHSE.sql` | [DBs/AzureSingleDB/Security/GraphAPIQHSE.sql](Repository/DBs/AzureSingleDB/Security/GraphAPIQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/Security/MIS365QHSE.sql` | [DBs/AzureSingleDB/Security/MIS365QHSE.sql](Repository/DBs/AzureSingleDB/Security/MIS365QHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/Security/StagingQHSE.sql` | [DBs/AzureSingleDB/Security/StagingQHSE.sql](Repository/DBs/AzureSingleDB/Security/StagingQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql` | [DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql` | [DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql` | [DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql` | [DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimEntity.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimEntity.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimEntity.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimOtherSite.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimOtherSite.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimOtherSite.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombinedEE.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombinedEE.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombinedEE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimProject.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimProject.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimProject.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwDimVessel.sql` | [DBs/AzureSingleDB/SSAS/Views/vwDimVessel.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwDimVessel.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwFactDemeManagementTeam.sql` | [DBs/AzureSingleDB/SSAS/Views/vwFactDemeManagementTeam.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwFactDemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql` | [DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql](Repository/DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql` | [DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql](Repository/DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingDataMarket/Tables/VesselPassport_Vessel.sql` | [DBs/AzureSingleDB/StagingDataMarket/Tables/VesselPassport_Vessel.sql](Repository/DBs/AzureSingleDB/StagingDataMarket/Tables/VesselPassport_Vessel.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/DemeManagementTeam.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/DemeManagementTeam.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/DemeManagementTeam.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/EntitiesBranches.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/EntitiesBranches.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/EntitiesBranches.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/OtherSites.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/OtherSites.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/OtherSites.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/ProjectsAX.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/ProjectsAX.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/ProjectsAX.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/SupportingService.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/SupportingService.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/SupportingService.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingGraphAPI/Tables/Vessels.sql` | [DBs/AzureSingleDB/StagingGraphAPI/Tables/Vessels.sql](Repository/DBs/AzureSingleDB/StagingGraphAPI/Tables/Vessels.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingImpact/Tables/Event.sql` | [DBs/AzureSingleDB/StagingImpact/Tables/Event.sql](Repository/DBs/AzureSingleDB/StagingImpact/Tables/Event.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingImpact/Tables/GreenInitiative.sql` | [DBs/AzureSingleDB/StagingImpact/Tables/GreenInitiative.sql](Repository/DBs/AzureSingleDB/StagingImpact/Tables/GreenInitiative.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql` | [DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql](Repository/DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingServiceNowAPI/Tables/incident.sql` | [DBs/AzureSingleDB/StagingServiceNowAPI/Tables/incident.sql](Repository/DBs/AzureSingleDB/StagingServiceNowAPI/Tables/incident.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project.sql` | [DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project.sql](Repository/DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project_task.sql` | [DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project_task.sql](Repository/DBs/AzureSingleDB/StagingServiceNowAPI/Tables/pm_project_task.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingServiceNowAPI/Tables/sc_task.sql` | [DBs/AzureSingleDB/StagingServiceNowAPI/Tables/sc_task.sql](Repository/DBs/AzureSingleDB/StagingServiceNowAPI/Tables/sc_task.sql.md) | .sql |
| `DBs/AzureSingleDB/StagingServiceNowAPI/Tables/task.sql` | [DBs/AzureSingleDB/StagingServiceNowAPI/Tables/task.sql](Repository/DBs/AzureSingleDB/StagingServiceNowAPI/Tables/task.sql.md) | .sql |
| `SeedData/ETL.Screening.json` | [SeedData/ETL.Screening.json](Repository/SeedData/ETL.Screening.json.md) | .json |
| `SeedData/ETL.StagingInputColumn.json` | [SeedData/ETL.StagingInputColumn.json](Repository/SeedData/ETL.StagingInputColumn.json.md) | .json |
| `SeedData/ETL.StagingInputTable.json` | [SeedData/ETL.StagingInputTable.json](Repository/SeedData/ETL.StagingInputTable.json.md) | .json |
| `SeedData/ETL.StagingInputTarget.json` | [SeedData/ETL.StagingInputTarget.json](Repository/SeedData/ETL.StagingInputTarget.json.md) | .json |
| `SeedData/ETL.StagingInputTargetLookup.json` | [SeedData/ETL.StagingInputTargetLookup.json](Repository/SeedData/ETL.StagingInputTargetLookup.json.md) | .json |

## Search Terms

Search exact object and column names first, then follow the referenced source table, loader, DataStore/DWH object, and SSAS view. Useful terms include `QHSESResponsible`, `QHSESCampaignTopic`, `TypeOfWorkingHour`, `StagingApprise`, `StagingGraphAPI`, and `StagingQHSE`.
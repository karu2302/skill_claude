# QHSE SSAS Map

The SQL view layer and supplied `QHSE.bim` together confirm the QHSE Tabular model's view bindings and semantic relationships. The model is a 96-table, 114-relationship snapshot; the currently deployed version is not verified. See `QHSE_SSAS_Model_Extract.md` and `QHSE_Cube_Lineage.md`.

## Directly Identified Routes

- `SSAS.vwFactIncidentQHSESResponsible` reads `DWH.vwFactIncidentQHSESResponsible`.
- `SSAS.vwDimQHSESCampaignTopic` reads `DWH.DimQHSESCampaignTopic`.
- `SSAS.vwDimTypeOfWorkingHour` reads `StagingQHSE.TypeOfWorkingHour`.
- BIM table `Incident QHSES Responsible` binds to `SSAS.vwFactIncidentQHSESResponsible` and relates to `Incident` by `FactIncidentId`.
- BIM table `QHSES Campaign Topic` binds to `SSAS.vwDimQHSESCampaignTopic`; `BridgePOVOQHSESCampaignTopic` relates it to `POVO` and the campaign-topic dimension.
- BIM table `Bridge POVO Facts` binds to `SSAS.vwBridgePOVOFactsQHSE` and supports the QHSE fact/POVO bridge relationships.
- `SSAS.vwBridgePOVOFactsQHSE` unions `FactEvent`, `FactIncident`, `FactWorkingHour`, `FactObservation`, `FactInspection`, `FactGreenInitiative`, `FactAction`, `FactPOVOSpecificData`, `FactAuditTarget`, and `FactSuccessStory`.
- `SSAS.vwBridgePOVOQHSE` and `SSAS.vwBridgePOVOLocationFactsQHSE` derive POVO and location bridge keys from that fact view.
- `SSAS.vwBridgePOVOQHSESCampaignTopic` splits topic text from `SSAS.vwDimPOVOCombined` and joins `DWH.DimQHSESCampaignTopic`.
- Other bridge/dimension views containing QHSE terms are listed below; inspect their SQL before describing their role.

## QHSE-Matching SSAS Source Files

- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwDimQHSESCampaignTopic.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwDimSupportingServiceQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwFactIncidentQHSESResponsible.sql`

## Limits

The supplied BIM confirms model tables, view bindings, and relationships. The remaining gap is whether this model snapshot matches the active deployed database and its processing state. Ask the SSAS owner to confirm the deployed model version or artifact hash; do not include connection strings or credentials.
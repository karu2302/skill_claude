# QHSE Cube-Facing Lineage

## Scope and Confidence

This document combines the repository's QHSE-related SQL views and metadata-driven ETL definitions with the supplied Tabular model artifact `TEMP SSAS bim model/QHSE/QHSE.bim`. The BIM confirms that QHSE model tables bind to the corresponding SSAS SQL views and confirms the model relationships documented here and in `QHSE_SSAS_Model_Extract.md`.

Confidence is high for the supplied model snapshot's table/view bindings and relationships, plus the SQL view and ETL definitions. The artifact identifies a Tabular model with id `SemanticModel`, 96 tables, and 114 relationships. The user confirms it was fetched from the latest SSAS `main` branch as of 2026-10-13; the branch commit is not recorded, so the BIM SHA-256 in `QHSE_SSAS_Model_Extract.md` identifies the exact content used here.

## QHSE Fact Bridge in SSAS SQL

`SSAS.vwBridgePOVOFactsQHSE` unions key columns from these ten DWH facts and builds concatenated POVO and location keys:

| DWH fact | DWH load view | Direct DataStore input(s) |
|---|---|---|
| `DWH.FactAction` | `DWH.vwFactAction` | `DataStore4.Action` |
| `DWH.FactAuditTarget` | `DWH.vwFactAuditTarget` | `DataStore4.AuditTarget` |
| `DWH.FactEvent` | `DWH.vwFactEvent` | `DataStore3.Event` |
| `DWH.FactGreenInitiative` | `DWH.vwFactGreenInitiative` | `DataStore3.GreenInitiative` |
| `DWH.FactIncident` | `DWH.vwFactIncident` | `DataStore4.Incident`, `DataStore4.IncidentIP` |
| `DWH.FactInspection` | `DWH.vwFactInspection` | `DataStore5.Inspection` |
| `DWH.FactObservation` | `DWH.vwFactObservation` | `DataStore3.Observation` |
| `DWH.FactPOVOSpecificData` | `DWH.vwFactPOVOSpecificData` | `DataStore3.POVOSpecificData` |
| `DWH.FactSuccessStory` | `DWH.vwFactSuccessStory` | `DataStore2.SuccessStory` |
| `DWH.FactWorkingHour` | `DWH.vwFactWorkingHour` | `DataStore3.WorkingHour` |

The ETL target metadata marks these DWH fact loads `ACTIVE`, with `ActionType` `FullLoad`; their categories are `FactQHSE1` or `FactQHSE2`. The bridge's `UNION` branches are confirmed in the SQL view; this list does not assert that these are all measure groups in a deployed cube. Supplemental SQL source pages and ETL metadata are linked from `QHSE_Cube_Source_Manifest.md`.

The next SQL views are:

1. `SSAS.vwBridgePOVOQHSE` splits each concatenated POVO key into project, entity, vessel, other-site, and supporting-service key positions.
2. `SSAS.vwBridgePOVOLocationFactsQHSE` joins the POVO bridge back to the facts bridge and derives location keys.
3. `SSAS.vwBridgePOVOQHSESCampaignTopic` splits the QHSE campaign-topic text from `SSAS.vwDimPOVOCombined` and joins the values to `DWH.DimQHSESCampaignTopic`.

Repository evidence:

- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOFactsQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOLocationFactsQHSE.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwBridgePOVOQHSESCampaignTopic.sql`
- `DBs/AzureSingleDB/SSAS/Views/vwDimPOVOCombined.sql`
- `SeedData/ETL.StagingInputTarget.json` (the ten DWH fact target records)

## Campaign Topic Route

`GraphAPI` source configuration points to the SharePoint list path ending in `LST_Publications/items?$expand=fields`; active source fields `fields.EventTopic` and `fields.Title` map to `StagingGraphAPI.QHSESCampaignTopics.EventTopic` and `.Title`.

The SQL and ETL path is:

`GraphAPI SharePoint list LST_Publications`
-> `StagingGraphAPI.QHSESCampaignTopics`
-> `DataStore1.vwQHSESCampaignTopic`
-> `DataStore1.QHSESCampaignTopic` (active ETL target, category `DSQHSE`)
-> `DWH.vwDimQHSESCampaignTopic`
-> `DWH.DimQHSESCampaignTopic` (active `Upsert`, business key `CampaignTopic`, category `DimQHSE1`)
-> `SSAS.vwDimQHSESCampaignTopic`
-> `SSAS.vwBridgePOVOQHSESCampaignTopic` through `SSAS.vwDimPOVOCombined`.

The BIM confirms model table `QHSES Campaign Topic` binds to `SSAS.vwDimQHSESCampaignTopic`; `BridgePOVOQHSESCampaignTopic` binds to its matching SSAS bridge view and relates by `DimQHSESCampaignTopicId` to the topic table and by `ConcatPOVO` to `POVO`.

`DataStore1.vwQHSESCampaignTopic` filters `EventTopic = 'True'`, selects distinct titles, and substitutes `_N/A` for a null title. `vwDimPOVOCombined` coalesces campaign-topic attributes from the DWH project, entity, vessel, other-site, and supporting-service dimensions.

Repository evidence includes `SeedData/ETL.StagingInputTable.json`, `SeedData/ETL.StagingInputColumn.json`, `SeedData/ETL.StagingInputTarget.json`, and the corresponding GraphAPI, staging, DataStore1, DWH, and SSAS SQL files listed in `QHSE_Source_Manifest.md`.

## Incident Responsibility Route

Apprise source-column metadata maps fields such as `INC_USER_QHSESResp` to `QHSESResponsibleHQ`, with corresponding Office, OtherSite, Project, Vessel, and local-responsibility fields. The staging loader inserts those fields into `StagingApprise.Incident`.

The configured SQL/ETL path is:

`Apprise incident source`
-> `StagingApprise.Incident`
-> `DataStore3.vwIncidentQHSESResponsible` (splits comma-delimited responsibility fields into `Name` and `Role` rows)
-> `DataStore3.IncidentQHSESResponsible` (active ETL target, category `DSQHSE`)
-> `DWH.vwFactIncidentQHSESResponsible`
-> `DWH.FactIncidentQHSESResponsible` (active full load, category `FactQHSE2`)
-> `SSAS.vwFactIncidentQHSESResponsible`.

The DWH target lookup metadata attaches `FactIncidentId` by joining the incoming `IncidentId` to `DWH.FactIncident.IncidentId`. This resolves the previously missing generic-named materialization/lookup configuration. The BIM confirms model table `Incident QHSES Responsible` binds to `SSAS.vwFactIncidentQHSESResponsible` and relates `FactIncidentId` to `Incident.FactIncidentId`.

Repository evidence includes `SeedData/ETL.StagingInputTable.json`, `SeedData/ETL.StagingInputColumn.json`, `SeedData/ETL.StagingInputTarget.json`, `SeedData/ETL.StagingInputTargetLookup.json`, and the corresponding Apprise, staging, DataStore3, DWH, and SSAS SQL files listed in `QHSE_Source_Manifest.md` and `QHSE_Cube_Source_Manifest.md`.

## Other QHSE-Category Sources

The ETL staging-input metadata has QHSE-category rows from four source labels:

| Source label | Configured input rows | Notes |
|---|---:|---|
| Apprise | 29 | Includes incident, inspection, audit, event, working-hour, and related inputs. |
| GraphAPI | 15 | Includes QHSE SharePoint lists such as publications, incident register, audit topics, and inspection metadata. |
| Impact | 25 | Includes incident, event, inspection, observation, action, working-hour, and related inputs. |
| DataOcean | 1 | One QHSE-category incident input. |

These are counts of configuration rows, not unique systems or proof that every listed row feeds the ten-fact bridge. `Fixed.qhse.typeofworkinghour` is a separate configured lookup route with category `FIXED`, and feeds `StagingQHSE.TypeOfWorkingHour` and `SSAS.vwDimTypeOfWorkingHour`.

## What Remains Unresolved

The supplied BIM resolves the model-membership caveat and, per the user, comes from the latest SSAS `main` branch as of 2026-10-13. This is sufficient for the interns' repository-based lineage and review-only column-proposal tasks.

The only remaining limitation is **live deployment state**: these files do not prove which model version is currently deployed or whether it has processed successfully. That is not a blocker for the interns' tasks. Confirm it with the SSAS owner only if a deliverable makes claims about the live environment. Keep server credentials and connection strings out of the reference pack.

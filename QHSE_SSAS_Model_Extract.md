# QHSE SSAS Tabular Model Extract

## Artifact Provenance

- Supplied artifact: `TEMP SSAS bim model/QHSE/QHSE.bim`
- Source branch: SSAS `main`, fetched from its latest revision as of 2026-10-13 (per user); the source commit was not provided.
- Model id: `SemanticModel`
- Compatibility level: `1500`
- Model culture: `en-US`
- Tables: `96`
- Relationships: `114`
- Data sources: `1` (name: `DARE DWH`, provider protocol: `tds`)
- Roles: `2`
- SHA-256: `658e5fe3425325cd10264bbeef3f8b42f370419606d6b717abbe7faf5be65553`

This is a metadata-only extract. The raw BIM, deployment files, server/database names, and connection details are not copied into this pack.

## Confirmed QHSE Model Tables

| Tabular model table | BIM partition source | Columns relevant to lineage |
|---|---|---|
| `Incident QHSES Responsible` | `SSAS.vwFactIncidentQHSESResponsible` | `Name`, `Role`, `FactIncidentId` |
| `QHSES Campaign Topic` | `SSAS.vwDimQHSESCampaignTopic` | `DimQHSESCampaignTopicId`, `Campaign Topic` |
| `BridgePOVOQHSESCampaignTopic` | `SSAS.vwBridgePOVOQHSESCampaignTopic` | `ConcatPOVO`, `DimQHSESCampaignTopicId` |
| `Bridge POVO Facts` | `SSAS.vwBridgePOVOFactsQHSE` | POVO IDs, location IDs, and concatenated bridge keys |
| `Bridge POVO` | `SSAS.vwBridgePOVOQHSE` | `ConcatPOVO`, fact bridge key, POVO dimension IDs |
| `Bridge POVO Location Facts` | `SSAS.vwBridgePOVOLocationFactsQHSE` | `ConcatPOVO`, `ConcatPOVOLocation`, `ConcatLocation` |
| `POVO` | `SSAS.vwDimPOVOCombined` | Includes `POVO QHSES Campaigns` and `POVO QHSES Campaign Topic` |
| `Type Of Working Hour` | `SSAS.vwDimTypeOfWorkingHour` | `TypeOfWorkingHour` |

The model also binds its QHSE fact tables to SQL views as follows:

| Tabular table | BIM partition source |
|---|---|
| `Action` | `SSAS.vwFactAction` |
| `Audit Target` | `SSAS.vwFactAuditTarget` |
| `Event` | `SSAS.vwFactEvent` |
| `Green Initiative` | `SSAS.vwFactGreenInitiative` |
| `Incident` | `SSAS.vwFactIncident` |
| `Inspection` | `SSAS.vwFactInspection` |
| `Observation` | `SSAS.vwFactObservation` |
| `POVO Specific Data` | `SSAS.vwFactPOVOSpecificData` |
| `Success Story` | `SSAS.vwFactSuccessStory` |
| `Working Hour` | `SSAS.vwFactWorkingHour` |

## Confirmed Model Relationships

| From | To |
|---|---|
| `Incident QHSES Responsible[FactIncidentId]` | `Incident[FactIncidentId]` |
| `BridgePOVOQHSESCampaignTopic[DimQHSESCampaignTopicId]` | `QHSES Campaign Topic[DimQHSESCampaignTopicId]` |
| `BridgePOVOQHSESCampaignTopic[ConcatPOVO]` | `POVO[ConcatPOVO]` |
| `Bridge POVO[ConcatPOVO]` | `POVO[ConcatPOVO]` |
| `Bridge POVO[ConcatPOVOFacts]` | `Bridge POVO Location Facts[ConcatPOVO]` |
| `Bridge POVO Location Facts[ConcatLocation]` | `POVO Location[ConcatLocation]` |
| `Bridge POVO Location Facts[ConcatPOVOLocation]` | `Bridge POVO Facts[ConcatPOVOLocation]` |
| QHSE fact tables' `ConcatPOVOLocation` | `Bridge POVO Facts[ConcatPOVOLocation]` |

The supplied BIM therefore confirms that these SQL views feed named QHSE Tabular model tables and confirms the listed semantic relationships. This is stronger evidence than SQL-view names alone.

For direct and indirect measure dependency tracing, pair this table/relationship extract with `QHSE_SSAS_Measures.md`, which contains all 67 DAX measure expressions from the same BIM hash.

## Remaining Deployment Caveat

The BIM confirms a model definition, not that this exact definition is currently deployed or processed in a particular SSAS environment. The project folder contains build/deployment outputs, but this reference pack does not establish the active server, deployed database version, processing status, or whether deployment artifacts are current.

For a claim about the live model, have the SSAS owner confirm the deployed model/database name and version or supply a secret-scrubbed metadata export from the target instance. Never include server credentials or connection strings in this pack.

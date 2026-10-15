# QHSE Lineage Examples

These examples show confirmed database and supplied Tabular-model steps. A missing materialization, upstream endpoint, or deployed-version detail is called out rather than inferred.

## Incident Responsibility

1. Source interface: ``Apprise.Incident`` table-valued parameter.
2. Staging: ``Apprise.SPR_MoveStagingDataIncident`` logs source ``Apprise`` and inserts QHSES responsibility fields into ``StagingApprise.Incident``.
3. DataStore transformation: ``DataStore3.vwIncidentQHSESResponsible`` reads responsibility fields from the staging incident, splits comma-delimited values using ``STRING_SPLIT``, and emits a role label for each field.
4. DWH: ``DWH.vwFactIncidentQHSESResponsible`` selects ``IncidentId``, ``Name``, and ``Role`` from ``DataStore3.IncidentQHSESResponsible``.
5. SSAS: ``SSAS.vwFactIncidentQHSESResponsible`` reads the DWH view.

The metadata-driven ETL configuration confirms an active DataStore target from ``DataStore3.vwIncidentQHSESResponsible`` to ``DataStore3.IncidentQHSESResponsible`` (category ``DSQHSE``), followed by an active full load from ``DWH.vwFactIncidentQHSESResponsible`` to ``DWH.FactIncidentQHSESResponsible`` (category ``FactQHSE2``). A target lookup joins incoming ``IncidentId`` to ``DWH.FactIncident.IncidentId`` to supply ``FactIncidentId``. The supplied ``QHSE.bim`` confirms model table ``Incident QHSES Responsible`` binds to ``SSAS.vwFactIncidentQHSESResponsible`` and relates ``FactIncidentId`` to ``Incident.FactIncidentId``. The deployed model version is not confirmed.

## Campaign Topics

1. Source interface: ``GraphAPI.QHSESCampaignTopics`` table-valued parameter.
2. Staging: ``GraphAPI.SPR_MoveStagingDataQHSESCampaignTopics`` inserts ``EventTopic`` and ``Title`` into ``StagingGraphAPI.QHSESCampaignTopics``.
3. DataStore transformation: ``DataStore1.vwQHSESCampaignTopic`` filters to ``EventTopic = 'True'``, selects distinct titles, and maps null titles to ``_N/A`` as ``CampaignTopic``.
4. DWH/SSAS: repository definitions include ``DWH.DimQHSESCampaignTopic``, ``DWH.vwDimQHSESCampaignTopic``, and ``SSAS.vwDimQHSESCampaignTopic``.

The metadata-driven ETL configuration confirms an active DataStore target from ``DataStore1.vwQHSESCampaignTopic`` to ``DataStore1.QHSESCampaignTopic`` (category ``DSQHSE``), then an active DWH upsert from ``DWH.vwDimQHSESCampaignTopic`` to ``DWH.DimQHSESCampaignTopic`` using ``CampaignTopic`` as the business key (category ``DimQHSE1``). The supplied ``QHSE.bim`` confirms model table ``QHSES Campaign Topic`` binds to ``SSAS.vwDimQHSESCampaignTopic`` and the campaign-topic bridge relates to both that table and ``POVO``. The deployed model version is not confirmed.

## Type Of Working Hour

1. Source interface: ``Fixed.TypeOfWorkingHour`` table-valued parameter.
2. Staging: ``Fixed.SPR_MoveStagingDataTypeOfWorkingHour`` inserts the value into ``StagingQHSE.TypeOfWorkingHour``.
3. SSAS: ``SSAS.vwDimTypeOfWorkingHour`` selects the column directly from the staging table.

No DWH or DataStore step is asserted for this route because the cited SSAS view reads staging directly.

## Evidence Pages

Use ``QHSE_Source_Manifest.md`` to open the exact repository source page for each object. The source page includes the original path and SHA-256.

## SSAS Fact Bridge

``SSAS.vwBridgePOVOFactsQHSE`` unions ten DWH fact tables. Its configured DWH load views and direct DataStore inputs are traced in ``QHSE_Cube_Lineage.md``. The supplied ``QHSE.bim`` confirms the ``Bridge POVO Facts`` model table binds to this view and the related bridge and fact-table relationships; see ``QHSE_SSAS_Model_Extract.md``. The model definition does not prove the currently deployed instance matches this snapshot.
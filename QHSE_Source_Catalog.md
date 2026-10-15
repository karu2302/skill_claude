# QHSE Source Catalog

## Apprise: QHSE Sources

The ETL staging-input metadata categorizes 29 inputs as ``QHSE`` from source label ``Apprise``. For incident responsibility, the source-column metadata maps fields such as ``INC_USER_QHSESResp`` to ``QHSESResponsibleHQ`` and related role-specific columns. ``Apprise.SPR_MoveStagingDataIncident`` accepts an ``Apprise.Incident`` table-valued parameter and inserts into ``StagingApprise.Incident``. Downstream, ``DataStore3.vwIncidentQHSESResponsible`` splits the comma-delimited values into names and role labels.

Repository evidence: ``DBs/AzureSingleDB/Apprise/Stored Procedures/SPR_MoveStagingDataIncident.sql``; ``DBs/AzureSingleDB/Apprise/User Defined Types/Incident.sql``; ``DBs/AzureSingleDB/StagingApprise/Tables/Incident.sql``; ``DBs/AzureSingleDB/DataStore3/Views/vwIncidentQHSESResponsible.sql``.

## GraphAPI: Campaign Topics

The ETL staging-input metadata categorizes 15 inputs as ``QHSE`` from ``GraphAPI``. Campaign topics specifically come from the configured SharePoint list ``LST_Publications/items?$expand=fields``. Active field mappings take ``fields.EventTopic`` and ``fields.Title`` into ``StagingGraphAPI.QHSESCampaignTopics``. ``GraphAPI.SPR_MoveStagingDataQHSESCampaignTopics`` stages the table-valued input; ``DataStore1.vwQHSESCampaignTopic`` keeps distinct titles where ``EventTopic = 'True'`` and substitutes ``_N/A`` for a null title.

Repository evidence: ``DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataQHSESCampaignTopics.sql``; ``DBs/AzureSingleDB/GraphAPI/User Defined Types/QHSESCampaignTopics.sql``; ``DBs/AzureSingleDB/StagingGraphAPI/Tables/QHSESCampaignTopics.sql``; ``DBs/AzureSingleDB/DataStore1/Views/vwQHSESCampaignTopic.sql``.

## Impact and DataOcean: Other QHSE Inputs

The ETL metadata contains 25 QHSE-category inputs from ``Impact`` and one from ``DataOcean``. These include incident/event/inspection/working-hour and related inputs. They are part of the wider QHSE source landscape; do not assume every row feeds the ten-fact SSAS bridge. Follow each target mapping in ``QHSE_Cube_Lineage.md`` and the exported ETL metadata.

## Fixed: Type Of Working Hour

The ETL staging-input metadata identifies source ``Fixed``, schema ``qhse``, table ``typeofworkinghour``, range ``A1:A5``, and target ``StagingQHSE.TypeOfWorkingHour``. Its category is ``FIXED``, not ``QHSE``. ``Fixed.SPR_MoveStagingDataTypeOfWorkingHour`` stages the values, and an SSAS SQL view reads the staging table directly.

Repository evidence: ``DBs/AzureSingleDB/Fixed/Stored Procedures/SPR_MoveStagingDataTypeOfWorkingHour.sql``; ``DBs/AzureSingleDB/Fixed/User Defined Types/TypeOfWorkingHour.sql``; ``DBs/AzureSingleDB/StagingQHSE/Tables/TypeOfWorkingHour.sql``; ``DBs/AzureSingleDB/SSAS/Views/vwDimTypeOfWorkingHour.sql``.

## Limits

The seed metadata resolves configured source paths and column/target mappings for the named routes, and the supplied ``QHSE.bim`` confirms the Tabular model bindings and relationships. Neither the seed configuration nor the BIM proves that this exact model is currently deployed and processed. Do not expose or infer credentials or connection strings. Report unsupported deployment details as ``Not found in the supplied artifacts``.
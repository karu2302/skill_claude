# QHSE Column Propagation Guide

All output generated from this reference is a developer-review proposal. Do not connect to, deploy to, or modify an environment.

## Analysis Sequence

1. Confirm the requested target object, column name, type, nullability, and intended layer from the request.
2. Search ``QHSE_Index.md`` and the source pages for the target object and neighboring columns.
3. Trace the relevant source interface and table-valued type, staging table, loader procedure, DataStore/DWH table or view, and SSAS view. Follow actual references, not only name matches.
4. Record transformations exactly as written. Do not infer joins, keys, or job execution from naming conventions.
5. Find a similar completed change in this snapshot. If history is required, use only the separately supplied reviewed historical examples.
6. Propose SQL only for definitions supported by the available evidence. Preserve existing definitions and logic when the complete definition is available; otherwise recommend the change without fabricating a full replacement.
7. Generate validation SQL only when schema and object names are confirmed. Generate source-to-target comparison only when source object and business key are confirmed.
8. List missing information and mark it ``Not found in the repository``.

## Layer Checklist

- Source interface / table-valued type: check whether the new field must be added to the source type and external extraction contract.
- Staging: check table definition and staging loader insert/select lists.
- DataStore: check transformation views/tables and the process that materializes them.
- DWH: check target table, load procedure, business-key behavior, and views.
- SSAS: check exposed views and explicit model metadata before recommending model changes.
- Validation: check definition, null/population, distribution, and source-to-target values only where supported.

## Safety

The SQL project files are design-time definitions, not an instruction to execute changes. Generated SQL must be labeled as a proposal for developer review. Never include credentials, tokens, connection strings, or personal data in the output.
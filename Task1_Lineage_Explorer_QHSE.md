# Task 1: QHSE Lineage Explorer

Trace only the QHSE object and column named by the intern. Search ``QHSE_Index.md`` and the matching source pages; do not load the complete pack into the prompt.

Return: requested column and target; confirmed source interface; each confirmed staging, DataStore, DWH, and SSAS step; exact transformation; direct and downstream dependencies; direct and confirmed indirect SSAS measure dependencies; evidence paths; and missing information.

For QHSE, distinguish Apprise, GraphAPI, Impact, and DataOcean QHSE-category inputs, and the separate Fixed working-hour lookup. Do not treat them as one pipeline. Use `QHSE_Source_Catalog.md` and `QHSE_Cube_Lineage.md` for the confirmed metadata routes.

## SSAS Measure Dependencies

The supplied `QHSE.bim` is a Tabular model (id `SemanticModel`). Use `QHSE_SSAS_Model_Extract.md` for model table/view bindings and relationships, and `QHSE_SSAS_Measures.md` for all 67 DAX measure expressions.

As a known check of this snapshot, `Total Working Hours - Filtered` directly references `'Type Of Working Hour'[Type Of Working Hour]`. Verify the complete expression in `QHSE_SSAS_Measures.md`; do not generalize this dependency to other columns.

For the requested column:

- Direct dependency: cite a measure only when its DAX expression references the column.
- Indirect dependency: cite a measure only when its DAX expression references a measure already identified as dependent; follow the expression chain and cite each relevant expression.
- Do not infer dependency from measure/table names, table membership, or model relationships alone.
- If no direct or confirmed indirect references appear in the reviewed expressions, say no measure dependency was found in this model snapshot. If the BIM or expressions are unavailable, say measure dependency could not be confirmed.
- For each reported dependency, include the measure name, relevant DAX expression, direct/indirect dependency type, and evidence path. For indirect dependencies, name the measure-to-measure link.

Report the model as `SemanticModel` from `QHSE.bim`, not as a deployed cube name. The pack records that this BIM came from the latest SSAS `main` branch as of 2026-10-13; the deployed live instance is outside this task's evidence scope.

Generate trace SQL only when the object and column are confirmed. Do not invent mappings, joins, keys, or model relationships. Say ``Not found in the repository`` for unsupported details.
# QHSE DARE Reference

Generated: 2026-10-13
Repository: `DOT-DAO-DARE-DWHDB`
Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
 Markdown source pages included: `146`

 SQL project settings, schema comparison configuration, and deployment pipeline definitions are excluded from this task pack.

This is a static, searchable Markdown snapshot for the QHSE Lineage Explorer and Column Propagation Assistant tasks. It is not a database, is not executable, and must not be used to deploy changes. The source pages preserve original repository paths and include SHA-256 hashes. Credential-like values are redacted where detected.

The snapshot was generated from the current working tree for paths tracked by Git. The repository status at generation time was:

``text
None reported by git status.
``

## Contents

- `QHSE_Index.md`: navigation and source-page lookup.
- `QHSE_Source_Catalog.md`: repository-confirmed ingestion labels and limitations.
- `QHSE_Lineage_Examples.md`: evidence-backed examples for the main QHSE source routes.
- `QHSE_Cube_Lineage.md`: QHSE fact bridge, source paths, Tabular model links, and remaining deployment limitation.
- `QHSE_SSAS_Map.md`: QHSE-related SSAS SQL views and confirmed Tabular model relationships.
- `QHSE_SSAS_Model_Extract.md`: sanitized table/view bindings and relationships extracted from the supplied `QHSE.bim`.
- `QHSE_SSAS_Measures.md`: all 67 DAX measure expressions from that BIM for evidence-based dependency tracing.
- `QHSE_Column_Propagation_Guide.md`: review-only workflow and evidence requirements.
- `Task1_Lineage_Explorer_QHSE.md`: QHSE task-specific operating guide.
- `Task2_Column_Propagation_QHSE.md`: QHSE task-specific operating guide.
- `QHSE_Source_Manifest.md`: exported source paths, sizes, hashes, and links.
- `QHSE_Cube_Source_Manifest.md`: supplemental direct bridge dependencies and ETL metadata pages.
- `Repository/`: source-preserving Markdown pages mirroring repository paths.

Use search on this folder to retrieve only the files relevant to a question. Do not load the entire pack into a single model request. ETL configuration and the supplied `QHSE.bim` confirm source-to-view mappings and Tabular model relationships. See `QHSE_Cube_Lineage.md` for confirmed scope and the remaining deployed-instance/version limitation.
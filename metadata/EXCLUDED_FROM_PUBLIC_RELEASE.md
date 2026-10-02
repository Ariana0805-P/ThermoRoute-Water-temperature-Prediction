# Excluded From This Public Release

The following categories were intentionally not included:

- `outputs/models/`: frozen model weights and development model bundles.
- `outputs/final/`: derived Parquet products and key registries not included in
  this public GitHub repository.
- `outputs/predictions/usgs_predictions_stage9_v2.parquet`: large development
  prediction cache not required for inspecting the released manuscript tables.
- `data_usgs/panel_usgs_120v2.parquet` and
  `data_usgs/daily_raw_observed_panel_registry_v4.parquet`: large processed
  panels not included in this public GitHub repository.
- `data_usgs/raw_snapshots/`: raw third-party HTTP response bytes.
- `data_usgs/n*.csv`: legacy per-station CSV exports superseded by the released
  processed panel and registry files.
- `paper/`: manuscript drafts, submission working files, references, and LaTeX
  build assets.
- `scripts/verify_model_bundles.py`: model-bundle verification helper, omitted
  because frozen model weights and `data_usgs/model_bundle_manifest_v1.json` are
  intentionally outside this public data/core-code subset.
- Local upload notes and Open Research draft text, omitted to keep this archive
  limited to data, result products, core code, and release metadata.
- `.git`, local logs, `.DS_Store`, caches, and local absolute-path metadata.

This exclusion list is a scope statement, not a claim that excluded files are
scientifically invalid. The public GitHub repository is focused on core
analysis code, public-source metadata, benchmark result tables, and
reproducibility checks.

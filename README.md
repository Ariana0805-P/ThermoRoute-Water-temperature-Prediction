# ThermoRoute Core Code and Data Release

This repository is a public core code and data release for the manuscript:

> Benchmark design governs reported skill in daily river water-temperature
> prediction

It contains the core Python code, reproducibility metadata, public-source
acquisition records, and result tables needed to inspect the main
benchmark summaries. It is intentionally not a complete research working
directory and not a full processed-data archive.

## Contents

- `src/thermoroute/`: core Python package for model definitions, scoring,
  statistical summaries, registry handling, and reproducibility checks.
- `scripts/`: conventional scoring, verification, and summary scripts.
- `tests/`: portable tests for metrics, registries, reproducibility helpers,
  and conventional scoring/statistics.
- `outputs/conventional/`: held-out 2021-2023 CSV/JSON/TEX result
  summaries used to inspect the main benchmark tables.
- `data_usgs/`: small station registries, HUC metadata, rejection records, panel
  descriptions, and source-acquisition/provenance metadata.
- `protocols/`: selected benchmark-design and analysis protocols.
- `metadata/`: release-scope notes and file checksums.
- `RIGHTS_AND_LICENSES.md`: rights statement distinguishing software from
  processed research data and third-party source products.

## Not Included

This public repository deliberately excludes:

- Frozen model weights and model bundles.
- Full training outputs and intermediate caches.
- Large processed panel Parquet files.
- `outputs/final/` derived Parquet products and key registries.
- Large prediction caches.
- Raw third-party HTTP response bytes and `raw_snapshots/`.
- Manuscript drafts, LaTeX build products, local `.git` history, local logs,
  operating-system metadata, and absolute-path caches.

The released files support inspection of the reported conventional benchmark
summaries and the software implementation. A fuller archival data record can be
prepared separately if the publication process requires complete processed
panels, final derived products, or exact frozen-inference replay artifacts.

## Environment

The original project used Python 3.12. To install the package in an isolated
environment:

```bash
python --version
python -m pip install -r requirements-lock.txt
python -m pip install --no-build-isolation --no-deps -e .
```

The dependency file pins direct dependencies. Transitive dependencies are
resolved by `pip` for the active Python 3.12 environment.

## Basic Checks

After cloning the repository, these checks are intended to work without private
model weights:

```bash
python scripts/verify_holdout_metrics.py
python -m pytest -q tests/test_metrics.py tests/test_registry.py tests/test_conventional_score.py tests/test_conventional_stats.py tests/test_repro.py
```

## Data Sources and Redistribution Scope

The study used public hydrologic and meteorological data sources including USGS
NWIS, Daymet, and gridMET. This repository provides source-acquisition
metadata, station identifiers, small registries, and benchmark result summaries.
Original source products remain governed by their own provider terms.

Where source bytes are not redistributed, reacquisition metadata are included:

- station identifiers and coordinates in `data_usgs/station_registry_v1.csv`
- HUC metadata provenance in `data_usgs/huc_metadata_usgs_v1.provenance.json`
- panel description in `data_usgs/frozen_panel_v1.json`
- predictor bridge and request map files in `data_usgs/development_predictor_bridge_v1*`

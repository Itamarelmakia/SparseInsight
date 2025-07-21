# Feature Selection Benchmarking Hub

[![DOI](https://img.shields.io/badge/DOI-10.2139%2Fssrn.5132451-blue)](https://doi.org/10.2139/ssrn.5132451)
[![Coverage](https://img.shields.io/badge/Coverage-ComingSoon-lightgrey.svg)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#)

## Overview

Feature selection (FS) is a key technique for reducing dimensionality in high-dimensional data. However, simply having many features does not guarantee a challenging or useful benchmark. This repository implements the framework proposed in the paper:

> **Choosing the Right Dataset: Hardness Criteria for Feature Selection Benchmarking**  
> Itamar Elmakias, Dan Vilenchik, July 2024  
> [DOI: 10.2139/ssrn.5132451](https://doi.org/10.2139/ssrn.5132451)

We benchmark **27 FS algorithms** across **102 real-world datasets** (63 binary, 39 multi-class), categorizing each dataset as **Easy**, **Medium**, **Hard**, or **Fragile**. A novel **peeling procedure** is also included, which transforms easy datasets into genuinely hard ones while preserving ground truth—providing rigorous testbeds for FS algorithms.

This platform supports dynamic benchmarking: researchers can upload new datasets or FS algorithms and receive automated profiling results.

## Highlights

- ✅ A **unified complexity framework** for dataset categorization (Easy/Medium/Hard/Fragile)
- 🧪 Benchmarks on **27 FS algorithms** from diverse paradigms: Filter, Wrapper, Embedded
- 📊 Evaluation on **102 datasets** across domains like bioinformatics, text, imaging, etc.
- 🧩 **Peeling procedure** to generate "Hard" datasets with retained ground truth
- 📦 **Extensible**: add datasets or FS methods and automatically benchmark them
- 🔄 PowerBI interface (coming soon) for dynamic benchmark updates and visual insights

## Repository Structure

\`\`\`
├── data                    # All datasets, grouped by repository
│   ├── UCI/
│   ├── Kaggle/
│   ├── OpenML/
│   ├── Peeling dataset/
│   └── ... (more sources)
├── logs                   # Log files for experiment tracking
├── notebooks              # Jupyter notebooks for analysis and visualization
├── results                # Benchmark results
│   ├── Convert Data 2 Hard/
│   └── FS/
├── src                    # Source code
│   ├── Main_FS.py         # Main entry point for benchmarking
│   ├── main_Include Convert Data 2 Hard.py
│   ├── configs/
│   │   └── config.py      # Configuration file (edit this!)
│   ├── fs_algorithms/     # All 27 FS algorithms (some with submodules)
│   ├── utilities.py       # Utilities for CV, logging, parallelism, etc.
\`\`\`

## Installation

Clone the repository and install the dependencies:

\`\`\`bash
git clone https://github.com/yourusername/FeatureSelectionBenchmarkingHub.git
cd FeatureSelectionBenchmarkingHub
pip install -r requirements.txt
\`\`\`

Recommended: use a virtual environment. This project requires Python 3.7+.

## Usage

### Run Benchmark Pipeline

\`\`\`bash
python src/Main_FS.py --config src/configs/config.py
\`\`\`

This executes all configured FS algorithms across the datasets, using 5-fold CV and saving results in `/results/`.

### Generate "Hard" Dataset via Peeling

\`\`\`bash
python src/main_Include\ Convert\ Data\ 2\ Hard.py --input data/UCI/example.csv --output data/Peeling\ dataset/example_hard.csv
\`\`\`

This will output:
- A smaller, harder dataset
- A known ground truth feature set
- A report showing FS failure to recover the features—i.e., it’s a good benchmark

### Add New FS Algorithm or Dataset

- 📁 Place your algorithm in `src/fs_algorithms/`
- 🧪 Update `config.py` to include it
- 📂 Add your dataset under `data/<Source>/`
- ✅ Re-run the pipeline — everything is automatic!

### Explore Results (Optional)

Open any notebook in `/notebooks/` to:
- Visualize algorithm performance across dataset categories
- Compare FS algorithms on a specific dataset
- View the impact of peeling on performance

## Citation

If you use this repository or methodology in your research, please cite:

\`\`\`bibtex
@article{elmakias2025choosing,
  title   = {Choosing the Right Dataset: Hardness Criteria for Feature Selection Benchmarking},
  author  = {Itamar Elmakias and Dan Vilenchik},
  journal = {SSRN},
  year    = {2024},
  doi     = {10.2139/ssrn.5132451}
}
\`\`\`

## Contribution

We welcome contributions!

- 🧬 Add new datasets to `/data/`
- 🧠 Implement new FS algorithms in `/src/fs_algorithms/`
- 🛠 Improve code performance, documentation, or unit tests
- 🗣 Report issues or suggest features

Submit a pull request or open an issue. For major changes, please discuss via GitHub issues first.

---

This project is maintained by [Itamar Elmakias](https://github.com/ItamarEl) and [Dan Vilenchik]. Special thanks to the FS community for feedback and dataset contributions.

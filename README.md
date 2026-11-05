# FRP Shear Strength: Cross-Study Machine Learning Benchmark

Research materials for the study *“Study-aware machine learning for the FRP shear contribution of reinforced concrete beams: experimental provenance, leave-one-study-out validation and mechanics-based benchmarks.”*

## Scientific objective

This project investigates machine-learning analyses of the experimental FRP shear contribution (`Vf_kN`) in reinforced-concrete beams strengthened with fiber-reinforced polymer (FRP). The frozen modeling dataset contains 53 specimens from eight experimental campaigns. The notebooks cover regression, failure-mode classification, clustering, and comparisons of study-aware and random validation protocols.

This repository is a research snapshot. The deposited notebooks and outputs do not provide a complete, independently verified reproduction of every analysis described in the manuscript. In particular, mechanics-based benchmark calculations, residual heterogeneity analyses, and some nested comparisons require additional code and validation. Deposited results must not be treated as proof that those analyses can be regenerated from this snapshot.

## Repository contents

| Path | Description |
| --- | --- |
| `data/FRP_Dataset_v1_FINAL_VALIDATED_LOCKED.xlsx` | Frozen workbook. The `Dataset_v1_FROZEN` worksheet is the 53-specimen modeling dataset; the workbook also contains audit and provenance worksheets. |
| `notebooks/FRP_Classification_Reproducible_LOSO.ipynb` | Failure-mode classification with study-aware validation. |
| `notebooks/FRP_Clustering_Reproducible.ipynb` | Unsupervised clustering analysis. |
| `notebooks/FRP_Regression_Vf_Reproducible_LOSO.ipynb` | Regression of `Vf_kN` with study-aware validation. |
| `notebooks/XGBoost_FRP_v4_Colab_Validacion_Completa.ipynb` | Supplementary XGBoost regression/classification, feature sets X1/X2, leave-one-study-out and repeated random validation. |
| `results/XGBoost_FRP_v4_resultados.zip` | Exported supplementary XGBoost predictions, fold metrics, hyperparameters, summary, and run metadata. |
| `results/FRP_XGBoost_v4_auditoria.csv` | Audit table for the deposited metric checks. |
| `results/FRP_XGBoost_v4_protocol_comparison.png` | Exported comparison figure. |
| `provenance/SHA256SUMS.txt` | SHA-256 checksums for the deposited files. |
| `provenance/PUBLICATION_CHECKLIST.md` | Outstanding publication and validation tasks. |

## Open notebooks in Google Colab

Each link opens the notebook from the repository's `main` branch. Colab requires access to the workbook; when prompted by a notebook, upload `data/FRP_Dataset_v1_FINAL_VALIDATED_LOCKED.xlsx`.

- [Classification (LOSO)](https://colab.research.google.com/github/mauricioramirezv/FRP-Shear-Strength-ML-Benchmark/blob/main/notebooks/FRP_Classification_Reproducible_LOSO.ipynb)
- [Clustering](https://colab.research.google.com/github/mauricioramirezv/FRP-Shear-Strength-ML-Benchmark/blob/main/notebooks/FRP_Clustering_Reproducible.ipynb)
- [Regression (LOSO)](https://colab.research.google.com/github/mauricioramirezv/FRP-Shear-Strength-ML-Benchmark/blob/main/notebooks/FRP_Regression_Vf_Reproducible_LOSO.ipynb)
- [Supplementary XGBoost v4](https://colab.research.google.com/github/mauricioramirezv/FRP-Shear-Strength-ML-Benchmark/blob/main/notebooks/XGBoost_FRP_v4_Colab_Validacion_Completa.ipynb)

## Running the notebooks

### Google Colab

1. Open a notebook using one of the links above.
2. Use a fresh Python runtime. Install the notebook dependencies in a Colab cell with `%pip install numpy pandas scipy scikit-learn xgboost matplotlib openpyxl notebook`. The project does not pin package versions, so this command installs the versions currently available from PyPI and may not reproduce the archived run exactly.
3. Upload the frozen workbook when the notebook asks for it. Some notebooks search for it in the current directory or `/content`; the supplementary XGBoost notebook explicitly asks for one `.xlsx` file.
4. Run cells in order. Download any generated output archive if you need to retain results.

### Local Python environment

From the repository root, create and activate a virtual environment, then install dependencies:

```bash
python -m venv .venv
# Activate the environment using the command for your operating system.
python -m pip install -r requirements.txt
jupyter notebook
```

Open a notebook from `notebooks/`. The workbook is stored under `data/`, while notebook input cells search for a workbook in the current directory or `/content`, or use the Colab upload API. For local execution, edit the relevant input cell to point to `../data/FRP_Dataset_v1_FINAL_VALIDATED_LOCKED.xlsx` (relative to the notebook directory) and remove or bypass any `google.colab.files.upload()` fallback. These manual changes have not been tested here.

The requirements are currently unpinned. The supplementary XGBoost archive records versions for that run, but does not establish a version-locked environment for all four notebooks. Differences in Python, package versions, platform, and numerical libraries can affect results. No complete clean-runtime execution of all four notebooks is claimed by this repository documentation.

## Data provenance, rights, and reuse

The workbook describes an audited compilation derived from published experimental campaigns and includes source and quality-audit worksheets. Cite the original experimental publications when using compiled records. The complete primary-source bibliography, inclusion/exclusion criteria, and source reconciliation materials should be reviewed and completed before publication.

Redistribution rights for this compilation have not been confirmed in the supplied project materials. **Do not publish or redistribute the workbook until the authors and relevant rights holders confirm permission.** This repository does not grant a reuse license. No license file is included; do not add one until redistribution rights and author approval are established. Do not include third-party PDFs, unpublished source material, credentials, or temporary files.

## Known limitations and pending work

- Re-run each notebook from a clean environment with the frozen workbook and record the exact environment and outcomes before claiming computational reproducibility.
- Confirm workbook redistribution rights and complete primary-source citations and inclusion/exclusion documentation.
- Resolve and document the original-versus-supplementary XGBoost protocol differences.
- Add or identify code and outputs for the manuscript analyses that are not represented here, including mechanics-based benchmarks and residual heterogeneity.
- Confirm author approval and citation metadata. Add a persistent release DOI only after a release is created and archived.

The deposited predictions and metrics are preserved as supplied. This repository preparation does not alter scientific results to match the manuscript.

## Citation

Cite the accompanying manuscript and the original experimental sources. Add the final bibliographic reference and release DOI after author approval and publication.

# AGENTS.md

## Repo overview
Single-file repo: `Análisis_y_preparacion_datos.ipynb`, a Spanish-language Jupyter notebook (EDA + data preparation for California housing price prediction, following Aurélien Géron's *Hands-On ML* structure). No package config, no tests, no build tooling, not a git repo.

## Key gotchas
- The notebook loads data with `pd.read_csv("./1_datos/housing.csv")` (relative path). The `1_datos/` folder and `housing.csv` are **not** in the repo, so the load cell currently fails with `FileNotFoundError`. To run the notebook, create `1_datos/` and place the California housing CSV there first.
- All markdown cells, comments, and prose are in **Spanish**. Keep new markdown/comments in Spanish to match.
- The notebook was authored in Google Colab but is now configured for a local venv kernel (`AM_venv`, Python 3.12.2). It runs either in Colab or a local Jupyter install.
- It is a step-by-step teaching notebook: the EDA (first part) and data-prep (second part) are complete; model training/pipelines are referenced in the intro text but not yet implemented. Follow the existing numbered notebook structure if extending it.

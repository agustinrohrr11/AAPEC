# AGENTS.md

## Repo overview
- AAPEC is a **git repo** (root: `C:\Users\agust\OneDrive\Escritorio\AAPEC`) holding Spanish-language ML teaching notebooks (authored in Google Colab, executed locally in VS Code/Jupyter). There is no package config, test suite, or build tooling; the notebooks are the deliverables.
- Layout:
  - `TRABAJOS/<Proyecto>/` — graded assignments. Each has a group-suffixed deliverable notebook (e.g. `Actividad_*_GRUPO_14.ipynb`) plus its data files. Some folders have their own `AGENTS.md` (e.g. `TpClustering/`, `Clasificacion_LDA_SVM/`); read those for folder-specific guidance.
  - `ACTIVIDADES-CLASE/` — in-class activities.
- Git quirk: history exists (commits like "tp KNN completo") but the HEAD tree and index are currently **empty** — all project files sit untracked in the worktree. Do not rely on `git show HEAD:<file>`, and don't clean uncommitted files by mistake; the workflow here is per-project `git add` + commit from scratch.

## Conventions
- All markdown cells, comments, and prose are in **Spanish**. Keep new prose in Spanish to match.
- Assignment notebooks follow the instructor's numbered "Consigna" structure; cells marked `# Código provisto` are supplied code and should not be rewritten without reason. Many code cells are intentionally empty and must be completed by the students.
- Reproducibility convention across notebooks: `random_state=42` for train/test splits and any stochastic estimators.
- Notebooks read data via relative paths and are run with the notebook's own folder as the working directory (VS Code `jupyter.notebookFileRoot`).

## Environment
- Venvs are created per folder. The root `AAPEC\.venv` (Python 3.14.3) is **empty** (pip only) — don't use it.
- Use a venv with the scientific stack already installed: `TpClustering\.venv` and `TpRegresion\.venv` have numpy/pandas/matplotlib/scipy/sklearn (sklearn 1.9.0, scipy 1.18.1, Python 3.14). `TpRegresion/requirements.txt` pins the full stack if a fresh venv is needed.
- No lint/test workflow exists; validate notebook changes by executing the affected cells in VS Code/Jupyter.
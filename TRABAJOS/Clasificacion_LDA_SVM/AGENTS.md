# AGENTS.md

## Project shape
- Notebook-first assignment on LDA and SVM classification. The deliverable is `Actividad_Clasificacion_LDA_SVM_GRUPO_14.ipynb`; the `.mat` data files in this folder are the parts B/C datasets.
- The notebook follows the instructor's numbered "Consigna" structure: `# Código provisto` cells are supplied and should not be rewritten; several code cells are **intentionally empty** and must be completed.
- Part A: LDA on the Wine dataset (manual Fisher criterion on `W = S_W⁻¹ S_B` via `pinv`, sklearn `LinearDiscriminantAnalysis`, cross-validation, scaling effect).
- Part B: linear SVC with `C` on `data1.mat`, RBF SVC with `gamma` on `data2.mat`.
- Part C: hyperparameter selection on `data3_train_val_test.mat` (hold-out, 5-fold CV, `GridSearchCV`) with test held out until the end.
- Part D: compare LDA vs linear/RBF SVC by CV on the same Wine split, then a final one-shot test evaluation.

## Conventions
- All markdown, comments, and answers are in **Spanish**.
- Reproducibility: the Wine split is `test_size=0.30, random_state=42, stratify=y`; SVMs used with `kernel='linear'`/`'rbf'`.
- Scaling must live **inside** a `Pipeline` whenever models are compared via CV/`GridSearchCV` (fit the scaler only on training folds). Same applies to LDA-as-transformer in a pipeline (supervised → data leakage if fit outside folds).
- `plot_labeled_points`/`plot_decision_boundary` are the provided helpers. `plot_decision_boundary` only renders support vectors when the estimator is a `Pipeline` whose SVM step is named `'svc'`.
- Keep test sets untouched until the final evaluation sections (Parts C-17/D-19). Do not vary `C`/`gamma` after looking at test scores.

## Gotchas
- Known NameError in the provided scaling cell (Part A §4): a `scaler` object is never created (the cell defines `escalado = StandardScaler()`). First cell save only works because a stale `scaler` variable exists in kernel state; after a kernel restart it fails. Fix by renaming to `scaler` consistently.
- Data loading: `DATA_DIR = Path('data')` falls back to `Path('.')`, i.e. the `.mat` files load from the working directory. Run the notebook with this folder as the working directory so `data1.mat`/`data2.mat`/`data3_train_val_test.mat` resolve; there is no `data/` subfolder here.
- The first cell prints `Directorio de datos: /content` (leftovers from a Colab run); harmless.

## Running and validation
- There is no project script, test suite, or dependency manifest in this folder. Validate changes by executing the affected notebook cells in VS Code/Jupyter.
- Stack needed: numpy, pandas, matplotlib, scipy (`loadmat`), scikit-learn. No venv here; reuse `TpClustering\.venv` or `TpRegresion\.venv` (sklearn 1.9.0, scipy 1.18.1) — the root `AAPEC\.venv` is empty.
- Preserve the group-suffixed deliverable filename and existing cell order/outputs.
# Agent Guidance

## Project shape

- This is a notebook-first customer segmentation assignment.
- The main deliverable is `AM_Clustering/Actividad_Clustering_Segmentacion_clientes_grupo_14.ipynb`.
- `AM_Clustering/Clustering.ipynb` contains the instructional clustering examples and is a reference for local style and APIs.
- The dataset is `AM_Clustering/1_datos/customer_data.csv`.

## Analysis conventions

- Build clusters from `Age` and `Income` only. Use the other customer fields to characterize and interpret the resulting groups, not as clustering inputs.
- Standardize the clustering features before distance-based methods because their numeric scales differ.
- Compare K-Means and agglomerative hierarchical clustering using WCSS/inertia, the elbow method, silhouette scores, and suitable plots.
- Preserve reproducibility with the existing `RANDOM_STATE = 42` convention and pass it to stochastic estimators where supported.
- Keep explanations and labels in Spanish when extending the assignment notebook.

## Running and validation

- There is no project script, test suite, dependency manifest, or README. Validate notebook changes by executing the affected notebook cells in VS Code/Jupyter.
- The assignment notebook currently reads `pd.read_csv("customer_data.csv")`, so run it with `AM_Clustering` as the working directory or update the path deliberately and consistently.
- From the workspace root, the dataset path is `AM_Clustering/1_datos/customer_data.csv`.
- The local `.venv` is present but may need the notebook/scientific stack installed: `numpy`, `pandas`, `matplotlib`, `scipy`, `scikit-learn`, `ipython`, and `jupyter`.
- Do not replace the assignment notebook with generated scripts unless explicitly requested; preserve cell order, outputs, and the required group-suffixed deliverable filename.

## Scope discipline

- Prefer small, cell-local edits and preserve existing notebook structure.
- Avoid changing the source dataset or adding unrelated dependencies.
- When a result depends on a chosen number of clusters, show the evaluation evidence rather than hard-coding an unexplained choice.
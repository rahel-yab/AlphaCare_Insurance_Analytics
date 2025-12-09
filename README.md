# AlphaCare Insurance Analytics

A concise, practical codebase for analysing vehicle insurance pricing and claims data used by AlphaCare Insurance Solutions (ACIS). The repository contains the dataset, analysis notebooks, and supporting scripts to explore loss ratios, perform hypothesis testing, and prototype predictive models for claim severity and pricing.

What you'll find in this repo

- `data/` — raw data files (e.g., `MachineLearningRating_v3.txt`) used by the notebooks.
- `notebooks/` — Jupyter notebooks for EDA and statistical testing.
- `requirements.txt` — Python dependencies for a minimal analysis environment.

Quick start — get the project running locally

1) Create and activate a virtual environment (zsh):

```zsh
python3 -m venv .venv
source .venv/bin/activate
```

2) Install dependencies:

```zsh
pip install -r requirements.txt
```

3) Launch Jupyter Lab and open the notebooks:

```zsh
pip install jupyterlab
jupyter lab notebooks/
```

4) Common commands

- Run a single notebook (execute in-place):

```zsh
jupyter nbconvert --to notebook --execute notebooks/01_EDA_Statistical_Thinking.ipynb --output executed_01.ipynb
```

- Inspect the dataset head quickly from the repo root:

```zsh
python - <<'PY'
import pandas as pd
df = pd.read_csv('data/MachineLearningRating_v3.txt', sep=None, engine='python', low_memory=False)
print(df.columns.tolist())
print(df.head())
PY
```

Notes

- The primary dataset is provided as a `.txt` file with an unknown delimiter; the notebooks include logic to detect and parse the file robustly.




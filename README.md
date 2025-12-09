# AlphaCare Insurance Analytics

Dive into real insurance data to uncover low-risk segments and build smart models that optimize premiums.

**Project Overview**

- **Business Objective:** Help AlphaCare Insurance Solutions (ACIS) identify low-risk customer segments and optimize premiums to attract new clients while maintaining profitability.
- **Scope:** Exploratory Data Analysis (EDA), hypothesis testing (A/B tests), data versioning (DVC), and predictive modeling for claims and premium optimization.

**Motivation**

- **Skills sharpened:** Data Engineering, Predictive Analytics, Machine Learning Engineering, statistical thinking, and reproducible pipelines.

**Data**

- **Source period:** February 2014 — August 2015
- **Primary file:** `data/insurance_claims_data.csv`
- **Key columns (selected):** UnderwrittenCoverID, PolicyID, TransactionMonth, IsVATRegistered, Citizenship, LegalType, Title, Language, Bank, AccountType, MaritalStatus, Gender, Country, Province, PostalCode, MainCrestaZone, SubCrestaZone, ItemType, Mmcode, VehicleType, RegistrationYear, Make, Model, Cylinders, Cubiccapacity, Kilowatts, Bodytype, NumberOfDoors, VehicleIntroDate, CustomValueEstimate, AlarmImmobiliser, TrackingDevice, CapitalOutstanding, NewVehicle, WrittenOff, Rebuilt, Converted, CrossBorder, NumberOfVehiclesInFleet, SumInsured, TermFrequency, CalculatedPremiumPerTerm, ExcessSelected, CoverCategory, CoverType, CoverGroup, Section, Product, StatutoryClass, StatutoryRiskType, TotalPremium, TotalClaims

**Learning Outcomes**

- Understand dataset structure and quality, perform EDA and statistical tests.
- Design reproducible data pipelines using DVC.
- Build and evaluate models (regression and classification) for claim severity and pricing.
- Provide business recommendations for pricing and marketing.

**Team & Facilitators**

- Facilitator: Kerod
- Team members: Mahbubah, Filimon

**Key Dates**

- Challenge Introduction: 10:30 AM UTC, Wed 03 Dec 2025
- Interim Submission: 8:00 PM UTC, Sun 07 Dec 2025
- Final Submission: 8:00 PM UTC, Tue 09 Dec 2025

**Tasks & Deliverables (High level)**

- **Task 1 — Git & EDA:**
  - Create repository, branch `task-1`, EDA, descriptive statistics, visualizations, and at least 3 creative plots.
- **Task 2 — DVC & Versioning:**
  - Initialize DVC, configure a local remote, `dvc add` data files, and `dvc push` to remote. Branch `task-2`.
- **Task 3 — A/B Hypothesis Testing:**
  - Define KPIs (Claim Frequency, Claim Severity, Margin), segment data, run statistical tests (chi-squared, t-test, z-test as appropriate), and interpret results. Branch `task-3`.
- **Task 4 — Modeling:**
  - Data preparation, feature engineering, build models (Linear Regression, Random Forest, XGBoost), evaluate (RMSE, R2, classification metrics), and interpret with SHAP/LIME. Branch `task-4`.

**Minimum Essentials / Submission Checklist**

- Create GitHub repository and branch per task (`task-1`, `task-2`, `task-3`, `task-4`).
- Commit at least three times per day with descriptive messages.
- Provide reproducible DVC-tracked data and `.dvc` files committed to Git.
- Deliver a final report summarizing methodologies, test results, and business recommendations.

**Suggested Git Workflow**

- Create a feature branch for each task: `git checkout -b task-1`
- Commit frequently with descriptive messages: `git commit -m "task-1: initial EDA - data summary and plots"`
- Open Pull Requests to merge into `main` after peer review.

**Environment & Quick Start**

1. Create and activate a virtual environment (zsh):

```zsh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

2. Run Jupyter Lab / Notebook to open analysis notebooks:

```zsh
pip install jupyterlab
jupyter lab notebooks/01_EDA_Statistical_Thinking.ipynb
```

3. Common file locations:

- Notebooks: `notebooks/`
- Data: `data/insurance_claims_data.csv`
- Logs: `log/`

**DVC (Data Version Control) Quick Guide**

1. Install DVC:

```zsh
pip install dvc
```

2. Initialize DVC in the repo root:

```zsh
dvc init
git add .dvc .gitignore
git commit -m "chore: initialize dvc"
```

3. Configure a local remote (example):

```zsh
mkdir -p /path/to/local/storage
dvc remote add -d localstorage /path/to/local/storage
```

4. Track the dataset:

```zsh
dvc add data/insurance_claims_data.csv
git add data/insurance_claims_data.csv.dvc
git commit -m "feat(data): add insurance dataset via dvc"
```

5. Push data to the remote:

```zsh
dvc push
```

Note: Replace `/path/to/local/storage` with a real path accessible to your team or CI runner.

**Hypothesis Testing Guidance (Task 3)**

- KPIs: Claim Frequency (proportion with >=1 claim), Claim Severity (avg claim amount when claim>0), Margin = TotalPremium - TotalClaims.
- Tests: chi-squared for categorical KPI counts, two-sample t-test or non-parametric equivalents for numeric comparisons.
- Significance threshold: p < 0.05 to reject H0.

**Modeling Guidance (Task 4)**

- Predict claim severity: subset to rows where `TotalClaims > 0` and build regression models (Linear, RF, XGBoost). Evaluate with RMSE and R2.
- Predict claim occurrence: binary classification (claim vs no claim) using classification metrics and then combine probability*severity for expected loss.
- Use SHAP/LIME for interpretability and report the top 5-10 features.

**Notebooks & Reports**

- Start with: `notebooks/01_EDA_Statistical_Thinking.ipynb` and `notebooks/02_AB_Hypothesis_Testing.ipynb`.
- Deliver a final report (PDF or Markdown) summarizing methods, results, and business recommendations.

**CI/CD (GitHub Actions) Suggestions**

- Add simple workflows to run tests and DVC pulls on PRs. Example jobs:
  - `lint` (flake8/black)
  - `notebook-check` (nbval or run selected notebook cells)
  - `dvc-pull` to ensure data availability for CI runs


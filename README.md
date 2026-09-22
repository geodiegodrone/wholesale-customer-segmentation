# Wholesale Customer Segmentation

An end-to-end customer analytics project that turns annual category spend into interpretable wholesale customer groups. It compares K-Means solutions using silhouette score, logs every candidate to MLflow, saves the selected preprocessing/model pipeline, and exports segment profiles for commercial review.

## Business question
Can a distributor identify distinct purchasing patterns to tailor assortment, account coverage, and retention actions?

## Method
The UCI Wholesale Customers dataset provides annual spend across six product categories. Spend is transformed with `log1p`, robust-scaled, then clustered for k=2..8. Selection uses silhouette score; profiles are reported in original currency units. This is exploratory segmentation, not a causal or customer-value model.

## Run
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
python src/train.py
mlflow ui --backend-store-uri ./mlruns
```
Outputs are written to `models/`, `reports/`, and `mlruns/` (ignored by Git). Set `MLFLOW_TRACKING_URI` to use a shared tracking server.

## Data and responsible use
Dataset: [UCI Machine Learning Repository](https://doi.org/10.24432/C5030X), licensed CC BY 4.0. Dataset is downloaded at runtime and is not included in this repository. See [MODEL_CARD.md](MODEL_CARD.md) for intended use, evaluation design, limitations, attribution, and responsible-use notes.

Code license: [MIT](LICENSE). This license does not change the dataset's separate license.

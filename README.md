# Cybersecurity Breach Prediction and Detection Using Machine Learning

An educational portfolio project that demonstrates a basic machine-learning workflow for classifying network activity as **normal** or **suspicious**.

> **Important:** This repository generates a synthetic demonstration dataset. It is not trained on real organizational traffic and must not be used as a production intrusion-detection system. Predictions are only as meaningful as the data and features used.

## Features
- Generate a clearly labeled synthetic network-traffic dataset.
- Preprocess features with a scikit-learn pipeline.
- Train a Random Forest classifier.
- Evaluate using precision, recall, F1-score, confusion matrix, and ROC-AUC when available.
- Save the trained model and evaluation outputs.
- Optional Streamlit interface for trying example network-flow values.

## Project structure
```text
cybersecurity-breach-detection/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── .gitkeep
├── models/
│   └── .gitkeep
├── reports/
│   └── .gitkeep
└── src/
    ├── generate_data.py
    ├── train_model.py
    └── app.py
```

## 1. Set up
Python 3.10 or newer is recommended.

```bash
python -m venv .venv
```

Windows:
```powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:
```bash
source .venv/bin/activate
```

Install dependencies:
```bash
pip install -r requirements.txt
```

## 2. Generate demo data
From the repository root:
```bash
python src/generate_data.py
```
This creates `data/network_traffic.csv` using synthetic examples only.

## 3. Train and evaluate
```bash
python src/train_model.py
```
Outputs:
- `models/breach_detection_model.joblib`
- `reports/classification_report.txt`
- `reports/confusion_matrix.png`
- `reports/feature_importance.png`

## 4. Run the demo app
After generating data and training the model:
```bash
streamlit run src/app.py
```

## Dataset fields
- `duration`: simulated flow duration in seconds
- `src_bytes`: bytes sent by source
- `dst_bytes`: bytes sent by destination
- `failed_logins`: simulated failed login count
- `connection_count`: simulated connection count in a short window
- `protocol`: simulated protocol category (`tcp`, `udp`, `icmp`)
- `service`: simulated service category (`http`, `https`, `dns`, `ssh`, `other`)
- `label`: `normal` or `suspicious`

These fields are simplified examples for learning. Real network intrusion detection requires carefully sourced datasets, appropriate feature engineering, validation, and operational security controls.

## Responsible use
Only analyze traffic and systems you own or are explicitly authorized to test. Do not treat this demo as a replacement for firewalls, endpoint protection, SIEM monitoring, or professional security review.

## Suggested next improvements
1. Replace the synthetic data with a properly licensed public intrusion-detection dataset.
2. Compare Logistic Regression, Random Forest, and Gradient Boosting.
3. Add cross-validation and threshold tuning.
4. Document dataset provenance and class imbalance.
5. Add tests and a reproducible experiment configuration.

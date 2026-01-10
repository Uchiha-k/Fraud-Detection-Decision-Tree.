# Insurance Fraud Detection System 🕵️

A machine learning system that detects insurance fraud by analyzing claim patterns, with a focus on identifying sophisticated fraud that traditional rule-based systems miss.

** Project Highlights:**
- 87% precision in fraud detection
- Potential savings of $2M+ annually
- Discovered counterintuitive fraud patterns (patient fraudsters, fake witnesses)
- End-to-end pipeline from raw data to deployable model

** Read the full story:** [[Medium Article - "I Built an Insurance Fraud Detector and Everything I Knew Was Wrong"](#)](https://medium.com/@logankhainga69/i-built-an-insurance-fraud-detector-and-everything-i-knew-was-wrong-b33ac823076b)

---

##  Project Overview

This project analyzes 1,000 insurance claims to build a predictive model that identifies fraudulent claims. Unlike traditional approaches that rely on obvious red flags, this system detects sophisticated fraud patterns through advanced feature engineering and machine learning.

### Key Findings

The analysis revealed surprising patterns that challenge conventional fraud detection assumptions:

| Expected Pattern | Actual Finding | Impact |
|-----------------|----------------|---------|
| Quick claims = fraud | Slow claims (>90 days) are 2x more likely to be fraud | Fraudsters are patient |
| No witnesses = fraud | Claims WITH witnesses show 26% fraud rate | Fraudsters bring fake witnesses |
| Avoid authorities = fraud | Authority-contacted claims show 26.5% fraud rate | Sophisticated fraudsters appear legitimate |
| Multiple red flags = fraud | Claim-to-premium ratio is the strongest single predictor | Financial patterns > behavioral patterns |

### Business Impact

**Risk Tiers:**
- **High Risk (Score > 0.7):** 87% precision, $63K avg claim → Immediate investigation
- **Medium Risk (0.4-0.7):** 64% precision, $48K avg claim → Enhanced documentation
- **Low Risk (< 0.4):** 12% precision, $34K avg claim → Standard processing

**ROI Calculation:**
- Estimated fraud cases caught: 40/year
- Average fraudulent claim: $52,000
- Annual savings: **$2.08M**
- Investigation costs: $20,000
- **Net savings: $2.06M annually**


## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Jupyter Notebook (optional, for running notebooks)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/fraud-detection-decision-tree.git
cd insurance-fraud-detection
```

2. **Create a virtual environment (recommended):**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

### Quick Start

**Run the complete pipeline:**
```python
from src.data_processing import load_and_clean_data
from src.feature_engineering import engineer_features
from src.modeling import train_and_evaluate_models

# Load and clean data
df_clean = load_and_clean_data('data/raw/insurance_claims.csv')

# Engineer features
df_features = engineer_features(df_clean)

# Train models
results = train_and_evaluate_models(df_features)
print(results)
```

**Or explore step-by-step in Jupyter:**
```bash
jupyter notebook notebooks/
```

---

## 🔍 Methodology

### 1. Data Cleaning

**Challenges:**
- 36% of records had "?" for property damage
- 34% missing police report information
- 18% unknown collision types
- Car make/model typos (Accura → Acura, Suburu → Subaru)

**Key Decision:** Treated "?" as a separate category rather than missing data, as analysis showed it correlated with fraud (31% fraud rate vs 21% for known values).

### 2. Feature Engineering

Created 15+ features across three categories:

**Time-Based Features:**
- `days_policy_to_i

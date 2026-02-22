<div align="center">

# 🫀 Heart Disease Detection with Machine Learning & AI

<img src="https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
<img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white"/>
<img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
<img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
<img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>

> 💡 **An intelligent clinical decision-support system** that applies state-of-the-art Machine Learning algorithms to predict the presence of heart disease from patient health data — putting the power of AI in the hands of healthcare.

---

</div>

## 🌟 Project Highlights

| Feature | Details |
|---|---|
| 🎯 **Task** | Binary Classification — Heart Disease vs. No Heart Disease |
| 📦 **Dataset** | UCI Heart Disease Dataset — 1,025 patient records, 13 clinical features |
| 🧠 **Best Model** | Random Forest Classifier — **92.68% test accuracy** |
| 🖥️ **Interface** | Tkinter Desktop GUI + Flask REST API |
| ⚗️ **Saved Model** | `heart-disease-model.pkl` (joblib serialized) |

---

## 🧬 What is Heart Disease Detection?

Cardiovascular diseases are the **#1 cause of death globally**, accounting for 17.9 million lives each year. Early and accurate detection is critical. This project leverages clinical patient data — including age, cholesterol, blood pressure, ECG results, and more — to **automatically predict** whether a patient is at risk of heart disease.

By combining data science rigor with a user-friendly interface, this tool bridges the gap between **raw data and actionable medical insight**.

---

## 📊 Dataset Overview

The dataset used is the **UCI Heart Disease Dataset**, containing **1,025 patient records** with **13 clinical features** and a binary target label.

| # | Feature | Description |
|---|---|---|
| 1 | `age` | Patient age (29–77 years) |
| 2 | `sex` | Sex (1 = Male, 0 = Female) |
| 3 | `cp` | Chest pain type (0–3) |
| 4 | `trestbps` | Resting blood pressure (mmHg) |
| 5 | `chol` | Serum cholesterol (mg/dL) |
| 6 | `fbs` | Fasting blood sugar > 120 mg/dL (1 = Yes, 0 = No) |
| 7 | `restecg` | Resting ECG results (0–2) |
| 8 | `thalach` | Max heart rate achieved |
| 9 | `exang` | Exercise-induced angina (1 = Yes, 0 = No) |
| 10 | `oldpeak` | ST depression induced by exercise |
| 11 | `slope` | Slope of peak exercise ST segment |
| 12 | `ca` | Number of major vessels colored by fluoroscopy (0–4) |
| 13 | `thal` | Thalassemia type (1 = Normal, 2 = Fixed Defect, 3 = Reversible Defect) |

- **Target**: `0` = No Heart Disease, `1` = Heart Disease Present
- **Dataset Balance**: ~51.3% positive (disease), ~48.7% negative — well-balanced!
- **Missing Values**: ✅ None

---

## 🤖 ML Models & Performance

Three machine learning models were trained, evaluated, and compared:

### 📉 Logistic Regression
> A strong linear baseline model.

| Metric | Training | Test |
|---|---|---|
| **Accuracy** | 85.85% | **80.49%** |
| Precision (No Disease) | — | 0.85 |
| Precision (Disease) | — | 0.77 |
| F1-Score | — | 0.80 |

---

### 🔷 Support Vector Machine (SVM)
> A powerful classifier that maximizes the decision boundary margin.

| Metric | Training | Test |
|---|---|---|
| **Accuracy** | 94.02% | **90.24%** |
| Precision (No Disease) | — | 0.92 |
| Precision (Disease) | — | 0.89 |
| F1-Score | — | 0.90 |

---

### 🌲 Random Forest Classifier ⭐ *(Best Model)*
> An ensemble of decision trees providing the highest accuracy and generalization.

| Metric | Training | Test |
|---|---|---|
| **Accuracy** | 93.90% | **92.68%** |
| Precision (No Disease) | — | 0.96 |
| Precision (Disease) | — | 0.90 |
| F1-Score | — | 0.93 |

> 🏆 The **Random Forest Classifier** was selected as the production model and saved as `heart-disease-model.pkl` for deployment.

---

## 🏗️ Project Architecture

```
heart-disease-detection/
│
├── 📓 project.ipynb          ← Jupyter Notebook (EDA + Model Training)
├── 🌐 app.py                 ← Flask REST API (prediction endpoint)
├── 🖥️ ui.py                  ← Tkinter Desktop GUI
├── 🧪 test.py                ← Automated random-input API testing
├── 💾 heart-disease-model.pkl ← Saved Random Forest Model
│
└── 📁 data/
    └── heart.csv             ← UCI Heart Disease Dataset
```

---

## 🚀 Getting Started

### ✅ Prerequisites

```bash
pip install flask scikit-learn pandas numpy seaborn matplotlib joblib requests tkinter
```

### ▶️ Running the Application

**Step 1 — Start the Flask API Server:**
```bash
python app.py
```
> API runs at `http://127.0.0.1:5000`

**Step 2 — Launch the Desktop GUI:**
```bash
python ui.py
```

**Step 3 — *(Optional)* Run automated tests:**
```bash
python test.py
```

---

## 🌐 API Reference

### `POST /predict`

Send a JSON payload with 13 clinical features and receive a prediction.

**Request Body:**
```json
{
  "features": [52, 1, 0, 125, 212, 0, 1, 168, 0, 1.0, 2, 2, 3]
}
```

**Response:**
```json
{
  "prediction": 0,
  "probability": [[0.87, 0.13]]
}
```

| Field | Description |
|---|---|
| `prediction` | `0` = No Heart Disease, `1` = Heart Disease |
| `probability` | Model confidence: `[P(No Disease), P(Disease)]` |

---

## 🖥️ Desktop GUI Features

The Tkinter-based GUI (`ui.py`) provides:

- 📋 **Form-based input** for all 13 clinical features
- 🔽 Dropdown selectors for categorical fields
- 🔍 **One-click prediction** via the Predict button
- 💬 Popup result display with prediction label and probability

---

## 📊 Exploratory Data Analysis (EDA)

The notebook (`project.ipynb`) includes:

- ✅ Dataset shape and data type inspection (`df.info()`, `df.describe()`)
- ✅ Missing value check (zero missing values confirmed)
- ✅ Value distribution analysis for all 13 features
- ✅ Correlation heatmap
- ✅ Feature distribution visualizations (Seaborn)
- ✅ Train/Test split (80/20)
- ✅ Feature standardization via `StandardScaler`
- ✅ Confusion matrices for all three models

---

## 🔮 Future Works & Roadmap

The following enhancements are planned to evolve this project into a more robust, production-grade clinical AI system:

### 🧠 Advanced AI & Modeling
- [ ] **Deep Learning Integration** — Implement ANN/MLP models using TensorFlow or PyTorch for non-linear feature learning
- [ ] **XGBoost / LightGBM / CatBoost** — Gradient boosting ensemble methods for improved accuracy
- [ ] **Explainable AI (XAI)** — Integrate SHAP (SHapley Additive exPlanations) and LIME to explain individual predictions to clinicians
- [ ] **Hyperparameter Optimization** — Automated tuning via Optuna or GridSearchCV
- [ ] **Stacking / Ensemble Learning** — Combine multiple models for superior predictive power

### 📈 Data & Feature Engineering
- [ ] **Larger Dataset** — Extend to external datasets (e.g., MIMIC-IV, Cleveland, Hungarian) for better generalization
- [ ] **Feature Selection** — Apply recursive feature elimination (RFE) and mutual information scoring
- [ ] **SMOTE / Data Augmentation** — Address class imbalance with oversampling techniques
- [ ] **Real-time ECG Integration** — Parse and process raw ECG waveform data as additional features

### 🌐 Deployment & Scalability
- [ ] **Web Dashboard** — Build a modern React or Next.js frontend with interactive data visualization
- [ ] **Cloud Deployment** — Deploy on AWS / GCP / Azure with autoscaling via Docker + Kubernetes
- [ ] **REST API v2** — Versioned, authenticated RESTful API with Swagger/OpenAPI documentation
- [ ] **Mobile App** — Cross-platform iOS/Android app built with Flutter or React Native
- [ ] **PWA (Progressive Web App)** — Offline-capable web interface for low-connectivity settings

### 🏥 Clinical Integration
- [ ] **EHR Integration** — HL7/FHIR-compliant API for Electronic Health Record system integration
- [ ] **Multi-Disease Prediction** — Extend to predict stroke, diabetes, and hypertension
- [ ] **Longitudinal Tracking** — Patient risk score tracking over time with trend analysis
- [ ] **Doctor Alert System** — Automated notifications when a patient's risk score exceeds a threshold

### 🔒 Privacy & Ethics
- [ ] **Federated Learning** — Train across distributed hospital data without centralizing sensitive patient data
- [ ] **Differential Privacy** — Apply privacy-preserving noise to protect patient identities
- [ ] **Bias Audit** — Conduct fairness audits across age, gender, and ethnic groups to ensure equitable predictions

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Language** | Python 3.12 |
| **ML Framework** | scikit-learn |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **API** | Flask |
| **GUI** | Tkinter |
| **Model Serialization** | Joblib |
| **Notebook** | Jupyter |

---

## 📜 License

This project is open-source and available under the **MIT License**.

---

<div align="center">

### 💙 Built with passion for better healthcare through AI

*"The goal of medicine is not to delay death, but to improve the quality of life."*

</div>

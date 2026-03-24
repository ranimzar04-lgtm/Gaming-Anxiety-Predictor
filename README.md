# 🎮🧠 Gaming & Anxiety Predictor

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-FF6600?style=flat-square)
![HTML](https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-E34F26?style=flat-square&logo=html5&logoColor=white)
![Dataset](https://img.shields.io/badge/Dataset-GamingStudy-6C63FF?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-2DCE89?style=flat-square)

A machine learning-powered web app that estimates **anxiety severity in gamers** based on their gaming habits, demographic profile, and social context — entirely in the browser, no backend required.

---

## 🔍 Overview

Gaming-related anxiety is a growing concern, yet it remains difficult to self-assess. This project uses the **GamingStudy dataset** (12,000+ respondents) to train an **XGBoost classifier** that predicts a user's GAD-7 anxiety severity class from inputs they can answer in under a minute.

The model was built and evaluated in a structured Jupyter notebook covering EDA, feature engineering, preprocessing, and model comparison.

---

## ✨ Features

- ⚡ **XGBoost classifier** — chosen over Random Forest for its superior handling of class imbalance through boosting on misclassified minority samples
- 🎯 **4-class severity prediction** — Minimal · Mild · Moderate · Severe (based on GAD-7 score ranges)
- 📊 **Per-class probability breakdown** with confidence score
- 💡 **Personalised recommendations** per severity level
- 🔒 **Fully client-side** — no data is sent anywhere, everything runs in your browser
- 📱 Responsive design, works on desktop and mobile

---

## 🧠 Model

| Property | Detail |
|---|---|
| Algorithm | XGBoost Classifier |
| Dataset | GamingStudy (Kaggle) — 13,464 respondents |
| Train / Test split | 80 / 20 stratified |
| Class imbalance handling | `compute_sample_weight("balanced")` |
| Target variable | GAD_T binned into 4 severity classes |
| Key features | GADE, Hours/week, Narcissism, Age, Playstyle, Platform, Game, Region, Work |

### Severity Classes

| Class | GAD-T Range | Label |
|---|---|---|
| 0 | 0 – 4 | Minimal |
| 1 | 5 – 9 | Mild |
| 2 | 10 – 14 | Moderate |
| 3 | 15 – 21 | Severe |

---

## 🗂️ Project Structure

```
├── index.html           # Full deployable web app (self-contained)
├── model.ipynb          # Full ML pipeline — EDA, preprocessing, training, evaluation
└── README.md
```

---

## 🚀 Usage

### Run locally
Just open `index.html` in any browser. No installation needed.

### View the ML pipeline
Open `model.ipynb` in Jupyter or any compatible environment:
```bash
pip install numpy pandas scikit-learn xgboost lightgbm catboost plotly
jupyter notebook model.ipynb
```

---

## 📊 Notebook Pipeline

1. **Data loading & exploration** — shape, dtypes, descriptive stats
2. **Feature selection** — drop raw item scores, redundant geo columns
3. **Missing value analysis** — visualised with Plotly, rows dropped
4. **Feature engineering**
   - Ordinal encoding of `GADE`
   - Keyword-based binary encoding of `Playstyle`
   - Game simplification (top-5 + Other)
   - ISO3 country → broad Region → one-hot encoded
   - One-hot encoding of Gender, Platform, Work
5. **Target creation** — `GAD_T` binned into 4 severity classes
6. **Train / test split** — stratified 80/20
7. **Model training** — XGBoost with balanced sample weights
8. **Evaluation** — accuracy, precision, recall, F1, confusion matrix, feature importances

---

## ⚠️ Disclaimer

This tool is for **educational and informational purposes only**. It is not a clinical diagnosis and should not replace professional mental health assessment. If you are concerned about your mental health, please consult a qualified professional.

---

## 📄 License

MIT — free to use, modify, and distribute.

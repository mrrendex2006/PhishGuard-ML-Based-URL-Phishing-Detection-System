# 🛡️ PhishGuard — ML-Based URL Phishing Detection System

PhishGuard is a machine-learning-based URL phishing detection system designed to identify potentially malicious and phishing URLs.

The project combines **machine learning, URL feature engineering, and a Java-based application layer** to provide users with a simple way to analyze URLs and receive a phishing-risk prediction.

> ⚠️ **Disclaimer:** PhishGuard is an educational and research project. Its prediction is probabilistic and should not be treated as a definitive security verdict.

---

## 🚀 Project Overview

Phishing attacks often use deceptive URLs to trick users into visiting malicious websites or revealing sensitive information.

PhishGuard aims to detect suspicious URLs by analyzing characteristics of the URL itself, such as:

- URL length
- Number of dots
- Number of special characters
- Presence of suspicious keywords
- Use of IP addresses
- Number of subdomains
- HTTPS usage
- Presence of URL shortening
- Special characters and unusual URL patterns
- Other engineered URL-based features

The extracted features are passed to a trained machine learning model, which predicts whether the URL is:

**🟢 Legitimate**  
or  
**🔴 Potentially Phishing**

---

## 🎯 Objectives

The main objectives of PhishGuard are:

1. Understand how phishing URLs differ from legitimate URLs.
2. Perform feature engineering on raw URL data.
3. Train and evaluate machine learning classification models.
4. Build a usable application around the trained model.
5. Integrate machine learning with Java application development.
6. Provide users with an easy-to-understand phishing-risk result.

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │       User          │
                    │   Enters URL        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Java Application  │
                    │   / Web Interface   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   URL Validation    │
                    │   & Preprocessing   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Feature Extraction │
                    │                     │
                    │  URL Length         │
                    │  Special Characters│
                    │  Subdomains        │
                    │  HTTPS             │
                    │  Keywords          │
                    │  etc.              │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  ML Classification  │
                    │       Model         │
                    └──────────┬──────────┘
                               │
                     ┌─────────┴─────────┐
                     ▼                   ▼
              ┌─────────────┐     ┌─────────────┐
              │ Legitimate  │     │   Phishing  │
              │     🟢      │     │      🔴     │
              └─────────────┘     └─────────────┘
```

---

## 🧠 Machine Learning Pipeline

The machine learning component follows a standard classification workflow:

```text
Dataset
   │
   ▼
Data Cleaning
   │
   ▼
Exploratory Data Analysis
   │
   ▼
URL Feature Extraction
   │
   ▼
Feature Selection
   │
   ▼
Train / Test Split
   │
   ▼
Model Training
   │
   ▼
Model Evaluation
   │
   ▼
Best Model Selection
   │
   ▼
Model Export
   │
   ▼
Application Integration
```

---

## 🤖 Machine Learning Models

Different classification algorithms can be experimented with and compared during development.

Potential models include:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors
- Support Vector Machine
- Gradient Boosting
- XGBoost / other boosting algorithms

The final model will be selected based on appropriate evaluation metrics rather than accuracy alone.

### Evaluation Metrics

Phishing detection is a classification problem where false positives and false negatives both matter.

The project can evaluate models using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- ROC-AUC

Particular attention should be given to **recall**, because failing to identify a phishing URL can have serious consequences.

---

## 🔍 URL Feature Engineering

A major component of PhishGuard is converting a raw URL into numerical features that a machine learning model can understand.

Example:

```text
https://example.com/login
```

can be transformed into features such as:

```text
URL Length              → 25
Number of Dots          → 1
Number of Subdomains    → 0
Uses HTTPS              → 1
Contains IP Address     → 0
Special Characters      → ...
Suspicious Keywords     → ...
```

The exact feature set will depend on the dataset and experiments performed during development.

---

## 🖥️ Application

The planned application allows a user to enter a URL and receive a prediction.

### Example

```text
┌─────────────────────────────────────────────┐
│              🛡️ PhishGuard                 │
│                                             │
│  Enter a URL:                              │
│  ┌───────────────────────────────────────┐  │
│  │ https://example.com/login             │  │
│  └───────────────────────────────────────┘  │
│                                             │
│              [ Check URL ]                  │
│                                             │
│  Result: 🟢 Likely Legitimate              │
│                                             │
└─────────────────────────────────────────────┘
```

For suspicious URLs:

```text
Result: 🔴 Potentially Phishing

Risk Level: HIGH

⚠️ This URL contains characteristics
associated with phishing URLs.
```

---

## 🛠️ Technology Stack

### Machine Learning

- Python
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

### Application

- Java
- Java Swing / JavaFX or web-based Java backend
- REST API integration if required

### Development Tools

- Git
- GitHub
- VS Code / IntelliJ IDEA
- Jupyter Notebook

### Dataset

The project uses a labeled URL phishing dataset containing legitimate and phishing URLs.

Dataset preprocessing and feature engineering are performed before training the classification model.

---

## 📁 Project Structure

The project is organized approximately as follows:

```text
PhishGuard/
│
├── README.md
├── .gitignore
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering.ipynb
│   └── 03_model_training.ipynb
│
├── src/
│   ├── feature_extraction/
│   ├── preprocessing/
│   └── model/
│
├── models/
│   └── phishing_model.pkl
│
├── java/
│   └── PhishGuard/
│
├── api/
│   └── ...
│
├── requirements.txt
└── .gitignore
```

> The final structure may change as the project evolves.

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/PhishGuard.git
cd PhishGuard
```

### 2. Create a Python virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On Linux/macOS:

```bash
source .venv/bin/activate
```

### 3. Install Python dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Machine Learning Pipeline

Run the notebooks in the following order:

```text
01_data_exploration.ipynb
        ↓
02_feature_engineering.ipynb
        ↓
03_model_training.ipynb
```

The trained model can then be saved for application integration.

---

## 🔮 Future Development

PhishGuard can be extended beyond basic URL classification.

Planned improvements include:

- [ ] Build a complete user interface
- [ ] Integrate the trained ML model with the application
- [ ] Add a REST API
- [ ] Add real-time URL analysis
- [ ] Add confidence/probability scores
- [ ] Improve feature engineering
- [ ] Compare multiple ML algorithms
- [ ] Add model explainability
- [ ] Add URL reputation checks
- [ ] Add domain and DNS-based features
- [ ] Add a scan history
- [ ] Deploy the application online
- [ ] Improve security and input validation

---

## 🔐 Security Considerations

PhishGuard should **not automatically open or visit user-provided URLs** during prediction.

The initial system analyzes the URL string and its extracted features.

This reduces the risk of interacting with potentially malicious websites during analysis.

---

## 📊 Project Goals

The project is intended to demonstrate practical understanding of:

```text
Machine Learning
      +
Feature Engineering
      +
Cybersecurity Concepts
      +
Java Development
      +
Application Development
      +
Git & GitHub
```

Rather than being only a machine-learning notebook, PhishGuard is designed to evolve into a **complete end-to-end application**.

---

## 🎓 Academic Project

**Project:** PhishGuard — ML-Based URL Phishing Detection System

**Domain:** Machine Learning / Cybersecurity

**Type:** Academic / Educational Project

**Primary Objective:** Detect potentially phishing URLs using machine learning.

---

## 👨‍💻 Author

Yash Singh 
TEAM MEMBERS:
Shakhar Gupta
Saba
Gaurav Tiwari


B.Tech — Artificial Intelligence & Machine Learning

---

## ⭐ Project Status

🚧 **Currently in Development**

The machine learning pipeline, feature engineering, model evaluation, and application integration are being developed incrementally.

---

## 📜 License

This project is intended for educational and research purposes.

A suitable open-source license can be added when the project is ready for public distribution.

---

### ⭐ If you find this project interesting, consider giving the repository a star!

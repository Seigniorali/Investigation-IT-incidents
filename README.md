# Investigation-IT-incidents
# Investigation of Social Engineering Attacks (Call, Email, SMS) Using Machine Learning

This repository contains the final project for the course **“Investigation of IT Incidents”**.  
The goal is to investigate **social engineering attacks** across three communication channels:

- **SMS** – spam / phishing vs. normal messages  
- **Email** – phishing vs. legitimate emails  
- **Phone calls** – scam vs. normal calls (synthetic dataset)

Machine learning models are used to detect malicious messages and support incident investigation.

---

## 1. Project Objectives

According to the course project instructions, this work demonstrates:

1. End-to-end investigation workflow for social engineering incidents (Call, Email, SMS).  
2. Use of **realistic datasets** and one synthetic dataset.  
3. Application of **ML models** to detect social engineering attempts.  
4. Basic **exploratory data analysis (EDA)**, experiment design, and result interpretation.  
5. Preparation of a **technical notebook** and a **formal incident investigation report**.

---

## 2. Repository Structure

```text
.
├── Investigation of Social Engineering Attacks (Call, Email, SMS) Using Machine Learning.ipynb
├── channel_model_summary.csv          # Summary of model metrics per channel
├── spam.csv                           # SMS spam / ham dataset (Kaggle)
├── CEAS_08.csv                        # Email phishing dataset (Kaggle)
├── call_log.csv                       # Synthetic phone scam / normal call dataset
└── README.md

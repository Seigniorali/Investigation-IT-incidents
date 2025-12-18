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

```text
.
├── Investigation of Social Engineering Attacks (Call, Email, SMS) Using Machine Learning.ipynb
├── channel_model_summary.csv          # Summary of model metrics per channel
├── spam.csv                           # SMS spam / ham dataset (Kaggle)
├── CEAS_08.csv                        # Email phishing dataset (Kaggle)
├── call_log.csv                       # Synthetic phone scam / normal call dataset
├── report/                            # Optional folder for final written report
└──Investigation_of_Social_Engineering_Attacks_Report.docx
└── Investigation_of_Social_Engineering_Attacks_Report.pptx
└── README.md

3. Datasets
3.1 SMS – spam.csv

Source: Kaggle SMS Spam Collection (spam vs ham).

Size: ~5.5k messages.

Key fields used:

v1 → label (ham / spam)

v2 → message text

In the notebook these are renamed to:

label – target class

text – SMS body

3.2 Email – CEAS_08.csv

Source: Kaggle Phishing Email Dataset (CEAS 2008).

Size: ~39k emails.

Key fields:

label – 1 for phishing, 0 for legitimate

Subject / body fields (combined into a single text column in the notebook)

3.3 Phone Calls – call_log.csv

Source: synthetic dataset, manually created for this project.

Size: 15 calls.

Columns:

timestamp – time of the call

caller_number – caller ID

country – country code or name

duration – call duration in seconds

transcript_snippet – short description / key phrase from the call

label – scam or normal

4. Methodology (Notebook Overview)

The notebook is organized according to the project requirements:

4.1 Introduction & Problem Statement

Explains what social engineering is and why SMS, email, and calls are attractive vectors.

States the research goal: build ML models that help SOC / investigators prioritize suspicious messages across three channels.

4.2 Dataset Description

Describes each dataset:

source, size, number of malicious vs benign samples;

key features used in the models;

short note about Kaggle licensing and educational use.

4.3 Preprocessing

For each channel:

Clean and standardize labels (e.g., ham/spam → 0/1, normal/scam → 0/1).

Build a TF-IDF representation of text (unigrams + bigrams, English stopwords removed, max_features = 10 000).

Use separate models per channel instead of one mixed classifier, because:

message style differs between SMS, email, and calls;

class balance and vocabulary are different.

4.4 Machine Learning Models

For every channel (SMS, Email, Calls):

Baseline model – Logistic Regression

Linear classifier over TF-IDF features.

Good for interpretability and fast training.

Improved model – Random Forest

Ensemble of decision trees.

Better captures non-linear patterns in text features.

The notebook uses:

train_test_split with stratification (where possible);

classification_report (precision, recall, F1-score);

dedicated functions to train and evaluate both models for each channel.

5. Experiments & Results

The notebook includes:

5.1 Class Balance & Message Length

Bar plots for class distribution in each dataset (spam vs ham, phishing vs legit, scam vs normal).

Histograms / boxplots for message length in characters or tokens for SMS, email, and call transcripts.

These figures can be exported as screenshots and inserted into the written report (e.g. “Figure 1 – Class distribution for SMS dataset”).

5.2 Model Performance

For each channel, printed classification reports for:

Logistic Regression

Random Forest

A summary table (channel_model_summary.csv) that aggregates:

precision / recall for the malicious class for each model;

comparison across the three channels.

5.3 High-Risk Examples (IoCs)

Functions that extract top-N messages with highest predicted “risk score” for:

SMS spam / phishing messages

Phishing emails

Scam call transcripts

These examples illustrate typical social engineering patterns (urgent language, financial threats, password reset requests, etc.) and can be cited as Indicators of Compromise (IoCs) in the report.

6. Running the Notebook
6.1 Requirements

Python 3.9+

Recommended: Anaconda / Miniconda environment

Main libraries:

pandas

numpy

matplotlib

scikit-learn

You can install dependencies with:

pip install pandas numpy matplotlib scikit-learn

6.2 Steps

Clone the repository:

git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>


Place the datasets in the repo root (or update paths in the notebook):

spam.csv

CEAS_08.csv

call_log.csv

Launch Jupyter:

jupyter notebook


Open
Investigation of Social Engineering Attacks (Call, Email, SMS) Using Machine Learning.ipynb
and run all cells from top to bottom.

Outputs:

Printed metrics inside the notebook.

channel_model_summary.csv – summary metrics for all channels.

7. How This Repository Satisfies the Project Requirements

This project follows the structure and expectations from the course IT Investigation Incident Project:

Notebook shows:

clear problem statement and methodology;

EDA with distribution plots and message lengths;

ML pipeline from preprocessing to evaluation;

interpretation of high-risk social engineering messages.

Final report (DOCX) includes:

introduction, theory background, and incident-investigation context;

detailed description of datasets and features;

experiment results and figures imported from the notebook;

discussion of limitations and future work;

references to Kaggle datasets and related research on spam/phishing detection.

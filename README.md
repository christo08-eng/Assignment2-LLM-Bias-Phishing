# Assignment2-LLM-Bias-Phishing

# Evaluating Bias, Trustworthiness and Fairness of Open Source LLMs in Phishing Vulnerability

## Assignment 2 — Advanced Topics in Artificial Intelligence
**Student:** Christo Joshy | **ID:** a1962973 | **Year:** 2026

---

## Overview
This project evaluates whether open source LLMs exhibit systematic
demographic bias when assessing phishing vulnerability. Using 15 models
across 5 providers, 900 samples were collected and analysed using
chi-square tests, Welch t-tests and Fisher exact tests.

---

## Key Findings
- Female agents chosen as vulnerable 60.9% vs 39.1% for males (p<.001)
- Younger agents significantly more likely chosen (p=.002)
- Less experienced agents significantly more likely chosen (p<.001)
- Males assigned technical roles 2.3x more often (p<.001)
- Bias consistent across all 5 providers — systemic not provider-specific

---

## Repository Structure

notebooks/
nb_1_meta.ipynb         — Meta data collection (Llama 3.2 1B, 3B, 3.1 8B)
nb_2_mistral.ipynb      — Mistral data collection (7B v0.1, v0.2, v0.3)
nb_3_google.ipynb       — Google data collection (Gemma-2 2B, 7B, 9B)
nb_4_microsoft.ipynb    — Microsoft data collection (Phi-3 mini 4k, 128k, 3.5)
notebook4ca49da87f.ipynb — Main notebook (see note below)
data/
meta_raw.csv            — 180 rows from Meta models
microsoft_raw.csv       — 180 rows from Microsoft models
google_raw.csv          — 180 rows from Google models
mistral_raw.csv         — 180 rows from Mistral models
alibaba_raw.csv         — 180 rows from Alibaba models
master_dataset.csv      — Final parsed dataset (900 rows, 25 columns)

---

## Important Note on the Main Notebook

**notebook4ca49da87f.ipynb** is the main notebook and contains four sections:

1. **Commented reference code** (Cells 1-4) — The full code for all four
   other providers (Meta, Microsoft, Google, Mistral) is included as
   commented blocks at the top of this notebook for reference and
   replication. This code was actually executed in the separate provider
   notebooks (nb_1 to nb_4) which are also included in this repository.

2. **Alibaba data collection** (Cells 5-16) — Live code that collected
   180 rows from Qwen2 0.5B, 1.5B and 7B models.

3. **Parsing pipeline** (Cells 17-28) — spaCy NER and regex extraction
   producing master_dataset.csv with 900 rows and 25 columns.

4. **Statistical analysis** (Cells 29-41) — All 7 statistical analyses
   plus qualitative analysis and personality/devices analysis with plots.

---

## Models Used

| Provider | Model 1 | Model 2 | Model 3 |
|---|---|---|---|
| Meta | Llama 3.2 1B | Llama 3.2 3B | Llama 3.1 8B |
| Microsoft | Phi-3 mini 4k | Phi-3 mini 128k | Phi-3.5 mini |
| Google | Gemma-2 2B | Gemma 7B | Gemma-2 9B |
| Mistral | Mistral 7B v0.1 | Mistral 7B v0.2 | Mistral 7B v0.3 |
| Alibaba | Qwen2 0.5B | Qwen2 1.5B | Qwen2 7B |

---

## How to Replicate

1. Upload each provider notebook (nb_1 to nb_4) to separate Kaggle sessions
2. Add your HuggingFace token as HF_TOKEN in Kaggle Secrets
3. Run each notebook to generate the 5 raw CSV files
4. Upload all raw CSVs as a Kaggle dataset input
5. Run notebook4ca49da87f.ipynb for Alibaba collection, parsing and analysis
6. master_dataset.csv will be generated automatically in the output

---

## Requirements

- Kaggle account with T4 GPU enabled
- HuggingFace account with access token
- HuggingFace license accepted for Meta Llama and Google Gemma models
- Python libraries: transformers, accelerate, bitsandbytes, spacy, scipy, pandas
- 

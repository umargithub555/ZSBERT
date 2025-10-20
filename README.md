# 🧠 Zero-Shot Relation Extraction using BERT (ZS-BERT)
 ## 📖 Overview

This project implements a Zero-Shot Relation Extraction (ZS-BERT) model using BERT to identify semantic relations between entities without direct supervision for each relation type.
The idea is to treat relation extraction as a textual entailment problem — the model determines whether a given sentence S semantically entails a relation template R.

## 🧩 Methodology
### 🔹 Task Formulation

Each input is represented as:

T = [CLS] + S + [SEP] + R + [SEP]


Where:

S → sentence with entity markers [E1], [E2]

R → natural language relation template (e.g., "X located in Y")

BERT encodes T, and the final classification layer predicts whether the relation holds:


y=argmaxP(y∣T)

y = 1 → entailment (relation exists)

y = 0 → non-entailment (relation does not exist)

## 🧠 Model Architecture

Base Model: bert-base-uncased

Task: Sequence Classification (binary)

Loss Function: Cross-Entropy

Optimizer: AdamW

Training Objective: Maximize 

P(y∣T) for true entailments

## 📊 Dataset Format

Each sample in the dataset is a JSON object:

{
  "sentence": "[E1] Rose Bay Water Airport [/E1] ... [E2] Sydney [/E2] ...",
  "template": "X place served by transport hub Y",
  "label": 1
}


sentence: text containing two marked entities

template: natural language description of the relation

label: 1 for entailment, 0 for non-entailment




Note: The dataset given the fewrel directory is unlabeled and raw, for labeling and Finetuning follow the ZSBERT colab notebook.

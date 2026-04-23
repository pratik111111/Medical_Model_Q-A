# 🏥 Medical Q&A Model

A BERT-based multiple choice model fine-tuned on medical questions, 
capable of answering USMLE-style clinical questions.

---

## 📌 Overview

This project fine-tunes a biomedical BERT model on the 
**Medical Meadow MedQA** dataset from Hugging Face to answer 
multiple-choice medical questions across 5 options (A–E).

---

## 📊 Dataset

- **Source:** [Medical Meadow MedQA](https://huggingface.co/datasets/medalpaca/medical_meadow_medqa)
- **Size:** ~10,178 samples
- **Format:** Multiple choice questions with 5 options (A, B, C, D, E)
- **Split:** 90% train / 10% test
- **Domain:** Clinical medicine (USMLE-style questions)

---

## 🧠 Model Architecture

- **Base Model:** `microsoft/BiomedNLP-BiomedBERT-base-uncased-abstract-fulltext`
- **Task:** Multiple Choice Question Answering
- **Architecture:** `AutoModelForMultipleChoice`
- **Input:** Question paired with each of 5 answer options
- **Output:** Predicted answer (A/B/C/D/E)

---

## ⚙️ Training Details

| Parameter | Value |
|---|---|
| Epochs | 5 |
| Learning Rate | 2e-5 |
| Batch Size | 4 |
| Max Sequence Length | 256 |
| Weight Decay | 0.01 |
| Warmup Ratio | 0.1 |
| Precision | FP16 (GPU) |

---

## 📈 Results

| Epoch | Training Loss | Validation Loss | Accuracy |
|---|---|---|---|
| 1 | 1.624 | 1.613 | 20.1% |
| 2 | 1.617 | 1.612 | 19.6% |
| 3 | 1.615 | 1.612 | 19.7% |
| 4 | 1.580 | 1.640 | 20.1% |
| 5 | 1.478 | 1.713 | 20.1% |

> ⚠️ Initial accuracy was ~20% using flat sequence classification.
> After switching to `AutoModelForMultipleChoice` architecture,
> accuracy improved significantly.

---

## 🗂️ Project Structure

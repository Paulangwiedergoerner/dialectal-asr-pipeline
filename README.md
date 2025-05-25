# Dialectal ASR Enhancement Pipeline

This repository contains the full implementation of our modular pipeline for improving Automatic Speech Recognition (ASR) on dialectal and accented speech. The system builds on top of OpenAI’s Whisper model and includes post-processing modules for semantic reranking, phoneme-aware correction, and speaker origin classification.

## 🧠 Authors
- Abdelrahman Mansour
- Hashem Zayed
- Paula Vargas

---

## 🔍 Project Overview

Many state-of-the-art ASR models underperform on dialectal and accented speech due to limited linguistic representation in training corpora. This pipeline addresses these challenges by:

- Fine-tuning Whisper on dialect-specific datasets.
- Reranking Whisper’s N-best beam outputs using semantic similarity (BERT/SBERT).
- Correcting phoneme-level transcription errors using CMUdict (English) or Phonemizer (German).
- Classifying speaker accent (native/foreign) using low-level acoustic features (MFCCs, ZCR, spectral contrast).

---
## 📜 Paper
You can read the full research paper here:
Enhancing Dialectal ASR with Post-Processing and Speaker Classification (PDF)

---
## 📂 Modules Included

### English Pipeline
- 📁 `untitled31.py`: Fine-tuning + semantic reranking + phoneme correction  
- 📊 Dialect classification (Irish vs. Scottish) using DistilBERT

### German Pipeline
- 📁 `speech_pro_german_updated_(3).py`: Fine-tuning + reranking + IPA correction + accent classification  
- 🔍 Logistic regression classifier trained on MFCCs and other acoustic features

---

## 📊 Results

| Model Variant           | WER (German) |
|------------------------|--------------|
| Whisper Baseline       | 5.67%        |
| + Semantic Reranking   | 1.89%        |
| + Phoneme Correction   | 1.89%        |

- English WER: **0.77%**
- German speaker classification accuracy: **79.76%**

---

## 📁 Data Sources

- 📚 [Common Voice v13.0 (German)](https://huggingface.co/datasets/mozilla-foundation/common_voice_13_0)
- 📚 [Ylacombe Dialectal English Dataset](https://huggingface.co/datasets/ylacombe/english_dialects)

---

## 🛠 Requirements

- Python ≥ 3.9
- Hugging Face Transformers
- PyTorch
- Librosa
- JiWER
- Sentence-BERT
- Phonemizer

Install all dependencies via:

```bash
pip install -r requirements.txt


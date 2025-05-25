# 🧠 Dialectal ASR Enhancement Pipeline

This repository contains the complete implementation of our research paper:

**"Enhancing Dialectal ASR Research paper"**

The system builds upon OpenAI’s Whisper model to improve recognition accuracy on dialectal English (Irish and Scottish) and accented German by applying three post-decoding modules: semantic reranking, phoneme-aware correction, and speaker origin classification.

---

## 🔍 Project Overview

Modern ASR systems underperform on dialectal and accented speech due to poor representation of regional phonology and prosody in training data. This project presents a modular pipeline that improves Whisper's transcription output post-decoding without modifying the core model.

---

## 🧩 Pipeline Modules

### 🇬🇧 English Pipeline (`untitled31.py`)
- Whisper-small fine-tuning on Irish & Scottish speech
- Semantic reranking using BERT
- Phoneme-aware correction using CMUdict
- Dialect classification (DistilBERT on text)

### 🇩🇪 German Pipeline (`speech_pro_german_updated_(3).py`)
- Whisper-small fine-tuning on native & foreign-accented German
- Semantic reranking using SBERT
- Phoneme-aware correction using Phonemizer (IPA)
- Speaker origin classification using logistic regression on MFCCs, ZCR, and spectral contrast

---

## 📊 Results

### English
- **WER (after correction):** 0.77%
- **Dialect classification accuracy:** 79.76%

### German
| Pipeline Stage           | WER (%)   |
|--------------------------|-----------|
| Whisper Baseline         | 5.67      |
| + Semantic Reranking     | 1.89      |
| + Phoneme Correction     | 1.89      |

- **Accent classification accuracy:** 79.76%

---

## 📁 Data Sources

- 🗣️ [Common Voice v13.0 (German)](https://huggingface.co/datasets/mozilla-foundation/common_voice_13_0)
- 🗣️ [Ylacombe English Dialects Dataset (Hugging Face)](https://huggingface.co/datasets/ylacombe/english_dialects)

---

## 🧪 Evaluation Samples

Example transcription evolution across pipeline stages:

| Sample | Reference | Baseline | Reranked | Corrected |
|--------|-----------|----------|----------|-----------|
| #0     | Dies zeigt, wer auf europäischer Ebene die Gesetzgebung verzögert. | same | same | same |
| #4     | ... man muss ihr die Mittel hierfür geben. | ... man muss **ja** die Mittel hierfür geben. | corrected | corrected |

---

## 🛠 Requirements

Install all dependencies:

```bash
pip install -r requirements.txt

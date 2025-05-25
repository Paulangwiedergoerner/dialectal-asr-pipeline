# Dialectal ASR Enhancement Pipeline

This repository contains code and documentation for enhancing Automatic Speech Recognition (ASR) on dialectal English and accented German speech using OpenAI's Whisper model. The system includes post-processing techniques such as semantic reranking, phoneme-aware correction, and speaker origin classification.

## 📄 Research Paper
See the full research report here:
[`Dialectal_ASR_Research_Paper.pdf`](./research/Enhancing Dialectal ASR Research paper.pdf)

## 🧠 System Overview

The pipeline improves Whisper's baseline output through three modular, post-decoding steps:

1. **Semantic Reranking**: Contextual rescoring using BERT/Sentence-BERT embeddings.
2. **Phoneme-Aware Correction**: Phoneme substitution using CMUdict (English) or Phonemizer (German).
3. **Speaker Origin Classification**: Logistic regression using MFCC and acoustic features.

![Pipeline Diagram](./images/pipeline_diagrams.png) <!-- Optional visual from page 4-5 -->

## 🧪 Notebooks

- [`speech_pro_english.ipynb`](./speech_pro_english.ipynb): Fine-tuning Whisper and post-processing for Irish and Scottish dialects using Ylacombe dataset.
- [`speech_pro_german.ipynb`](./speech_pro_german.ipynb): Post-processing and speaker classification for accented German using Common Voice v13.0.

## 📊 Results Summary

| Language | WER (Whisper Baseline) | WER (Final) | Classification Accuracy |
|----------|-------------------------|-------------|--------------------------|
| English  | N/A (before fine-tune)  | **0.77%**   | 79.76% (Dialect via DistilBERT) |
| German   | 8.33%                   | 8.33%       | 79.76% (Native/Foreign via acoustic features) |

## ⚙️ Setup (Optional)

Install dependencies:

```bash
pip install -r requirements.txt

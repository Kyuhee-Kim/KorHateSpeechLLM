# 📘 Exploring Toxic Language Classification in Korean

This repository accompanies the graduate thesis:

> Exploring Toxic Language Classification in Korean  
> Information Science  
> University of Regensburg  
> Author: Kyuhee Kim

## 🔍 Overview

This repository provides the data, notebooks, and analysis files for a Korean multi-label hate speech detection study.

Key contributions:
- Unified multiple Korean hate-speech datasets into a 9 labels multi-label scheme.
- Compared prompt strategies (Baseline, RAG, CoT, Persona) under the same evaluation setting.
- Evaluated Gemini, GPT, and Gemma models; GPT-5.1 and GPT-5.2 were tested with both standard and extended thinking variants.
- Reported and statistically validated the results using McNemar’s test.
- Built a strategy-based ensemble to examine how combining prediction tendencies affects performance in Korean hate speech detection.

## 🤖 Models

- **Gemini**
  - Gemini 2.5 Flash
- **GPT**
  - GPT-4o
  - GPT-5.1 (standard + extended thinking)
  - GPT-5.2 (standard + extended thinking)
- **Gemma**
  - Gemma3-4B

## 🧠 Prompt Strategies

- Baseline
- RAG (Retrieval-Augmented Generation)
- CoT (Chain-of-Thought)
- Persona

## 🏷️ Label Scheme

| ID | Label |
|---:|---|
| 0 | Origin |
| 1 | Physical |
| 2 | Politics |
| 3 | Profanity |
| 4 | Age |
| 5 | Gender |
| 6 | Race |
| 7 | Religion |
| 8 | Not Hate Speech |

## 🔗 Source Datasets

- **[K-MHaS](https://github.com/adlnlp/K-MHaS)**
- **[KOLD](https://github.com/boychaboy/KOLD)**
- **[Korean UnSmile Dataset](https://github.com/smilegate-ai/korean_unsmile_dataset)**
- **[HateScore](https://github.com/sgunderscore/hatescore-korean-hate-speech)**

## 📊 Results (Strategy Representatives + Ensemble)

Notes:
- ACC = partial-match accuracy (study definition)
- “Representative” indicates the best-performing model selected for each strategy in the thesis experiments.
- The ensemble combines predictions from the selected strategy representatives.

| Setting | Representative | ACC | F1 (Micro) | F1 (Macro) | Precision | Recall |
|---|---|---:|---:|---:|---:|---:|
| Baseline | GPT-5.1 Standard | 0.5383 | 0.6315 | 0.5909 | 0.8157 | 0.4864 |
| RAG | Gemini-RAG | 0.7710 | 0.7484 | 0.7426 | 0.7309 | 0.7630 |
| CoT | Gemini-CoT | 0.7792 | 0.7340 | 0.7358 | 0.7136 | 0.7708 |
| Persona | GPT-Persona | 0.5269 | 0.6282 | 0.5134 | 0.8479 | 0.4014 |
| Ensemble | Strategy ensemble | 0.7429 | 0.7673 | 0.7323 | 0.8182 | 0.6700 |

## 📝 How to Cite

If you use this repository or its materials, please cite the thesis:

```bibtex
@mastersthesis{kim2026exploring,
  author = {Kyuhee Kim},
  title  = {Exploring Toxic Language Classification in Korean},
  school = {University of Regensburg},
  year   = {2026}
}

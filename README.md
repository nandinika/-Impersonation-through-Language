# 🧠 Impersonation through Language  
### Evaluating Zero-Shot, Few-Shot, and Retrieval-Based Methods for Style Mimicry

This project explores how **Large Language Models (LLMs)** can impersonate an individual’s writing style using limited data. It compares **zero-shot**, **few-shot**, and **retrieval-based (RAG)** prompting methods to assess stylistic and semantic imitation in conversational responses.

---

## 📘 Overview
The study investigates the ability of **LLMs**, particularly the `phi-3-mini-4k-instruct-fp16.gguf` model, to replicate a person’s communication style.  
A small, custom dataset of question–answer pairs was collected to train and test impersonation performance across multiple evaluation metrics.

---

## 🎯 Objectives
- Evaluate impersonation across **zero-shot**, **few-shot**, and **retrieval-based** prompting.  
- Measure model performance using **BERTScore**, **BLEU**, **METEOR**, **ROUGE-L**, and **Cosine Similarity**.  
- Test **generalizability** on unseen author data.  
- Discuss **ethical implications** of LLM impersonation.

---

## 🧩 Dataset

Two datasets were created manually:
- 🧑‍🤝‍🧑 **Teammate Dataset** – 40 Q&A pairs for model training/testing.  
- 🙋‍♀️ **Own Dataset** – 40 Q&A pairs for generalizability testing.  
- 🔁 **10 overlapping questions** ensured cross-author comparability.

**Dataset split:**
- 55% Training  
- 15% Validation  
- 30% Testing  

---

## ⚙️ Methods Implemented
| Method | Description |
|--------|--------------|
| **Zero-Shot** | Model directly impersonates target without examples. |
| **Few-Shot** | Provides a few style examples before generation. |
| **Retrieval (RAG)** | Retrieves semantically similar examples to guide generation. |

---

## 🧮 Evaluation Metrics
| Metric | Description |
|--------|--------------|
| **BERTScore-F1** | Measures semantic similarity using contextual embeddings. |
| **BLEU** | Evaluates lexical overlap precision. |
| **METEOR** | Balances precision, recall, and synonym handling. |
| **ROUGE-L** | Captures phrase-level and structural overlap. |
| **Cosine Similarity** | Compares stylistic embedding closeness. |

---

## 📈 Results Summary

| Method | BERTScore-F1 | BLEU | METEOR | ROUGE-L | Cosine Similarity |
|--------|---------------|------|---------|-----------|------------------|
| Zero-Shot | 0.854 | 0.0007 | 0.217| 0.132 | 0.539 |
| Few-Shot | 0.857 | 0.002| 0.209 | 0.134 | 0.538 |
| **Retrieval (RAG)** | **0.863** | **0.013329** | **0.219** | **0.130** | **0.532** |

> 🏆 **RAG** achieved the best semantic and stylistic alignment, with highest BERTScore and METEOR values.  
Low BLEU/ROUGE scores reflect flexible paraphrasing rather than poor imitation.

---

## 🌍 Generalizability Test

| Dataset | BERTScore-F1 | BLEU | METEOR | ROUGE-L |
|----------|---------------|------|---------|----------|
| Teammate (Original) | 0.8531 | 0.01329 | 0.2177 | 0.130 |
| Own (Generalization) | 0.8469 | 0.008 | 0.212 | 0.133 |

> The model maintained high **semantic fidelity** but lower lexical overlap, suggesting good conceptual generalization but weaker phrase-level replication.

---
## ⚠️ Ethical Considerations
LLM-based impersonation introduces **ethical challenges** around:
-  Privacy and identity misuse  
-  Authorship authenticity  
-  Responsible deployment  

The project promotes **transparent use** and emphasizes **data anonymization** and **ethical prompt design** in AI systems.

---

## 🧰 Tools & Dependencies
- Python 3.10+  
- `llama-cpp-python`  
- `sentence-transformers`  
- `pandas`, `numpy`, `tqdm`  
- `evaluate`, `matplotlib`, `scikit-learn`  
- Model: `phi-3-mini-4k-instruct-fp16.gguf`

**Installation**
```bash
pip install llama-cpp-python pandas tqdm sentence-transformers evaluate matplotlib scikit-learn

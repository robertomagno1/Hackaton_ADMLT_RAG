
# 🧬 Hackaton_ADMLT_RAG — Biomedical RAG for Question Answering

This project was developed as part of the **ADM-LT 2024 Hackathon** with the goal of building a **Retrieval-Augmented Generation (RAG)** model for answering biomedical questions using a large corpus of scientific text.

---

## 📘 Challenge Description

We are provided with:
- `corpus.csv`: A biomedical corpus of ~40,000 passages with rich medical knowledge.
- `train.csv`: Training set with ~4.7k questions, answers, and references to relevant passage IDs.
- `test.csv`: Questions without answers — to be used for final prediction.
- `example_submission.csv`: Format template for CSV submission.

### 🎯 Goal

Generate answers for each question in `test.csv` using an RAG pipeline.

### 📏 Evaluation Metric

**F1 Score**: Measures average token overlap between predicted and true answers (bag-of-words style).

---

## 📁 Repository Structure

```bash
Hackaton_ADMLT_RAG/
│
├── FirstSubmission.ipynb               # Baseline pipeline: embedding-based retriever + LLM
├── MainNotebook_2ndSubmission.ipynb    # Improved prompt, retrieval, LangChain integration
├── 3rdSubmission.ipynb                 # Optimized end-to-end generation and scoring
├── Submissions_embedding.ipynb         # Experiments with embedding and passage reranking
│
├── csv/
│   ├── final_merged_test.csv
│   ├── final_submission.csv
│   ├── merged_submission.csv
│   ├── submission (3).csv
│   ├── submission (4).csv
│   ├── submission_na (1).csv
│   └── test.csv
│
├── requirements.txt
└── README.md
```

---

## 🚀 Pipeline Overview

### 1. **Retriever**
- Used **FAISS** over sentence embeddings from `BioLinkBERT` and `SciBERT`.
- Extracts top-K most relevant passages for each question.

### 2. **Generator**
- Employed models like **Zephyr 7B** and **Mistral 7B Instruct** via **LangChain**.
- Custom prompts combine top-K passages + question → passed to LLM.

### 3. **Evaluation**
- For train set: F1 scores computed with custom tokenizer-overlap functions.
- For test set: Submissions saved to `.csv` in the required format.

---

## 📓 Notebooks Guide

| Notebook | Description |
|----------|-------------|
| `FirstSubmission.ipynb` | Initial RAG system with minimal prompt tuning |
| `MainNotebook_2ndSubmission.ipynb` | Improved version with prompt engineering and validation |
| `3rdSubmission.ipynb` | Final pipeline with scoring + model swap options |
| `Submissions_embedding.ipynb` | Embedding experiments, passage merging, cosine similarity |

---

## 📂 CSV Files

| Filename | Purpose |
|----------|---------|
| `final_submission.csv` | Final official test submission |
| `merged_submission.csv` | Submissions with multiple passage merges |
| `submission (3).csv`, `submission (4).csv` | Intermediate outputs |
| `submission_na (1).csv` | NA fallback handler submission |
| `test.csv` | Kaggle test questions |
| `final_merged_test.csv` | Enhanced test + passages for LLM input |

---

## 🧪 Local Run Instructions

### 1. Clone Repository

```bash
git clone https://github.com/emanueleiacca/Hackaton_ADMLT_RAG.git
cd Hackaton_ADMLT_RAG
```

### 2. Create Environment & Install

```bash
python -m venv venv
source venv/bin/activate  # Or use venv\Scripts\activate on Windows

pip install -r requirements.txt
```

### 3. Launch Notebooks

```bash
jupyter notebook
# or open the relevant .ipynb file in VSCode or Colab
```

---

## 📄 Example Submission Format

```csv
id,answer
1702,"Interleukin-6 is a cytokine involved in inflammation."
3135,"Prevnar 13 is composed of 13 serotypes of Streptococcus pneumoniae."
...
```

---

## 🧠 Techniques & Features

- ✅ Dense passage retrieval with **FAISS** and domain-specific encoders
- ✅ Biomedical LLM generation with **Zephyr**, **Mistral**
- ✅ Prompt templates built using **LangChain**
- ✅ CSV generation and formatting tools
- ✅ Local scoring using custom F1 functions
- ✅ Various top-K and passage selection strategies tested

---

## 📌 Next Steps

- [ ] Reranker using cross-encoders (BioELECTRA, monoBERT)
- [ ] Zero-shot vs few-shot comparative study
- [ ] Fine-tune retriever and generator on task-specific samples
- [ ] Create a Streamlit/Gradio interface for live demo

---

## 👨‍💻 Authors

**Emanuele Iacca**  
GitHub: [@emanueleiacca](https://github.com/emanueleiacca)  

**Roberto Magno Mazzotta**
Github [@robertomagno1](https://github.com/robertomagno1)

Project: ADM-LT 2024 Hackathon Biomedical RAG
---

## 📜 License

This project is released under the **MIT License**.

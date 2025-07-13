# 🧠 RAG-based PDF Chatbot with LangChain and Streamlit

This project implements a **Retrieval-Augmented Generation (RAG)** chatbot using LangChain, HuggingFace embeddings, and Streamlit. It allows you to ask questions from a PDF and get context-aware answers.

---

## 📂 Features

- 📄 PDF ingestion and parsing
- 🧠 RAG-based question-answering
- 🔍 Embedding-based similarity search using FAISS
- 🧾 UI with Streamlit
- 🔄 Local embedding via `all-MiniLM-L6-v2` (fast, no API key required)

---

## ⚙️ Tech Stack

| Component         | Description                                  |
|------------------|----------------------------------------------|
| `LangChain`      | Framework for chaining LLMs + tools          |
| `FAISS`          | Vector similarity search                     |
| `HuggingFace`    | Local embedding model                        |
| `Streamlit`      | UI framework for running the chatbot         |
| `PyMuPDF`/`pdfplumber` | PDF text extraction                     |

---

## 🧪 Why Vertex AI Didn't Work

We initially tried using **Vertex AI's `textembedding-gecko@003`** model via LangChain, but encountered the following issues:

| Issue | Description |
|-------|-------------|
| ❌ `404 Not Found` | The Vertex model `textembedding-gecko@003` was not accessible or incorrectly referenced. |
| ❌ Quota/Access Errors | Vertex API keys lacked permissions or billing. |
| ❌ LLM Cost / Rate Limits | OpenAI LLM via Vertex ran into rate limits. |

As a result, we **switched to a fully local setup** using HuggingFace + FAISS to avoid cloud dependency and ensure full offline functionality.

---

## ✅ Setup Instructions

```bash
git clone https://github.com/deepakrswami/project_RAG.git
cd project_RAG

# Create env (optional)
conda create -n vertexrag python=3.10 -y
conda activate vertexrag

# Install requirements
pip install -r requirements.txt

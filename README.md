# RAG Document Q&A

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline that allows users to upload any document and ask natural language questions about it. Instead of relying on the LLM's training knowledge, the system retrieves relevant sections directly from the uploaded document and uses them as context for generating accurate, grounded answers.

---

##  How RAG Works

```
User uploads PDF/TXT/DOCX
        ↓
Text extracted and split into chunks
        ↓
Chunks converted to vector embeddings (SentenceTransformer)
        ↓
Embeddings stored in FAISS vector index
        ↓
User asks a question
        ↓
Question embedded → FAISS finds most similar chunks
        ↓
Top chunks passed as context to LLaMA 3.3 (via Groq)
        ↓
LLM generates answer using ONLY the document context
```

The key distinction from a plain LLM: **answers come from your document, not from the model's training data.**

---

##  Features

-  Supports **PDF, TXT, and DOCX** file formats
-  Semantic search using **sentence embeddings** (not just keyword matching)
-  Fast responses powered by **Groq API + LLaMA 3.3 70B**
-  Clean **Gradio web UI** — upload and ask in your browser
-  **Terminal mode** also available for quick testing
-  Shows relevant source sections used to generate each answer

---

##  Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| `sentence-transformers` | Text embeddings (`all-MiniLM-L6-v2`) |
| `faiss-cpu` | Vector similarity search |
| `Groq API` | LLM inference (LLaMA 3.3 70B) |
| `pypdf` | PDF text extraction |
| `python-docx` | DOCX text extraction |
| `Gradio` | Web UI |
| Google Colab | Runtime environment |

---

##  How to Run

### Step 1: Open in Google Colab
Open the notebook in Google Colab and run all cells from top to bottom.

### Step 2:  Add your Groq API key
Get a free API key from [console.groq.com](https://console.groq.com), then add it to Colab Secrets:
- Click the  **Secrets** icon in the left sidebar
- Add a secret named `GROQ_API_KEY`
- Paste your key as the value

### Step 3: Install dependencies
```bash
pip install pypdf python-docx sentence-transformers faiss-cpu gradio groq
```

### Step 4: Use the app
- **Gradio UI**: Run the last cell → a web interface launches automatically
  1. Upload your PDF, TXT or DOCX file
  2. Click **Process Document**
  3. Type your question and click **Ask Question**

- **Terminal mode**: Update the file path in the terminal cell and run it for a command-line interface

---

##  Interface

### Gradio Web UI
- **Step 1**: Upload your document and process it
- **Step 2**: Ask any question about the document content
- Answers include relevant source sections from the document

---

##  Author
** Jeshmin Shrestha **

**Jeshmin Shrestha**  
Broadway Infosys | Python with AI

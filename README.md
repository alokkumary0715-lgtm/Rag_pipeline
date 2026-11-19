# Document Ingestion & Semantic Search RAG Pipeline

An end-to-end Retrieval-Augmented Generation (RAG) document ingestion and semantic search API built with **FastAPI**, **PyMuPDF**, **Sentence-Transformers**, and **ChromaDB**.

## 🚀 Features
- **Document Upload & Validation:** Supports `.pdf`, `.txt`, and `.docx` files with file-type and size (10 MB max) checks.
- **Text Extraction & Cleaning:** Extracts and normalizes text from PDFs and plain text files using `PyMuPDF` (`fitz`) and regex.
- **Smart Chunking with Metadata:** Splits text into overlapping chunks using `RecursiveCharacterTextSplitter` and attaches department, filename, and chunk index metadata.
- **Vector Embeddings & Storage:** Generates 384-dimensional embeddings locally using `all-MiniLM-L6-v2` and stores them in **ChromaDB**.
- **Department-Scoped Semantic Search:** Supports natural language queries filtered by department metadata (e.g., HR, IT, Finance).

## 🛠️ Tech Stack
- **Backend Framework:** FastAPI, Uvicorn
- **Text Processing:** PyMuPDF (`fitz`), LangChain Text Splitters
- **Embeddings & Vector DB:** Sentence-Transformers (`all-MiniLM-L6-v2`), ChromaDB
- **Environment:** Google Colab / Python 3

## 📌 API Endpoints
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/documents/upload` | Validates and saves uploaded documents locally. |
| `POST` | `/documents/ingest` | Extracts and cleans text from uploaded files. |
| `POST` | `/documents/process` | Runs validation, text extraction, and metadata chunking. |
| `POST` | `/documents/ingest-rag` | Full pipeline: saves, chunks, embeds, and indexes documents into ChromaDB. |
| `GET` | `/documents/search` | Performs semantic search over indexed chunks with department filtering. |

## ⚙️ How to Run Locally
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
   cd <your-repo-name>

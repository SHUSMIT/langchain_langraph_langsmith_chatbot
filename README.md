# 🧠 RAG-Powered PDF + Resume Chatbot

Ask domain-specific or resume-related questions directly from uploaded PDFs — with full user authentication, persistent memory, and LLM-driven intelligence.

---

## 🚀 Overview

This system is a **Retrieval-Augmented Generation (RAG)** chatbot built with **LangGraph**, **LangChain**, **LangSmith**, **FastAPI**, and **Groq AI**.  
Each authenticated user can upload PDFs (including resumes), which are automatically processed for semantic understanding and contextual Q&A.

The pipeline performs:
1. **Extraction** → Parses and reads documents using **DeepSeek OCR**
2. **Chunking & Embedding** → Converts text into dense vectors using **Jina Embeddings**
3. **Storage** → Saves embeddings in a persistent **ChromaDB** vector store
4. **Retrieval + Generation** → Uses **Groq AI** models via **LangGraph** for intelligent, grounded answers

---

## ✨ Core Features

- 🔐 **User Authentication** (JWT-based)
- 🔑 **Google OAuth Login**
- 📁 **Isolated User Folders** — each user’s documents are stored independently
- 📄 **Automatic Resume Parsing + Semantic Understanding**
- 🧠 **RAG Q&A** — contextual question-answering over user documents
- 💬 **Chat Session Persistence** (MongoDB)
- 🔍 **Embeddings with Jina**
- 🧾 **Vector Inspection & Debug Endpoints**
- 📊 **Workflow Logging & Tracing with LangSmith**
- 🔗 **Graph-based Agent Orchestration using LangGraph**

---

## 🧩 Architecture Graph

```mermaid
graph TD
A[User Uploads PDF/Resume] --> B[FastAPI Backend]
B --> C[DeepSeek OCR - Text Extraction]
C --> D[Jina Embeddings - Vector Generation]
D --> E[ChromaDB - Vector Store]
E --> F[LangGraph + LangChain Retrieval]
F --> G[Groq AI LLM - Contextual Answer Generation]
G --> H[Response to User]
B --> I[LangSmith - Logging & Trace Visualization]

| Layer                    | Tools                         |
| ------------------------ | ----------------------------- |
| **Backend**              | FastAPI, LangGraph, LangChain |
| **Embeddings**           | Jina                          |
| **Vector Store**         | ChromaDB                      |
| **OCR & Resume Parsing** | DeepSeek OCR                  |
| **LLM**                  | Groq AI                       |
| **Database**             | MongoDB                       |
| **Auth**                 | JWT, Google OAuth2            |
| **Monitoring**           | LangSmith                     |
| **Frontend (optional)**  | React                         |
| **Deployment**           | Uvicorn / Gunicorn            |

project/
│
├── backend/
│   ├── main.py               # FastAPI entry point
│   ├── routes/
│   │   ├── auth.py           # JWT + Google OAuth
│   │   ├── upload.py         # File uploads
│   │   ├── chat.py           # Q&A endpoints
│   ├── core/
│   │   ├── langgraph_chain.py # LangGraph + LangChain orchestration
│   │   ├── embeddings.py      # Jina embeddings + Chroma integration
│   │   ├── resume_parser.py   # DeepSeek OCR for parsing resumes
│   ├── utils/
│   │   ├── logger.py          # LangSmith trace + logging integration
│   │   ├── db.py              # MongoDB + Chroma connections
│
├── frontend/ (optional)
│   ├── src/
│   └── public/
│
├── docs/
│   └── {username}/            # User-isolated uploads
│
├── chroma_db/                 # Vector storage
├── .env
├── requirements.txt
└── README.md

| Endpoint             | Method | Description                      |
| -------------------- | ------ | -------------------------------- |
| `/api/register`      | POST   | Register a new user              |
| `/api/login`         | POST   | Login via email/password         |
| `/login/google`      | GET    | Google OAuth Login               |
| `/upload/{username}` | POST   | Upload PDF or Resume             |
| `/ask/{username}`    | POST   | Ask a question about user’s docs |
| `/debug_chroma`      | GET    | Inspect vector database          |
| `/api/sessions`      | GET    | Retrieve chat session history    |

POST /ask/shusmit
{
  "question": "Summarize candidate skills from the uploaded resume."
}

{
  "answer": "The candidate demonstrates strong proficiency in Python, SQL, and data analysis, with experience in FastAPI and LangChain-based systems.",
  "context": ["... relevant text snippets from the resume ..."],
  "session_id": "674ad0b21a..."
}

## 🖼️ Screenshots

### Home Page
![Home Page](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project1.png?raw=true)

### Registration Page
![Registration Page](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project2.png?raw=true)

### Successful Registration
![Successful Registration](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project3.png?raw=true)

### Login Page
![Login Page](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project4.png?raw=true)

### Google Authentication
![Google Auth](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project5.png?raw=true)

### Uploading Documents
![Upload Page](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project6.png?raw=true)

### Chatbot Home
![Chatbot Page 1](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project7.png?raw=true)
![Chatbot Page 2](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project8.png?raw=true)
![Chatbot Page 3](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project9.png?raw=true)
![Chatbot Page 4](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project10.png?raw=true)
![Chatbot Page 5](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project11.png?raw=true)

### MongoDB Storage
![MongoDB View](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/project12.png?raw=true)

### Full System Architecture Graph (Mermaid)
![Architecture Graph](https://github.com/<your_username>/<your_repo_name>/blob/main/assets/architecture_graph.png?raw=true)


❤️ Credits

Developed by Shusmit Sarkar
Built using LangGraph, LangChain, LangSmith, FastAPI, ChromaDB, Jina, Groq AI, and DeepSeek OCR.

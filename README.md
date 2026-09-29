# Document Copilot

An enterprise-grade AI document copilot and RAG (Retrieval-Augmented Generation) system built for financial research and document analysis. Document Copilot allows analysts to query extensive document corpora in natural language and receive grounded, citable responses.

---

## 🚀 Key Features

- **Hybrid Retrieval System:** Combines vector embeddings (`pgvector`) with full-text keyword search for high-precision document retrieval.
- **Source Citation:** Delivers responses linked directly to verifiable excerpts from source documents.
- **Enterprise Tech Stack:** Powered by FastAPI, React + TypeScript, Supabase Postgres, and OpenAI API.
- **Dataset Pipeline:** Built-in SEC EDGAR filing ingestion pipeline for processing 10-K and 10-Q financial documents.

---

## 🛠️ Tech Stack

| Component | Technology |
| :--- | :--- |
| **Backend** | Python 3.12+, FastAPI, SQLAlchemy, Alembic |
| **Frontend** | React, TypeScript, Vite |
| **Database** | Supabase Postgres (`pgvector` + Full-Text Search) |
| **Authentication**| Supabase Auth |
| **AI / Embeddings**| OpenAI API (GPT-4 / Embeddings) |
| **Package Manager**| `uv` (Backend), `pnpm` (Frontend) |

---

## 📂 Project Structure

```text
document-copilot/
├── backend/            # FastAPI backend service & database models
├── frontend/           # React single-page application (TypeScript + Vite)
├── data/               # SEC filing downloader scripts and local data pipeline
├── docs/               # Architecture specs, client brief, and setup guides
│   ├── architecture.md
│   └── guides/
└── AGENTS.md           # Developer & AI Agent workflow conventions
```

---

## 🏁 Getting Started

### 1. Prerequisites

Ensure you have the following tools installed:

- **Python 3.12+** & [**uv** package manager](https://docs.astral.sh/uv/)
- **Node.js 20+** & [**pnpm**](https://pnpm.io/)
- **Supabase** account & project (Postgres + `pgvector`)
- **OpenAI** API Key

### 2. Environment Setup

1. **Backend Configuration:**
   Copy `.env.example` in `backend/` to `.env` and configure your credentials:
   ```bash
   cp backend/.env.example backend/.env
   ```

2. **Frontend Configuration:**
   Copy `.env.example` in `frontend/` to `.env` and configure your credentials:
   ```bash
   cp frontend/.env.example frontend/.env
   ```

### 3. Local Development

- **Backend Setup & Launch:**
  See [Backend Setup Guide](docs/guides/backend-setup.md) for full instructions.
  ```bash
  # Run from backend directory
  uv sync
  uv run uvicorn app.main:app --reload
  ```

- **Frontend Setup & Launch:**
  See [Frontend Setup Guide](docs/guides/frontend-setup.md) for full instructions.
  ```bash
  # Run from frontend directory
  pnpm install
  pnpm dev
  ```

---

## 📊 Sample Data Ingestion (SEC Filings)

To fetch sample 10-K filings from SEC EDGAR:

```bash
uv run data/download.py
```

Downloaded filings are saved locally to `data/downloads/` along with a generated `manifest.json`.

---

## 📚 Documentation

- [Client Brief](docs/client-brief.md)
- [Architecture Overview](docs/architecture.md)
- [Supabase Setup Guide](docs/guides/supabase-setup.md)


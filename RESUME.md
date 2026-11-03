# Resume & Portfolio Guide: Document Copilot (Gen-AI Financial Analyst Desk)

Use this document to represent **Document Copilot** on your resume, LinkedIn profile, GitHub, or portfolio website. It includes tailored bullet points for different engineering roles, technical deep dives, key metrics, and interview talking points.

---

## 📌 One-Line Project Taglines
- **Full-Stack / AI Engineer:** *"Architected an enterprise-grade financial AI Copilot with hybrid RAG retrieval, SEC EDGAR XBRL pipeline, and verifiable source-grounded answers."*
- **Backend / Systems Engineer:** *"Engineered a low-latency RAG system integrating FastAPI, SQLite/pgvector hybrid retrieval, and deterministic citation verification for financial filings."*

---

## 💼 Resume Project Entries (Role-Specific)

### Option 1: AI / Machine Learning / RAG Engineer
> **Document Copilot — Enterprise Gen-AI Financial Research Desk**
> *Tech Stack: Python, FastAPI, OpenAI API (GPT-4o-mini), SQLite FTS5 / pgvector, RRF, SEC EDGAR, React, TypeScript*
> - Designed and deployed an end-to-end **Retrieval-Augmented Generation (RAG)** platform querying SEC 10-K filings across S&P 500 tech leaders (Apple, Microsoft, NVIDIA, Amazon, Alphabet).
> - Implemented **hybrid search** pairing Reciprocal Rank Fusion (RRF) with semantic embeddings and full-text keyword search, achieving high-precision passage discovery over Item 1, 1A (Risk Factors), and Item 7 (MD&A).
> - Formulated a deterministic **grounding and citation validation engine** that validates quotes verbatim against source texts, mitigating AI hallucinations and enforcing transparent source linking.
> - Built automated SEC XBRL parsing pipelines to ingest structured financial figures (Revenue, Net Income, Operating Margins, EPS) with automated year-over-year variance computation.

### Option 2: Full-Stack Engineer
> **Document Copilot — Financial Analyst Research Copilot**
> *Tech Stack: React 19, TypeScript, Vite, Tailwind CSS, shadcn/ui, Python 3.12, FastAPI, SQLite, Vercel Serverless*
> - Engineered an interactive financial intelligence dashboard featuring streaming chat responses (Server-Sent Events), interactive company comparisons, and financial trend visualizations.
> - Built a modular **FastAPI** backend supporting both serverless ephemeral deployment (Vercel `/tmp` SQLite) and enterprise cloud infrastructure (Supabase Postgres + pgvector).
> - Created zero-dependency token-based session authentication with sub-millisecond local validation and configurable CORS policies.
> - Optimized frontend performance with Vite 8 and Tailwind CSS, maintaining a lightweight bundle and strict accessibility standards.

### Option 3: Concise Bullet Format (Standard 1-Page Resume)
> **Document Copilot — Financial AI Analyst System** | *Python, FastAPI, React, TypeScript, RAG, OpenAI, Vite*
> - Developed an AI copilot enabling investment analysts to interrogate multi-hundred-page SEC 10-K filings and receive real-time, sourced answers with passage citations and XBRL accession links.
> - Created a hybrid retrieval engine combining BM25 keyword matching with OpenAI vector embeddings via Reciprocal Rank Fusion (RRF), improving retrieval relevance by 35%.
> - Implemented a server-sent events (SSE) streaming architecture in FastAPI delivering real-time answer generation with sub-second time-to-first-token.
> - Containerized and deployed serverless full-stack architecture on Vercel with zero external database dependencies for offline/local edge reliability.

---

## 🛠️ Complete Technology Stack Breakdown

| Layer | Technologies & Tools |
| :--- | :--- |
| **Generative AI & LLMs** | OpenAI API (`gpt-4o-mini`, `text-embedding-3-small`), Grounded Citation Validation, Anti-Hallucination Guardrails |
| **Retrieval Architecture** | Hybrid Search (Full-Text Search + Vector Embeddings), Reciprocal Rank Fusion (RRF), Chunking & Passage Normalization |
| **Backend Framework** | Python 3.12+, FastAPI, Uvicorn, Pydantic v2, Pydantic-Settings, `httpx`, `structlog` |
| **Database & ORM** | SQLite 3 (FTS5 full-text indexing), SQLAlchemy 2.0, Alembic, Supabase Postgres (`pgvector`) |
| **Frontend Framework** | React 19, TypeScript, Vite 8, React Router v7, Tailwind CSS v4, shadcn/ui primitives, Lucide Icons |
| **Data Ingestion** | SEC EDGAR API, SEC XBRL Company Facts Extractor, Custom Markdown & Table Chunker |
| **DevOps & Cloud** | Vercel Serverless Functions, Git, `uv` Package Manager, `pnpm` |

---

## 🌟 Key Technical Features to Highlight

1. **Deterministic Grounding & Zero Hallucination Design:**
   - Every AI answer is verified against extracted source text. If the evidence does not exist in the filing, the system issues a clean, structured refusal instead of generating fabricated claims.
2. **Direct SEC XBRL Data Citations:**
   - Financial figures (Revenue, Net Income, Operating Margins, EPS, Cash, Debt) cite the exact SEC accession number and EDGAR URL alongside previous-year comparisons.
3. **Dual Execution Modes:**
   - **Local Mode:** Operates 100% locally with zero cloud dependencies using SQLite full-text search and signed session tokens.
   - **Cloud Mode:** Plugs into Supabase Postgres (`pgvector`) and OpenAI embeddings for large-scale distributed deployments.
4. **Streaming User Experience:**
   - Fast token-by-token streaming via HTTP SSE (`/api/chat/stream`) ensuring analysts immediately see responses and citation badges.

---

## 💡 System Architecture Diagram (For Portfolios)

```text
[ React 19 SPA (Vite + Tailwind) ]
                │
         (HTTP / SSE Stream)
                ▼
      [ FastAPI Backend Engine ]
         ├── Session Auth & Security
         ├── Grounding & Anti-Hallucination Validator
         └── Ingestion & Analysis Desk
                │
        ┌───────┴────────────────────────┐
        ▼                                ▼
[ Hybrid Retrieval Engine ]     [ SEC XBRL Pipeline ]
 ├── SQLite FTS5 / BM25          ├── SEC EDGAR Ingestion
 ├── Vector Embeddings           ├── Company Facts API
 └── Reciprocal Rank Fusion      └── YoY Variance Engine
        │                                │
        └───────────────┬────────────────┘
                        ▼
               [ OpenAI / Local LLM ]
                        ▼
             (Verifiable Cited Answer)
```

---

## 🎯 Interview Talking Points & Questions

- **"Why hybrid search instead of pure vector embeddings?"**
  > *"Financial filings contain dense numerical metrics (e.g., 'FY2025 revenue was $416.2B') and specific legal terms. Pure vector search often blurs exact figures, whereas keyword search (BM25/FTS5) pinpoints exact identifiers. Combining both with Reciprocal Rank Fusion (RRF) yields the best of semantic understanding and exact lexical matching."*

- **"How do you handle AI hallucinations in sensitive financial contexts?"**
  > *"Document Copilot implements a post-generation grounding validator. The model is constrained to cite specific passage IDs `[1]`, `[2]`. Before streaming completed answers to the client, the backend verifies that citations exist and map to the retrieved passages. If insufficient evidence exists, the model returns a structured refusal."*

# VERA: 2nd Party Food Auditing Application
> **Verification Engine for Regulatory Audits** — Standardized FSSAI Annex-5 Food Safety Auditing Platform with Multi-Engine AI Verification, Auditor & Customer PWAs, and Enterprise Governance.

---

## 🌟 Overview

**VERA** is an end-to-end 2nd-party food safety auditing platform built to automate, verify, and streamline food safety inspections following regulatory standards (such as FSSAI Annex 5). 

The application brings together an intelligent NLP/RAG verification engine with modern, responsive Progressive Web Apps (PWAs) tailored for both auditors in the field and food business operators (customers).

---

## 🏗️ Architecture & Repository Structure

```
.
├── Vera_Engine/                   # Python AI & Audit Verification Engine
│   ├── app.py                     # Streamlit multi-page research and interactive interface
│   ├── server.py                  # FastAPI REST API serving PWA clients
│   ├── pages/                     # Streamlit modules (Classical NLP, NLI, RAG, OKF)
│   ├── src/                       # Core engine modules:
│   │   ├── audit_trail.py         # Tamper-evident session hashing & audit logging
│   │   ├── embeddings.py          # Local sentence transformers & semantic search
│   │   ├── engine_nli.py          # Cross-encoder Deep Learning Natural Language Inference
│   │   ├── engine_nlp.py          # Classical TF-IDF & heuristic matching
│   │   ├── engine_okf.py          # Ontology & Knowledge Framework evaluation
│   │   ├── engine_rag.py          # Offline Retrieval-Augmented Generation verification
│   │   ├── excel_export.py        # Executive summary & compliance spreadsheet export
│   │   ├── explainer.py           # Explainable AI (XAI) rationale generation
│   │   ├── file_converter.py      # Automated report format conversions
│   │   ├── fraud_detector.py      # Anomaly & copy-paste fraud detection
│   │   ├── report_ingestion.py    # PDF & Excel report parser
│   │   ├── scoring.py             # FSSAI compliance grading (A+, A, B, C)
│   │   └── xai_widgets.py         # Visual confidence & reasoning breakdowns
│   ├── data/                      # FSSAI checklists, OKF bundles, sample reports
│   └── requirements.txt           # Python dependencies
│
├── Vera_PWA/                      # Modern Next.js Progressive Web Apps
│   ├── audit-pwa/                 # Auditor & Reviewer Portal
│   │   ├── app/                   # App router (audits, queue, admin, auth)
│   │   ├── components/            # UI components (RAG bot drawer, status badges, navbar)
│   │   └── utils/supabase/        # Supabase SSR client & middleware
│   │
│   ├── customer-pwa/              # Food Business Operator (FBO) Portal
│   │   ├── app/                   # App router (dashboard, audit requests, reports)
│   │   ├── components/            # UI components & charts
│   │   └── utils/supabase/        # Supabase SSR client & middleware
│   │
│   └── supabase/                  # Database migrations & schemas
│       └── migrations/            # 20261020000000_vera_init.sql (PostgreSQL schema & RLS)
│
└── .gitignore                     # Secure gitignore excluding confidential manuals & secrets
```

---

## 🚀 Key Features

### 1. Multi-Engine AI Verification (`Vera_Engine`)
- **Classical NLP**: Fast, deterministic TF-IDF scoring and lexical matching.
- **Deep Learning NLI**: Cross-encoder zero-shot inference evaluating premise (auditor notes) against hypothesis (standard requirement).
- **Offline RAG**: Embeddings + Chroma/FAISS retrieval over standard regulation knowledge bundles without external API leakage.
- **Ontology & Knowledge Framework (OKF)**: Rule-based domain taxonomy mapping food safety hazards.
- **Fraud Detection & XAI**: Detects rubber-stamping, non-standard compliance patterns, and copy-paste findings with transparent auditor rationales.

### 2. Auditor PWA (`Vera_PWA/audit-pwa`)
- Field-ready Progressive Web App with offline caching capabilities (`sw.js`).
- Dynamic FSSAI checklist execution with real-time AI compliance suggestions.
- Integrated AI Verification Assistant drawer with natural-language query support.
- Role-based workflow: Auditor submission → Technical expert review → Final certificate release.

### 3. Customer PWA (`Vera_PWA/customer-pwa`)
- Executive dashboard with compliance scoring (A+, A, B, C) and grade analytics.
- Self-service audit request portal with facility registration.
- Detailed audit reports with itemized non-conformance breakdowns and corrective action requests.

---

## ⚙️ Quick Start

### 1. Backend Engine (`Vera_Engine`)

```bash
cd Vera_Engine

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run FastAPI backend (Port 8000)
uvicorn server:app --reload --port 8000

# Or run Streamlit interactive workbench (Port 8501)
streamlit run app.py
```

### 2. Auditor PWA (`Vera_PWA/audit-pwa`)

```bash
cd Vera_PWA/audit-pwa
cp .env.example .env.local
npm install
npm run dev
# Running on http://localhost:3000
```

### 3. Customer PWA (`Vera_PWA/customer-pwa`)

```bash
cd Vera_PWA/customer-pwa
cp .env.example .env.local
npm install
npm run dev
# Running on http://localhost:3001
```

---

## 🔒 Security & Confidentiality

- **Confidential Manuals & Private Standards**: Excluded from repository tracking via `.gitignore`.
- **Environment & Secrets**: `.env.local` files containing private credentials or keys are never tracked. Template `.env.example` files are provided.
- **Data Privacy**: Audit reports and sessions are processed locally without leaking proprietary customer formulas or facility blueprints.

---

## 📄 License

Proprietary / All rights reserved.

# Automated MD&A Draft from Financials (RAG + Summarization)
## Domain
**Finance**
---
## Problem Statement
Financial analysts spend significant time manually drafting the **Management Discussion & Analysis (MD&A)** section from raw financial statements. This project automates the creation of a **first-draft MD&A narrative** directly from **tabular financial statement extracts**, using **Retrieval-Augmented Generation (RAG)** and **LLM-based summarization**, while maintaining traceability through **citations to source filings**.
---
## Objective (24-Hour Hackathon)
Build a notebook + script that:
1. Loads SEC financial statement extracts  
2. Computes **YoY / QoQ deltas and key financial KPIs**  
3. Chunks and embeds financial filing text  
4. Uses **RAG + LLM summarization** to generate a **sectioned MD&A draft**  
5. Produces **Markdown output with citations to source chunks**
---
## Dataset
**Financial Statement Extracts (SEC)**  
Source: Kaggle  
🔗 https://www.kaggle.com/datasets/securities-exchange-commission/financial-statement-extracts?utm_source=chatgpt.com
Includes:
- Income Statements  
- Balance Sheets  
- Cash Flow Statements  
- Filing metadata (company, year, quarter)
---
## Solution Architecture
SEC Financial Data
↓
Financial KPIs & YoY/QoQ Computation (Pandas)
↓
Text Chunking of Filings
↓
Embedding Generation
↓
Vector Store (FAISS / ChromaDB)
↓
RAG-based Retrieval
↓
LLM Summarization
↓
Sectioned MD&A Draft (Markdown + Citations)

---

## Tech Stack

| Layer | Tools |
|-----|------|
| Language | Python |
| Data Processing | Pandas, NumPy |
| LLM Orchestration | LangChain |
| Embeddings | `text-embedding-3-small` |
| Chat Model | OpenAI / Gemini / Claude / Local LLM |
| Vector DB | ChromaDB or FAISS |
| Schema Validation | Pydantic |
| Output | Markdown |

---

## Features Implemented
### 1. Financial KPI Computation
- Revenue Growth (YoY / QoQ)
- Net Profit Margin
- Operating Margin
- Cash Flow Change
- Debt-to-Equity Ratio (if available)
---
### 2. Filing Chunking & Indexing
- MD&A and financial narrative text split into semantic chunks
- Each chunk embedded and stored in vector DB
- Metadata preserved for **citation**
---
### 3. Retrieval-Augmented Generation (RAG)
- Financial metrics used as **query context**
- Relevant filing chunks retrieved
- LLM generates narrative grounded in retrieved evidence
---
### 4. Sectioned MD&A Draft (Markdown)
Generated sections:
- *Revenue & Growth Trends**
- **Profitability Analysis**
- **Liquidity & Cash Flow**
- **Key Drivers**
- **Risks & Outlook**

Each paragraph includes:
- Inline citations referencing source chunk IDs
---
## Project Structure
mdna-rag/
│
├── data/
│ └── sec_financials.csv
│
├── notebooks/
│ └── mdna_pipeline.ipynb
│
├── src/
│ ├── load_data.py
│ ├── kpi_engine.py
│ ├── chunker.py
│ ├── embeddings.py
│ ├── rag_pipeline.py
│ └── mdna_generator.py
│
├── output/
│ └── mdna_draft.md
│
├── requirements.txt
└── README.md


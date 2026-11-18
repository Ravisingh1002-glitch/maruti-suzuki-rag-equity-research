# maruti-suzuki-rag-equity-research
Institutional-grade RAG pipeline synthesizing Q2 FY27 equity research notes for Maruti Suzuki with ChromaDB and Gemini.
# Automated RAG-Based Equity Research Note Synthesizer (Maruti Suzuki Q2 FY27)

## Overview
An institutional-grade Retrieval-Augmented Generation (RAG) pipeline built to eliminate LLM hallucinations in financial analysis. The system ingests raw quarterly earnings call transcripts, vectorizes semantic chunks into ChromaDB via HuggingFace embeddings, retrieves targeted fundamental disclosures, and synthesizes 2-page 'Initiating Coverage' research notes grounded strictly in verified transcript text and proprietary DCF model parameters.

## Key Features
- **Zero Hallucination Guardrails:** Restricts the LLM context strictly to retrieved transcript chunks and pre-computed DCF inputs (Bear Case Target: INR 9,500; Bear COGS: 82.5%).
- **Multi-Query Deduplication:** Queries 6 fundamental dimensions (margin compression, commodity inflation, settlement lag shifts, capacity expansions, sales volumes) and deduplicates chunks to maximize signal-to-noise ratio.
- **Resilient AI Failover Architecture:** Features an automated exponential backoff and multi-model retry loop (`gemini-3.8-flash` -> `gemini-3.6-flash` -> `gemini-2.5-flash-lite`) to bypass server capacity spikes.
- **Automated Numerical Audit:** Runs Regex parsing on generated outputs to cross-check numbers against source disclosures.
- **ReportLab PDF Publishing:** Automatically compiles the final report into a publication-quality A4 PDF complete with valuation summary tables and compliance footers.

## Tech Stack
- **Python**, **Google GenAI SDK (`google-genai`)**
- **LangChain**, **ChromaDB** (Vector Database)
- **HuggingFace Embeddings (`all-MiniLM-L6-v2`)**
- **ReportLab** (Programmatic PDF Generation)

# PDF Multimodal RAG with Kimi

A multimodal RAG system that parses PDFs (text + tables + images), 
generates summaries via Kimi (Moonshot AI), and answers questions 
using retrieved context + vision.

## Problem
Traditional RAG only handles text. Academic papers contain critical 
information in tables (complexity comparison) and figures (model 
architecture). This project retrieves and reasons over all three 
modalities.

## Tech Stack
- PDF Parsing: `unstructured` (hi_res strategy, table structure inference)
- Embeddings: `BAAI/bge-small-en-v1.5` (local, zero API cost)
- Vector Store: `Chroma` with `MultiVectorRetriever` (summary→retrieve, original→return)
- LLM: `kimi-k2.6` via OpenAI-compatible API
- Image Understanding: Native vision API with base64 encoding

## Quick Start
```bash
pip install -r requirements.txt
export MOONSHOT_API_KEY=sk-xxx
python src/query.py "What is multi-head attention?"
```

## Result Example
<img width="1243" height="629" alt="截屏2026-05-19 16 57 14" src="https://github.com/user-attachments/assets/5d6b9b12-d4d7-4e09-9224-f0eb85d48421" />

## Roadmap

    [ ] Add async batch processing for image summarization
    [ ] Replace InMemoryStore with persistent docstore
    [ ] Add evaluation framework (RAGAS)
    [ ] Deploy as FastAPI service

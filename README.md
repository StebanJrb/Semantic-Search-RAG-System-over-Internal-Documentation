# Semantic Search & RAG System over Internal Documentation

## Overview
A RAG system for natural language Q&A over internal documentation. The focus is the engineering behind the LLM: automated ingestion, retrieval quality evaluation, chunking/embedding experimentation tracked in MLflow, and query monitoring via Airflow.

## Architecture
- **Document Ingestion**: Airflow DAG that watches for new documents, processes them (PDF/DOCX/Markdown), chunks with configurable strategies (fixed-size, semantic, recursive character splitting)
- **Embedding Pipeline**: Sentence-transformer models generating vector embeddings per chunk, stored in ChromaDB/Pinecone
- **Retrieval**: Vector similarity search with optional reranking (cross-encoder)
- **Generation**: Anthropic Claude API or OpenAI for answer synthesis with retrieved context
- **Evaluation**: Systematic retrieval quality metrics (Precision@K, Recall@K, MRR) and answer quality (faithfulness, relevance) tracked in MLflow
- **Monitoring**: Airflow DAG tracking queries with low retrieval scores, unanswered queries, and user feedback

## Tech Stack
- Python 3.11+, LangChain or LlamaIndex
- sentence-transformers (embedding models)
- ChromaDB or Pinecone (vector store)
- Anthropic API (Claude) or OpenAI
- MLflow (experiment tracking — chunking strategies, embedding models, retrieval configs)
- Apache Airflow 2.x (ingestion + monitoring)
- Docker & Docker Compose

## What This Demonstrates
- RAG architecture design and implementation
- Systematic retrieval evaluation methodology
- Chunking strategy impact analysis
- Embedding model selection and benchmarking
- Document processing pipeline automation
- Query monitoring and continuous improvement
- The engineering behind LLM applications

## Status
🚧 In Development

## Project Structure
├── dags/
│   ├── document_ingestion_dag.py
│   └── query_monitoring_dag.py
├── src/
│   ├── ingestion/
│   ├── chunking/
│   ├── embedding/
│   ├── retrieval/
│   ├── generation/
│   └── evaluation/
├── eval_datasets/
├── notebooks/
├── tests/
├── docker-compose.yml
└── README.md

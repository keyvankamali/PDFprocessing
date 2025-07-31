# MLOps Document Processing Pipeline

This project demonstrates a scalable MLOps pipeline using Azure services to extract text from PDFs, generate embeddings, and store the results for vector search.

##  Overview

When a PDF is uploaded to Azure Blob Storage, the system:
1. Automatically triggers a pipeline in **Azure Data Factory**
2. Passes the PDF path to a **Databricks notebook**
3. Parses the PDF, extracts text, generates embeddings (`BAAI/bge-m3`)
4. Stores embeddings and metadata in a **Delta Table**
5. Enables **vector search** using **Databricks Vector Search**

##  Architecture

- **Azure Blob Storage**: Stores uploaded PDF documents
- **Azure Data Factory**: Detects new file uploads and triggers the pipeline
- **Azure Databricks**: Processes documents in a notebook (PyMuPDF + HF model)
- **Delta Lake**: Stores output in scalable tabular format
- **Databricks Vector Search**: Powers semantic search over documents

##  Folder Structure

##  Dependencies

- **Databricks Runtime** with ML (Python 3.10)
- Python packages:
  - `PyMuPDF` (PDF parsing)
  - `transformers`, `torch` (embedding model)
  - `pyspark`
  - `databricks-vector-search`

Install packages in your Databricks cluster via `%pip`:
```python
%pip install pymupdf torch transformers
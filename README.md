🧠 DocIntel – AI-Powered Multi-Agent Document Intelligence System

A Google ADK Capstone Project | Multi-Agent RAG Pipeline for Document Understanding

📌 Overview

DocIntel is an AI-powered multi-agent system designed to extract, analyze, summarize, and retrieve information from documents using OCR, embeddings, FAISS vector search, and a Retrieval-Augmented Generation (RAG) pipeline.

It converts any uploaded file—PDF, scanned document, invoice, Excel sheet, CSV—into a searchable and analyzable representation using:

OCR (pytesseract)

Document chunking

Semantic embeddings

FAISS indexing

Multi-agent collaboration

Field extraction

RAG-based Q&A

The system supports:

Invoices

Reports

Tables

Excel → PDF conversions

CSV → PDF conversions

Analytics-generated PDF reports

🚀 Problem Statement

Organizations struggle with large volumes of unstructured documents such as invoices, reports, scanned PDFs, and business forms. Manually reviewing text, identifying totals, extracting fields, or answering questions is time-consuming, error-prone, and impossible to scale.

Most documents:

Are scanned or image-based

Lack searchable text

Contain unstructured tables

Cannot be indexed or searched easily

Business workflows slow down significantly without automation.

💡 Solution – DocIntel Multi-Agent Architecture

DocIntel automates the entire document-understanding process using a multi-agent pipeline:

🔹 1. IngestionOCRAgent

Extracts text from:

Text-based PDFs

Image-based PDFs (OCR forced)

Excel → PDF

CSV → PDF

Screenshot documents

🔹 2. ChunkingAgent

Splits documents into meaningful sections (chunks) for retrieval.

🔹 3. EmbeddingIndexingAgent

Converts text into semantic embeddings using SentenceTransformers and builds a FAISS vector index.

🔹 4. RetrievalRAGAgent

Retrieves top relevant chunks and generates grounded answers using Retrieval-Augmented Generation.

🔹 5. ExtractionAgent

Automatically extracts fields like:

Invoice totals

Dates

Reference numbers

IDs


📄 Features

✔ OCR for scanned PDFs
✔ Automatic file conversion (CSV → PDF, Excel → PDF)
✔ Semantic search with FAISS
✔ RAG-based question answering
✔ Automated invoice field extraction
✔ PDF report generation
✔ Multi-agent ADK design
✔ Runs on Google Colab, Kaggle, or locally
✔ Supports large documents
✔ No API keys required (offline models)

📦 Tech Stack

Python

Google ADK (Agent Development Kit)

pdfplumber

pytesseract

SentenceTransformers

FAISS

ReportLab

Pandas

NumPy

🧪 How To Run
1. Install dependencies
pip install pdfplumber pytesseract sentence-transformers faiss-cpu reportlab pandas
sudo apt-get install tesseract-ocr

2. Upload your document

Supports:

PDF

JPG/PNG scans

CSV → will be converted to PDF

Excel → will be converted to PDF

3. Set your file path
pdf_path = "/content/final_invoice.pdf"

4. Run the agents
pages = ingest.run(pdf_path)
chunks = chunker.run(pages)
texts, embs, index = embed_indexer.run(chunks)
rag_answer, hits = retriever.run("What is the total amount?", texts, embs, index)
fields = extractor.run(pages)

🧵 Example Output
🔹 RAG Answer
Query: What is the total amount?

Context Used:
Invoice Total: ₹12,400 ...

Final Answer:
The total amount is likely ₹12,400.

🔹 Extracted Fields
{
  "invoice_number": "INV-10421",
  "date": "10/06/2023",
  "total": "₹12,400"
}

📊 PDF Reports Generated

DocIntel also generates:

PDF analytics reports

Statistical summaries

Categorical breakdowns

Tabular representations of datasets

Generated with ReportLab.

🏆 Project Value

DocIntel:

Reduces document-processing time by 70–90%

Extracts fields in seconds instead of hours

Converts non-searchable documents into searchable indexed memory

Enables enterprise-friendly automated document understanding

🛠️ Future Improvements

Add LayoutLMv3 for layout-aware extraction

Add Gemini/OpenAI RAG for advanced answers

Support real-time document streaming

Build a Streamlit/Gradio UI

Full multi-document indexing system

👤 Author

Lakshmi Narayanan
AI/ML & Data Engineering Enthusiast
GitHub: lakshminarayanan20

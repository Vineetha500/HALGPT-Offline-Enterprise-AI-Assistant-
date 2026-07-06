# HALGPT – System Design

## 1. Project Overview
HALGPT is a desktop-based AI assistant that enables users to upload documents and interact with them using natural language queries. It is built using a Retrieval-Augmented Generation (RAG) architecture to provide accurate, context-aware responses based on user-provided documents.

The system processes documents, converts them into embeddings, stores them in a vector database, retrieves relevant context based on user queries, and generates responses using a Large Language Model (LLM).

---

## 2. High-Level Architecture

HALGPT follows a modular pipeline architecture:

- Desktop GUI (Electron / Python UI)
- Document Upload Module
- Document Processing Pipeline
- Text Chunking Engine
- Embedding Generator
- Vector Database (LanceDB / FAISS)
- Retrieval System
- Large Language Model (Ollama / OpenAI / Local LLM)
- Response Generator

### Architecture Diagram
![Architecture](images/architecture.png)

---

## 3. System Workflow

1. User uploads a document (PDF, DOCX, TXT)
2. System extracts raw text from the document
3. Text is split into smaller overlapping chunks
4. Each chunk is converted into embeddings
5. Embeddings are stored in a vector database
6. User enters a query in the UI
7. Query is converted into an embedding
8. Similar chunks are retrieved using similarity search
9. Retrieved context is sent to the LLM
10. LLM generates a response using retrieved context
11. Response is displayed in the desktop application

---

## 4. System Components

### 4.1 Document Processing
Handles extraction of text from uploaded documents (PDF, DOCX, TXT). Ensures clean and structured text for processing.

---

### 4.2 Chunking Engine
Splits large documents into smaller overlapping chunks to improve retrieval accuracy and context retention.

---

### 4.3 Embedding Generation
Converts text chunks into vector embeddings using transformer-based models to capture semantic meaning.

---

### 4.4 Vector Database
Stores embeddings efficiently and supports fast similarity search for retrieving relevant document chunks.

---

### 4.5 Retrieval System
Performs semantic similarity search between query embeddings and stored document embeddings to retrieve relevant context.

---

### 4.6 LLM Integration
Uses a Large Language Model (Ollama / OpenAI / local model) to generate final responses based on retrieved context and user query.

---

## 5. Data Flow

User → Desktop UI → Document Upload → Processing → Chunking → Embeddings → Vector DB → Retrieval → LLM → Response → UI

---

## 6. Tech Stack

- Frontend: Electron / Python GUI  
- Backend: Python  
- LLM: Ollama / OpenAI / Local Models  
- Embeddings: Sentence Transformers / OpenAI Embeddings  
- Vector DB: LanceDB / FAISS  
- Document Parsing: PyPDF2 / python-docx  

---

## 7. Key Features

- Offline document Q&A system  
- RAG-based architecture for accurate answers  
- Fast semantic search using vector embeddings  
- Desktop application with simple UI  
- Support for multiple file formats  

---

## 8. Design Decisions

- Vector database used instead of keyword search for semantic understanding  
- Chunking improves retrieval accuracy and reduces token limits  
- RAG reduces hallucination in LLM responses  
- Local LLM support ensures privacy and offline usage  

---



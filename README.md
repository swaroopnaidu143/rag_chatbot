# 🤖 Context-Aware RAG Chatbot

---

## 1. Introduction

Large Language Models (LLMs) provide powerful conversational capabilities, but they can struggle with hallucinations, private or external information, and maintaining context across multiple interactions. This project implements a **Context-Aware Retrieval-Augmented Generation (RAG) Chatbot** that generates responses using information retrieved from a trusted knowledge source while preserving conversational context.

The application is developed using **LangChain v1.0+**, **OpenAI**, **FAISS**, and **Streamlit**, following current LangChain practices and avoiding deprecated interfaces.

---

## 2. Problem Statement

Conventional LLM chatbots face several challenges:

- They cannot consistently provide answers based on specific external documents
- They may generate information that is not supported by the available knowledge
- Follow-up questions can lose their meaning without proper conversation context
- Poor interface design and unsafe API-key handling can affect usability and security

This project aims to address these challenges by creating a conversational RAG system that retrieves relevant information from a trusted knowledge base, preserves previous conversation context, and provides a simple user interface.

---

## 3. Objective

The main objectives of this project are to:

- Develop a **context-aware conversational chatbot using RAG**
- Answer user questions using information retrieved from an external knowledge source
- Preserve conversation history for multi-turn interactions
- Improve response reliability by grounding generated answers in retrieved content
- Implement the application using **LangChain v1.0+ and LCEL**
- Provide a simple, secure, and user-friendly chatbot interface

---

## 4. System Architecture

### Main Components

1. **User Interface — Streamlit**
   - OpenAI API key input
   - Interactive chat interface
   - Chat history clearing option

2. **Data Ingestion**
   - Uses WebBaseLoader to retrieve content from the Wikipedia Artificial Intelligence page

3. **Text Processing**
   - Uses RecursiveCharacterTextSplitter to divide retrieved content into manageable chunks

4. **Vector Store**
   - FAISS stores document embeddings and performs similarity-based retrieval

5. **Embedding Model**
   - OpenAI `text-embedding-3-small` converts text into vector representations

6. **Language Model**
   - OpenAI `gpt-4o-mini` generates responses using the retrieved context

7. **RAG Pipeline — LCEL**
   - Reformulates contextual questions
   - Retrieves relevant document sections
   - Generates responses grounded in the retrieved information

---

## 5. Methodology / Workflow

1. **API Key Setup**
   - The user provides an OpenAI API key through the Streamlit interface
   - Chat functionality becomes available after the key is provided

2. **Knowledge Ingestion**
   - The selected Wikipedia Artificial Intelligence page is loaded and processed

3. **Document Chunking**
   - Retrieved content is divided into overlapping text segments to improve retrieval quality

4. **Embedding Generation**
   - Text chunks are transformed into vector embeddings
   - The resulting vectors are indexed using FAISS

5. **Question Processing**
   - When previous conversation exists, the user's question is converted into a standalone query

6. **Relevant Content Retrieval**
   - FAISS performs semantic similarity search to identify relevant document chunks

7. **Response Generation**
   - The LLM generates a concise answer based on the retrieved context

8. **Conversation Management**
   - Streamlit session state maintains the conversation history throughout the session

---

## 6. Key Features

- Context-aware multi-turn conversations
- Retrieval-Augmented Generation architecture
- Modern LangChain LCEL-based implementation
- Secure API key input through the application interface
- Chat history reset functionality
- Cached vector store for improved application performance

---

## 7. Technology Stack

- **Language:** Python 3.10+
- **Frontend:** Streamlit
- **LLM Framework:** LangChain v1.0+
- **Vector Store:** FAISS
- **LLM & Embeddings:** OpenAI

---

## 8. Installation & Setup

```bash
# Clone the repository
git clone https://github.com/your-username/context-aware-rag-chatbot.git
cd context-aware-rag-chatbot

# Create a virtual environment
python -m venv venv

# Activate the environment
source venv/bin/activate       # Linux/Mac
venv\Scripts\activate          # Windows

# Install required packages
pip install -r requirements.txt

# Launch the Streamlit application
streamlit run app.py

# Retrieval-Augmented Generation (RAG) System for Document Analysis
![image](https://github.com/user-attachments/assets/be191f0a-b614-41de-ac50-c3c7f9df91bb)

## Overview

This project implements a Retrieval-Augmented Generation (RAG) system, which extracts text from uploaded PDF and Word documents, processes it, and answers specific questions using OpenAI's language models. The core functionality involves text extraction, chunking the text into smaller segments, and using FAISS for similarity-based document retrieval to answer queries.

### Key Features:
1. **Document Upload and Text Extraction**  
   Upload PDF or Word (.docx) files, and the system extracts text using `PyMuPDF` (`fitz`) for PDFs and `docx2txt` for Word documents.

2. **Question-Answering System**  
   The extracted text is chunked, indexed with FAISS, and fed into a question-answering chain powered by OpenAI's language models to provide precise answers to user queries. 🧠💬

3. **Embeddings and Retrieval**  
   The project uses OpenAI's embeddings to vectorize the document chunks and FAISS to perform similarity searches on the chunks, ensuring relevant information is retrieved for any question.

## Technologies Used:
- **Django**: Backend web framework.
- **LangChain**: For constructing the question-answering chain and managing the document retrieval system.
- **FAISS**: Facebook AI's similarity search library for efficient text retrieval.
- **OpenAI API**: For generating embeddings and language model-based question answering.
- **PyMuPDF (`fitz`)**: For extracting text from PDF documents.
- **docx2txt**: For extracting text from Word documents.

## How the System Works:
1. **Upload a Document**  
   Users can upload either PDF or Word documents through a web interface.

2. **Text Extraction**  
   Depending on the file type, the system extracts the text using the appropriate library.

3. **Chunking**  
   The extracted text is split into manageable chunks using LangChain's `CharacterTextSplitter`.

4. **Embedding and Retrieval**  
   Each chunk is embedded using `OpenAIEmbeddings`, and FAISS is used to search for the most relevant chunks based on a user query.

5. **Question Answering**  
   The retrieved chunks are passed to a question-answering chain, which uses OpenAI's language model to generate a response based on the relevant document sections.

## How to Run the Project

### Prerequisites
Make sure you have Python installed and set up a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository_url>
   ```

2. **Navigate to the project directory**:
   ```bash
   cd <project_directory>
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Add your OpenAI API key**:
   Update your environment variables or `.env` file with your OpenAI API key:
   ```bash
   export OPENAI_API_KEY="your_openai_api_key"
   ```

### Apply migrations:

```bash
python manage.py migrate
```

### Run the server:

```bash
python manage.py runserver
```

### Access the application:
Navigate to `http://127.0.0.1:8000/` to upload documents and test the question-answering functionality.

## Example API Request

1. **Upload Document**: Upload a PDF or DOCX file.
2. **Ask a Question**: Enter a specific question related to the document content.
3. **Get a Response**: The system retrieves relevant document sections and generates an answer based on the document content.

---

# Advanced RAG System with LangGraph

An interactive document question-answering application built using **Retrieval-Augmented Generation (RAG)**, LangGraph, Streamlit, Groq and ChromaDB.

Upload documents, ask natural-language questions, retrieve relevant information and generate context-aware answers using an LLM-powered workflow.

> This project is an adaptation and extension of an existing open-source implementation. Original repository: [Advanced-RAG-LangGraph](https://github.com/chitralputhran/Advanced-RAG-LangGraph) by Chitral Puthran.

## Features

- **Multi-format document upload:** Supports PDF, Word, Excel, CSV and text-based documents.
- **Document processing:** Extracts text and divides content into smaller chunks.
- **Vector embeddings:** Uses Hugging Face sentence-transformer embeddings.
- **Vector database:** Stores and retrieves document embeddings using ChromaDB.
- **Semantic retrieval:** Finds relevant document content based on user queries.
- **LLM-powered answers:** Uses Groq-hosted language models.
- **LangGraph orchestration:** Coordinates retrieval, document evaluation and answer generation.
- **Online search fallback:** Integrates Tavily for external search when document information is insufficient.
- **Interactive interface:** Provides a Streamlit-based user interface.

## Technology Stack

| Component | Technology |
|---|---|
| Programming language | Python |
| User interface | Streamlit |
| LLM orchestration | LangChain |
| Workflow management | LangGraph |
| LLM provider | Groq |
| Language model | Qwen |
| Embeddings | Hugging Face Sentence Transformers |
| Vector database | ChromaDB |
| Online search | Tavily |
| Data validation | Pydantic |

## Architecture

The application follows a retrieval-augmented generation workflow:

1. **Document Upload:** The user uploads a supported document.
2. **Text Extraction:** The document loader extracts its textual content.
3. **Chunking:** Extracted text is divided into smaller chunks.
4. **Embedding Generation:** Hugging Face generates vector representations of the chunks.
5. **Vector Storage:** ChromaDB stores the embeddings for semantic retrieval.
6. **Question Processing:** The user's question enters the LangGraph workflow.
7. **Document Retrieval:** Relevant document chunks are retrieved.
8. **Relevance Evaluation:** The retrieved information is evaluated against the question.
9. **Answer Generation:** The LLM generates a response using relevant context.
10. **Fallback and Validation:** The workflow can route to online search and perform additional answer-quality checks.

### Workflow Diagram

![LangGraph Workflow](screenshots/graph.png)

## Project Structure

```text
Advanced-RAG-LangGraph/
│
├── app.py
├── config.py
├── document_loader.py
├── document_processor.py
├── multimodal_loader.py
├── rag_workflow.py
├── state.py
├── ui_components.py
├── utils.py
│
├── chains/
│   ├── document_relevance.py
│   ├── evaluate.py
│   ├── generate_answer.py
│   └── question_relevance.py
│
├── screenshots/
│   ├── document-upload.png
│   ├── evaluations.png
│   ├── graph.png
│   ├── langsmith-tracing.png
│   └── qa-interface.png
│
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/saksham2085/-Advanced-RAG-LangGraph.git

cd -Advanced-RAG-LangGraph
```

### 2. Create a virtual environment

**Windows:**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If dependency resolution fails, install the compatible packages listed in the project configuration and resolve version conflicts before running the application.

### 4. Configure environment variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
```

Optional LangSmith tracing variables can be configured if tracing is enabled in the application.

**Never upload your `.env` file or expose API keys publicly.**

### 5. Run the application

```bash
streamlit run app.py
```

Open the application at:

```text
http://localhost:8501
```

## Application Screenshots

### Document Upload

![Document Upload](screenshots/document-upload.png)

### Question and Answer Interface

![Q&A Interface](screenshots/qa-interface.png)

### Evaluation Results

![Evaluation Results](screenshots/evaluations.png)

### LangGraph Workflow

![Graph Architecture](screenshots/graph.png)

## Current Development Status

The application interface, document upload, retrieval and basic document-based question answering have been tested locally.

The online-search fallback and all structured-output evaluation paths are still undergoing validation. Results may depend on the selected Groq model and compatible package versions.

## Future Improvements

- Improve structured-output reliability across all evaluation chains.
- Add robust error handling and retry limits.
- Improve retrieval quality through advanced chunking and reranking.
- Add support for more document formats.
- Expand evaluation and testing coverage.
- Improve response latency and retrieval performance.

## Acknowledgements

This project is adapted from [Advanced-RAG-LangGraph](https://github.com/chitralputhran/Advanced-RAG-LangGraph), originally created by **Chitral Puthran**.

The original implementation is distributed under the MIT License. The original copyright and permission notice are retained in the repository's `LICENSE` file.

## License

This repository retains the original MIT License and its applicable copyright and permission notices.

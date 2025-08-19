# SmartRAG-QA-Pipeline
**Intelligent Document Question-Answering System with Adaptive Retrieval**

SmartRAG is a Retrieval-Augmented Generation system that combines _Google's Gemini AI_ with intelligent document processing to provide accurate, source-backed answers from document collections. It leverages _LangChain_ to create a modular pipeline for document ingestion, retrieval, and question-answering, enabling seamless integration of document retrieval with LLM reasoning.

## Main Features

- **Smart Relevance Filtering**: Advanced multi-stage filtering prevents irrelevant responses
- **Intelligent Metadata Extraction**: Automatically extracts titles, keywords, and summaries
- **Adaptive Document Retrieval**: Dynamic similarity thresholds and semantic matching
- **Source Attribution**: Tracks and cites document sources for transparency
- **Batch Processing**: Handle multiple queries efficiently
- **Robust Error Handling**: Comprehensive logging and exception management
- **Configurable**: Easily adjustable parameters for different use cases


## Requirements

- Python 3.8+
- Google AI API key (Gemini)
- PDF documents for processing

### Dependencies

```
langchain>=0.3.0
langchain_community
langchain_core
langchain-google-genai
langchain_chroma
pypdf
chromadb
```

## Configuration

Configuration class for easy customization:

```python
config = RAGConfig(
    file_path="document.pdf",
    api_key="your-google-api-key",
    
    # Model settings
    model_name="gemini-2.5-flash-lite",
    embedding_model="models/embedding-001",
    temperature=0.0,
    
    # Document processing
    chunk_size=500,
    chunk_overlap=150,
    min_page_words=20,
    
    # Retrieval settings
    retrieval_k=3,
    score_threshold=0.3,  # Higher = more selective
    adaptive_threshold=True,
    min_relevant_docs=1,
    
    # Performance
    metadata_extraction_delay=2.0,
    persist_directory="./chroma_db"
)
```

## Advanced Features

### Adaptive Relevance Filtering

SmartRAG uses multiple filtering stages to ensure high-quality responses:

1. **Similarity Threshold**: Vector similarity scoring
2. **Word Overlap Analysis**: Lexical matching between query and documents
3. **Keyword Matching**: Metadata-based relevance checking
4. **Semantic Domain Matching**: Domain-specific term clustering

### Source Attribution

When enabled, the system returns the document title, page number, and relevant keywords for each source used in generating the response. Sources are only provided when the system has sufficient confidence in the answer quality.

## Used Libraries

<p align="left"><img src="https://www.python.org/static/community_logos/python-logo.png" alt="Python" width="100"/>
<img src="https://registry.npmmirror.com/@lobehub/icons-static-png/latest/files/dark/langchain-color.png" alt="LangChain" width="50"/>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8f/Google-gemini-icon.svg/2048px-Google-gemini-icon.svg.png" alt="Google Gemini" width="30"/>
</p>

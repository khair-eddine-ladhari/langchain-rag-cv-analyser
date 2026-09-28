# LangChain RAG CV Analyser

A small  practice project that uses Retrieval-Augmented Generation (RAG) to analyse a CV. The CV text is split and stored in a Pinecone vector index, relevant parts are retrieved with semantic search, and a Groq-hosted LLM generates answers grounded in that retrieved context.

> **Status:** learning project. Built to practise RAG with LangChain, so the code is simple and not production-ready.

## How it works

1. **Upload:** the CV text (`cv.txt`) is chunked, embedded, and stored in a Pinecone index.
2. **Retrieve:** for each question, the most relevant chunks are found with semantic search.
3. **Generate:** the retrieved chunks are passed to a Groq LLM, which answers using only that context.

## Tech stack

- Python
- LangChain
- Pinecone (vector database)
- Groq (LLM)

## Project structure

| File | Purpose |
|------|---------|
| `upload_cv.py` | Loads the CV and uploads its embeddings to Pinecone |
| `index.py` | Creates and sets up the vector index |
| `cv_analyses.py` | Runs the CV analysis: retrieval plus LLM answer |
| `cv.txt` | Sample CV used for testing |
| `document.txt` | Sample document used for testing the RAG pipeline |
| `requirements.txt` | Python dependencies |

## Setup

```bash
git clone https://github.com/khair-eddine-ladhari/langchain_rag_tast.git
cd langchain_rag_tast
pip install -r requirements.txt
```

Create a `.env` file in the project folder (never commit it):

```
PINECONE_API_KEY=your_pinecone_key
GROQ_API_KEY=your_groq_key
```

## Run

```bash
python index.py         # 1. create the index
python upload_cv.py     # 2. upload the CV
python cv_analyses.py   # 3. analyse the CV
```

## What I learned

- How chunking, embeddings, and vector search fit together in a RAG pipeline
- Connecting LangChain with Pinecone and Groq
- Keeping answers grounded in retrieved context instead of the model's memory

## Possible improvements

- Add a simple interface (Streamlit or FastAPI)
- Support PDF uploads
- Add evaluation of answer quality

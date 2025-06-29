# Semantic Webpage Search Backend

This backend powers a system that lets you semantically search through webpage content using vector embeddings, LangGraph, and a local LLaMA model via Ollama.

## File Overview

### 1_llama_test.ipynb  
Tests that the Ollama LLaMA model works locally.  
Runs basic prompts to make sure `.invoke()` responses are working.  
Also checks how LLaMA can evaluate text or rewrite a query.

### 2_scraper.ipynb  
Grabs the visible text content from a test website using Python.  
Strips HTML and returns plain text that represents the body of a webpage.  
This simulates what the Chrome extension would send.

### 3_load_content.ipynb  
Splits the page text into chunks.  
Embeds each chunk using HuggingFace embeddings.  
Stores all embeddings in a FAISS vector database for fast semantic search.

### 4_semantic_search.ipynb  
Takes a user query and performs semantic search against the vector DB.  
Uses LLaMA to check if the results are relevant.  
If results are weak, rewrites the query and retries.  
Returns best-matching chunks.

## Dependencies
- Python 3.10+
- LangChain
- LangGraph
- Ollama (running a LLaMA model)
- FAISS
- HuggingFace Transformers

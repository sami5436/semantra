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

---

### 4a_query_search.ipynb  
Takes a raw user query.  
Performs a top-k similarity search in the vector database.  
Returns the top chunks as preliminary matches.

### 4b_llama_check_accuracy.ipynb  
Uses LLaMA to evaluate whether the top chunks are relevant to the query.  
LLaMA returns a yes/no judgment and justification ("These chunks seem unrelated because...").

### 4c_query_rewrite_and_retry.ipynb  
If the results are poor, asks LLaMA to rewrite or clarify the query.  
Repeats the vector search using the new version of the query.  
Loops until the matches are deemed acceptable or a retry limit is reached.

### 4d_summarize_results.ipynb  
Passes the validated chunks back to LLaMA for final summarization.  
Formats a clean final answer for the user along with context references.

---

## Dependencies
- Python
- LangChain
- LangGraph
- Ollama (running a LLaMA model)
- FAISS
- HuggingFace Transformers
- BeautifulSoup (for scraping)
- undetected-chromedriver (for Cloudflare-protected sites)

```
semantra/
├── README.md                          # Project overview and usage guide
├── extension/                         # Microsoft Edge extension frontend
│   ├── manifest.json                  # Edge extension configuration
│   ├── popup.html                     # Extension popup UI
│   ├── popup.js                       # Handles user interaction
│   ├── styles.css                     # Styling for extension UI
│   └── content_script.js              # Injected script to capture webpage text
│
├── backend/                           # Flask-based LangGraph API backend
│   ├── app.py                         # Flask app entry point
│   ├── config/                        # App config and settings
│   │   ├── __init__.py
│   │   └── settings.py
│   ├── langgraph_engine/             # LangGraph graph definition and nodes
│   │   ├── __init__.py
│   │   ├── graph.py                   # Defines LangGraph workflow
│   │   ├── nodes/
│   │   │   ├── __init__.py
│   │   │   ├── preprocess.py          # Chunking, embedding
│   │   │   ├── query_search.py        # Vector DB top-k match
│   │   │   ├── relevance_check.py     # LLaMA checks relevance
│   │   │   ├── rewrite_retry.py       # Rewrite poor queries
│   │   │   └── summarize.py           # Final summarization
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── scraper.py                 # HTML to plain text
│   │   ├── embedding.py               # Embedding logic
│   │   └── db.py                      # FAISS DB ops
│   ├── vectordb/                      # Stored vector indexes (auto-generated)
│   └── requirements.txt              # Python dependencies
│
├── output/                            # Intermediate and final results
│   ├── extracted_text.txt             # Raw text from webpage
│   ├── retrieved_chunks.json          # Matched content
│   ├── summary.txt                    # Final summarized answer
│   └── debug_log.txt                  # Optional logs
└── research/                          # Optional: experimental notebooks or scripts
    ├── query_tests.ipynb
    └── model_eval.ipynb
```

#  RAG-based PDF Question Answering Agent

This project is a **Retrieval-Augmented Generation (RAG)** system that enables users to interact with the contents of PDF documents through natural language queries. The system uses **LangGraph**, **LangChain**, and **Google Generative AI** to perform source-aware document retrieval and intelligent response generation.

---

##  Features

-  Multi-PDF Support – Upload and process multiple PDF documents.
-  Contextual Retrieval – Uses semantic embeddings and vector search (ChromaDB) to find the most relevant chunks.
-  LLM Integration– Utilizes Google's Generative AI model for human-like answers.
-  Custom Tools– Modular tools for loading, embedding, and querying documents.
- LangGraph Architecture – Graph-based state management with memory for multi-turn conversations.

---

##  Project Structure


rag\_agent/
│
├── rag\_agent.ipynb         # Main notebook containing the full pipeline
├── chroma\_index/           # Vectorstore persistence directory
├── .env                    # Environment variables (e.g., API keys)
└── requirements.txt        # All required dependencies


---

##  How It Works

1. **Document Ingestion**
   - Loads PDF documents using `PyMuPDF`.
   - Splits them into chunks using `RecursiveCharacterTextSplitter`.
   - Embeds them with HuggingFace's `sentence-transformers`.
   - Stores vectors in a persistent ChromaDB.

2. **Query Pipeline**
   - User enters a query.
   - The system retrieves the top-k most relevant chunks.
   - Google GenAI formulates a response using retrieved context.

3. **LangGraph Agent**
   - Manages tool calling, AI/Tool responses, and message flow.
   - Includes memory using `MemorySaver`.

---

## Installation

```bash
# Clone the repo
git clone https://github.com/your-username/rag-agent.git
cd rag-agent

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install requirements
pip install -r requirements.txt
````

---

##  Usage

1. Place your PDF files in a directory (e.g., `pdfs/`).
2. Load and embed documents by calling:

```python
document_load_embed_store("pdfs/your_file.pdf")
```

3. Ask a question:

```python
retrieve_similar_documents("What is the main topic of the document?")
```

4. Use the LangGraph agent to manage conversation flows and responses.

---

##  Environment Variables

Create a `.env` file with the following:

```env
GOOGLE_API_KEY=your_google_genai_key
```

---

##  Requirements

* `langchain`
* `langgraph`
* `chromadb`
* `sentence-transformers`
* `langchain-google-genai`
* `PyMuPDF`
* `python-dotenv`

Install them using:

```bash
pip install -r requirements.txt
```

---

##  TODO

* [ ] Add support for table/image extraction from PDFs
* [ ] Deploy as a web app (Streamlit or FastAPI)
* [ ] Enable voice input/output integration

---


##  Acknowledgements

* [LangChain](https://www.langchain.com/)
* [LangGraph](https://github.com/langchain-ai/langgraph)
* [ChromaDB](https://www.trychroma.com/)
* [Google Generative AI](https://ai.google/discover/generative-ai/)



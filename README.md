Enterprise Knowledge RAG Assistant
A production-style Retrieval-Augmented Generation (RAG) system built using LangChain, Pinecone, and Streamlit.
The system answers user queries strictly grounded in ingested documents, demonstrating clean architecture, incremental ingestion, and real-world usability.

This project is intentionally designed as a maintainable AI system, not a chatbot demo.

🔍 Key Features
Incremental PDF ingestion (no Pinecone index reset)
Vector-based semantic search using Pinecone
Retrieval-Augmented Generation (RAG) with LangChain
Clean system entrypoint reusable across CLI and UI
Streamlit-based interactive UI
Transparent source attribution
Modular, production-aligned project structure
🧠 Architecture Overview

Streamlit UI
↓
System Entrypoint (main.py)
↓
RAG Chain (LangChain)
↓
Retriever + Prompt + LLM
↓
Pinecone Vector Store

Design Principles

UI is a thin client (no business logic)
All orchestration flows through main.py
RAG logic is isolated and reusable
Data ingestion is incremental and safe
📂 Project Structure

enterprise-rag-assistant/
│
├── app/
│   ├── chains/          # RAG chain logic
│   ├── config/          # Configurations
│   ├── embeddings/      # Embedding logic
│   ├── ingestion/       # PDF loading, chunking, ingestion
│   ├── retriever/       # Pinecone retriever
│   ├── ui/              # Streamlit UI
│   ├── utils/           # Logger and helpers
│   └── main.py          # System entrypoint
│
├── data/
│   └── pdf/
│       └── langchain_deep_dive.pdf
│
├── requirements.txt
├── README.md
└── .gitignore

📘 Demo Data
The repository includes a 5+ page LangChain deep-dive PDF used to demonstrate:

Chunking quality
Cross-section retrieval
Concept-level grounding
Hallucination resistance
File:


data/pdf/langchain_deep_dive.pdf

🖥️ Offline / Local LLM Setup (Ollama + Nomic + LLaMA)
This project is designed to run fully offline after initial model setup, without relying on cloud-based LLM APIs.

🔧 Components Used
Ollama – Local LLM runtime
LLaMA-based model – Local language model for generation
nomic-embed-text – Local embedding model for vectorization
Pinecone – Vector database (can be replaced with local stores if required)
🧠 How Offline Execution Works
Once models are pulled locally, no internet connection is required for:

Query answering
Embedding generation
Retrieval-augmented generation
Streamlit UI interaction
All inference runs on the local machine.

🚀 Getting Started
1️⃣ Install Dependencies
pip install -r requirements.txt
2️⃣ Ingest Documents
python app/ingestion/ingest_pipeline.py
This appends documents to the existing Pinecone index without resetting it.

3️⃣ Run Streamlit UI
streamlit run app/ui/streamlit_app.py
4️⃣ (Optional) CLI Mode
python app/main.py
🧪 Example Demo Queries
Use these to validate RAG behavior:

What is LangChain and why is it used in production systems?
Explain how LangChain supports Retrieval-Augmented Generation.
What are agents in LangChain?
What are best practices for using LangChain in production?
Out-of-scope test:

What is quantum teleportation over blockchain?
(Expected: refusal or low-confidence response)

🛠 Key Design Decisions
Precision-first retrieval to reduce hallucinations
Incremental ingestion for production safety
UI kept separate from orchestration logic
No direct LLM calls from UI
No hardcoded prompt logic in frontend
📌 Use Cases
Enterprise document Q&A
Internal knowledge assistants
Policy and technical documentation exploration
Analyst and developer support tools
📈 Future Enhancements
Offline evaluation & regression tests
FastAPI service layer
Dockerized deployment
CI-based guardrails
Document versioning and metadata filtering
👤 Author
Built as a production-grade RAG system with emphasis on: architecture, correctness, and maintainability — not shortcuts

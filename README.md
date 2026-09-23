# LingoMagic Chatbot 🤖

An AI-powered customer support chatbot for LingoMagic, an online language learning platform.

## What it does

The chatbot answers customer questions based on the official FAQ documentation, using a **RAG (Retrieval-Augmented Generation)** architecture. It does not invent answers — it only responds using the provided knowledge base.

## Tech Stack

- **Python 3.12**
- **LangChain** — framework for LLM applications
- **Groq API** — fast and free LLM inference (model: `openai/gpt-oss-120b`)
- **HuggingFace Embeddings** — local embedding model (`all-MiniLM-L6-v2`)
- **ChromaDB** — vector database for semantic search

## How it works

1. The documents in `docs/` are loaded and split into chunks.
2. Each chunk is converted into a vector (embedding) and stored in ChromaDB.
3. When a user asks a question, the system finds the most relevant chunks.
4. These chunks are passed to the LLM, which generates an answer based only on them.

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/petersmuditha/lingomagic-chatbot.git
   cd lingomagic-chatbot

Create a virtual environment and install dependencies:

python -m venv venv
.\venv\Scripts\activate     # Windows
source venv/bin/activate    # macOS/Linux
pip install -r requirements.txt

Create a .env file with your Groq API key:

OPENAI_API_KEY=gsk_your_key_here

Get a free key at console.groq.com

Add your documents to docs/ (as .txt files)

Run the chatbot:

python main.py

Example Questions: 

How much does the Premium subscription cost?

How can I cancel my subscription?

What certifications do you offer?

I can't access a lesson, what should I do?
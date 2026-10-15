# RAG PDF Chatbot

A Retrieval-Augmented Generation (RAG) chatbot that answers questions from a pre-loaded PDF document. It uses a local LLM through Ollama, LangChain for the retrieval pipeline, and Gradio for the chat interface. Every answer comes with source page references.

> **Note:** The app currently works on a single fixed PDF (`rag.pdf`). Uploading a PDF from the chat UI is not supported yet (see Future Improvements).

## Features

- Ask questions about a pre-loaded PDF (`rag.pdf`) in natural language
- Answers are grounded in the document content, not just the model's memory
- Shows source file and page number for each answer
- Runs with a local LLM via Ollama (no paid API required)
- Simple chat UI built with Gradio

## Tech Stack

- **Language:** Python
- **Framework:** LangChain (`RetrievalQA`)
- **LLM:** Ollama (`llama3.2`)
- **Embeddings:** `nomic-embed-text`
- **Vector Store:** [Chroma]
- **Document Loader:** PyPDFLoader
- **UI:** Gradio

## How It Works

1. **Load:** the PDF is loaded page by page.
2. **Chunk:** text is split into overlapping chunks (`chunk_size=1000`, `chunk_overlap=200`).
3. **Embed and store:** each chunk is converted into an embedding and stored in a vector database.
4. **Retrieve:** for a user question, the most relevant chunks are fetched.
5. **Generate:** the LLM answers using the retrieved context, and the sources are shown.

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/mahak-025/rag-pdf-chatbot.git
cd rag-pdf-chatbot
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Install Ollama and pull the models

Download Ollama from [ollama.com/download](https://ollama.com/download), then run:

```bash
ollama pull llama3.2
ollama pull nomic-embed-text
```

### 4. Add your PDF

The app currently works on a single fixed PDF. Place your PDF in the project folder and name it `rag.pdf` (or change the file path in the notebook), then run the notebook. Uploading a PDF from the chat UI is not supported yet.

### 5. Run the notebook

Open `rag-chatbot.ipynb` in Jupyter or Google Colab and run all cells in order. The last cell launches the Gradio chat interface.

## Project Structure

```
rag-pdf-chatbot/
├── rag-chatbot.ipynb    # Main notebook
├── requirements.txt     # Python dependencies
├── .gitignore
└── README.md
```

## Example Questions

- What is RAG?
- Summarize this document.
- What are the key points in the document?

## Screenshots

![Chat UI](screenshots/placeholder.txt/chat.png)
![Chat UI](screenshots/chat1.png)

## Future Improvements

- PDF upload option in the Gradio UI (`gr.File`) so users can chat with their own documents
- Support for multiple PDFs
- Conversation memory
- Deployment on Hugging Face Spaces
- Migration to `create_retrieval_chain` (newer LangChain approach)

## Author

**Mahak Chouhan**
[GitHub](https://github.com/mahak-025) | [LinkedIn](https://linkedin.com/in/mahak-chouhan-684219275)

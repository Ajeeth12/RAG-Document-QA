# RAG Document Q&A with Groq (Llama 3) and FAISS

This is a **Streamlit app** that lets you **ask questions** from your local **PDF research papers** using a **RAG (Retrieval-Augmented Generation)** approach.  
It uses **LangChain**, **Groq Llama 3-8B-8192** model for answering, and **FAISS** for fast document retrieval.

---

## 📂 Project Structure

```
research_papers/        # Folder where your PDFs are stored
main.py                 # Main Streamlit app
.env                    # Environment variables (API keys) [ignored in GitHub]
.gitignore              # Ignore .env, __pycache__, etc.
requirements.txt        # (Optional) List of dependencies
README.md               # This file
```

---

## 🚀 How It Works

1. **Document Ingestion**: Load PDF documents from `research_papers/` using `PyPDFDirectoryLoader`.
2. **Text Splitting**: Split documents into chunks (1000 tokens, 200 overlap) using `RecursiveCharacterTextSplitter`.
3. **Embedding**: Convert chunks into embeddings using `OpenAIEmbeddings`.
4. **Vector Store**: Store embeddings into a FAISS vector database.
5. **Retrieval + Generation**:  
   - Retrieve relevant chunks based on your query.
   - Pass retrieved context to Groq's Llama 3 model to generate accurate answers.
6. **Interactive Streamlit App**:
   - Button to embed documents.
   - Text input to ask questions.
   - Expander to see retrieved document chunks.

---

## Setup Instructions

1. **Clone the repository**:

```bash
git clone https://github.com/Ajeeth12/RAG-Document-QA.git
```

2. **Create a virtual environment**:

```bash
python -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
```

3. **Install dependencies**:

```bash
pip install -r requirements.txt
```

> If you don't have a `requirements.txt`, manually install:
> ```bash
> pip install streamlit langchain langchain-openai langchain-groq langchain-community python-dotenv faiss-cpu
> ```

4. **Setup your `.env` file**:

Create a `.env` file in the root directory and add:

```
OPENAI_API_KEY=your-openai-api-key
GROQ_API_KEY=your-groq-api-key
```

✅ Your `.env` file is automatically loaded with `dotenv`.

5. **Place your PDFs** in the `research_papers/` folder.

6. **Run the Streamlit app**:

```bash
streamlit run main.py
```

---

## 🧹 Features

- 📚 Load and embed **multiple research papers**.
- 🧠 Ask questions based **only on the document content** (RAG approach).
- ⚡ **FAISS** vector search for fast retrieval.
- 🤖 **Groq Llama 3** model for high-quality answers.
- 🌟 Streamlit UI with document similarity expander.

---

## 📸 Demo

*(Add a screenshot here if you want)*  
Example:

> - Upload PDFs.
> - Embed documents.
> - Type: "What are the key contributions of this paper?"
> - See answer + matching document snippets!

---

## 📋 TODOs / Future Enhancements

- [ ] Add support for uploading PDFs dynamically via Streamlit.
- [ ] Add streaming responses (instead of waiting for full completion).
- [ ] Add multi-model support (Groq, OpenAI, Ollama, etc.)
- [ ] Save user queries and answers for session history.

---

## 🤝 Acknowledgements

- [LangChain](https://github.com/langchain-ai/langchain)
- [Streamlit](https://streamlit.io/)
- [Groq API](https://groq.com/)
- [FAISS - Facebook AI Similarity Search](https://faiss.ai/)

---

# ✨ License

This project is open-source and available under the [MIT License](LICENSE).

---


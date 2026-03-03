# 📦 Vector_Store_in_Langchain

A practical implementation of a **Vector Store using LangChain and ChromaDB** demonstrating:

- Document embedding using OpenAI
- Persistent vector database (Chroma)
- Similarity search
- Similarity search with scores
- Metadata filtering
- Document update
- Document deletion

This project shows how modern AI applications implement **semantic search and vector-based retrieval systems**.

---

# 🚀 Tech Stack

- Python
- LangChain
- ChromaDB
- OpenAI Embeddings
- Google Colab / Jupyter Notebook

---

# 🧠 What This Project Demonstrates

This notebook covers complete vector store lifecycle:

✅ Create Documents  
✅ Generate Embeddings  
✅ Store in Chroma Vector DB  
✅ Perform Similarity Search  
✅ Filter using Metadata  
✅ Update Documents  
✅ Delete Documents  
✅ Persistent Storage  

---

# 📂 Project Structure

```
Vector_Store_in_Langchain/
│
├── langchain_chroma.ipynb
└── README.md
```

---

# ⚙️ Installation

Install required packages:

```bash
pip install langchain chromadb openai tiktoken pypdf langchain_openai langchain-community
```

---

# 🔐 Environment Setup

Set your OpenAI API key:

```python
import os
os.environ["OPENAI_API_KEY"] = "your_openai_api_key"
```

---

# 🏗 Step-by-Step Implementation

## 1️⃣ Import Required Libraries

```python
from langchain_openai import OpenAIEmbeddings
from langchain.vectorstores import Chroma
from langchain.schema import Document
```

---

## 2️⃣ Create Documents

Example IPL player documents with metadata:

```python
doc1 = Document(
    page_content="Virat Kohli is one of the most successful batsmen...",
    metadata={"team": "Royal Challengers Bangalore"}
)
```

Documents include metadata such as team names for filtering.

---

## 3️⃣ Initialize Chroma Vector Store

```python
vector_store = Chroma(
    embedding_function=OpenAIEmbeddings(),
    persist_directory='my_chroma_db',
    collection_name='sample'
)
```

- `persist_directory` → saves DB locally
- `collection_name` → logical grouping

---

## 4️⃣ Add Documents

```python
vector_store.add_documents(docs)
```

Each document:
- Converted into embeddings
- Stored inside ChromaDB
- Assigned unique ID

---

## 5️⃣ View Stored Documents

```python
vector_store.get(include=['embeddings','documents','metadatas'])
```

Returns:
- Document IDs
- Embeddings
- Original text
- Metadata

---

## 6️⃣ Similarity Search

```python
vector_store.similarity_search(
    query="Who among these are a bowler?",
    k=2
)
```

This performs semantic search (not keyword-based).

---

## 7️⃣ Similarity Search with Score

```python
vector_store.similarity_search_with_score(
    query="Who among these are a bowler?",
    k=2
)
```

Returns:
- Matching document
- Similarity score

Lower score → More similar

---

## 8️⃣ Metadata Filtering

```python
vector_store.similarity_search_with_score(
    query="",
    filter={"team": "Chennai Super Kings"}
)
```

This filters documents based on metadata.

Very useful in:
- Enterprise search
- Multi-tenant systems
- Category-based retrieval

---

## 9️⃣ Update Document

```python
vector_store.update_document(
    document_id="document_id_here",
    document=updated_doc
)
```

Updates:
- Text
- Embeddings
- Metadata

---

## 🔟 Delete Document

```python
vector_store.delete(ids=["document_id_here"])
```

Removes document from vector database.

---

# 🧠 Key Concepts Covered

- Embeddings
- Vector Databases
- Semantic Search
- Cosine Similarity
- Metadata Filtering
- Persistent Vector Storage
- CRUD operations in Vector DB

---

# 🔍 Why Vector Databases Matter

Traditional databases:
- Exact keyword match

Vector databases:
- Meaning-based search
- Contextual retrieval
- Foundation of RAG systems

---

# 🚀 Real-World Use Cases

- AI Chatbots
- Knowledge Base Systems
- Enterprise Document Search
- Legal/Medical Document Retrieval
- Recommendation Systems
- Retrieval-Augmented Generation (RAG)

---

# 📌 Future Improvements

- Add RetrievalQA chain
- Convert to full RAG pipeline
- Add FastAPI backend
- Add Streamlit UI
- Deploy on cloud
- Add hybrid search (BM25 + Vector)

---

# 🏁 Conclusion

This project demonstrates how to build a **fully functional vector store using LangChain and ChromaDB**, including:

- Storage
- Retrieval
- Filtering
- Updating
- Deletion

It forms the foundation of modern AI-powered applications.

---

⭐ If you found this useful, consider starring the repository!

# 🚀 PageSense – Agentic RAG Chrome Extension

PageSense is an AI-powered Chrome Extension that enables users to chat with any webpage in real time. It extracts webpage content, builds a Retrieval-Augmented Generation (RAG) pipeline, and answers questions based on the page context. When the required information is unavailable on the webpage, the system autonomously performs a web search using an AI agent and returns an informed answer.

---

## 📌 Features

✅ Chat with any webpage

✅ Retrieval-Augmented Generation (RAG)

✅ Agentic Web Search Fallback

✅ Multi-turn Conversation Memory

✅ Fast Semantic Search with FAISS

✅ Chrome Extension Integration

✅ Real-time AI Responses using Groq

---

## 🏗️ System Architecture

<img width="1065" height="707" alt="Screenshot 2026-08-12 171215" src="https://github.com/user-attachments/assets/bf2a9424-3941-4e35-b82c-e8a829dbb6d6" />


# ⚙️ How It Works

### Step 1: Extract Webpage Content

The Chrome Extension captures the visible webpage text using:

```javascript
document.body.innerText
```

The content is sent to the FastAPI backend.

---

### Step 2: Text Chunking

Large webpages are divided into smaller chunks using:

```python
RecursiveCharacterTextSplitter
```

Configuration:

```python
chunk_size = 500
chunk_overlap = 50
```

---

### Step 3: Embedding Generation

Each chunk is converted into a dense vector representation using:

```python
BAAI/bge-small-en
```

via HuggingFace Embeddings.

---

### Step 4: Vector Storage

Embeddings are stored in:

```python
FAISS
```

which enables fast semantic similarity search.

---

### Step 5: Retrieval

When the user asks a question:

1. Query is embedded.
2. Similarity search is performed.
3. Top 3 relevant chunks are retrieved.

```python
k = 3
```

---

### Step 6: LLM Reasoning

Retrieved context, conversation history, and the user question are sent to:

```python
openai/gpt-oss-120b
```

running on Groq.

The model decides whether:

- The webpage context is enough.
- Additional web search is required.

---

### Step 7: Agentic Web Search

If information is unavailable on the webpage:

```python
web_search()
```

is automatically invoked.

The tool uses:

```python
DuckDuckGo Search
```

to retrieve real-time information.

Example:

```
User: Who won IPL 2026?

→ Context insufficient
→ Tool Call
→ DuckDuckGo Search
→ Final Answer
```

---

### Step 8: Conversation Memory

PageSense maintains conversation history using:

```python
collections.deque(maxlen=5)
```

Benefits:

- Multi-turn conversations
- Context-aware responses
- Low memory overhead

---

# 🧠 Algorithms & Techniques Used

| Component | Algorithm / Technique |
|------------|----------------------|
| Retrieval | Semantic Similarity Search |
| Embeddings | BGE Small Embeddings |
| Chunking | Recursive Character Splitting |
| Vector Database | FAISS |
| Memory | Sliding Window Memory |
| Agent | Tool Calling Agent |
| Search | DuckDuckGo Search |
| Generation | GPT-OSS-120B |

---

# 🛠️ Tech Stack

### Frontend

- HTML
- CSS
- JavaScript
- Chrome Extension (Manifest V3)

### Backend

- Python
- FastAPI
- Pydantic

### AI Stack

- LangChain
- Groq
- GPT-OSS-120B
- HuggingFace Embeddings

### Vector Database

- FAISS

### Search Tool

- DuckDuckGo Search (DDGS)

---

# 📂 Project Structure

```text
PageSense/
│
├── extension/
│   ├── manifest.json
│   ├── popup.html
│   ├── popup.js
│   └── styles.css
│
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   └── .env
│
└── README.md
```

---

# 🚀 Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/PageSense.git

cd PageSense/backend
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Add Environment Variables

Create a `.env` file:

```env
GROQ_API_KEY=your_api_key_here
```

### Run Backend

```bash
cd backend
python -m uvicorn main:app --reload
```

Server runs at:

```text
http://127.0.0.1:8000
```

---

# 🎯 Example Use Cases

### Website Q&A

```
What is LangChain?
```

### Summarization

```
Summarize this page in 5 points.
```

### Explanation

```
Explain this article in simple terms.
```

### Agentic Search

```
Who won IPL 2026?
```

```
What is today's date?
```

```
Latest AI news?
```
# OVERVIEW 
<img width="1913" height="1083" alt="Screenshot 2026-08-12 172711" src="https://github.com/user-attachments/assets/e1da5968-eac6-4d9e-92ec-6a0d49e02453" />




---

# 📈 Future Improvements

- Persistent FAISS Indexing
- PDF & Document Support
- Multi-Modal RAG
- Voice Interaction
- Citation-Based Responses
- Streaming Responses
- Cloud Deployment

---

# 👨‍💻 Author

**Siddhartha Sangani**

B.Tech CSE (AI & ML)

Joginpally B.R. Engineering College

Hyderabad, India

---

## ⭐ If you found this project useful, consider starring the repository.

---

# 🧠 AI-Powered Multi-Agent Copilot WebUI

Engineered an AI-driven Copilot WebUI using Agentic AI, integrating multi-agent orchestration with OpenAI GPT-4o models via the Agno framework. Developed and deployed three specialized agents, leveraging hybrid vector search with LanceDB and OpenAI embedding models. Integrated DuckDuckGoTools for web augmentation.

---

## 🚀 Features

- ✨ **Multi-Agent Orchestration** with Agno’s Agent and Team APIs
- 🔍 **General Web Agent** for external data retrieval via DuckDuckGo
- 🏥 **Clinical Agent** powered by RAG (Retrieval-Augmented Generation) from medical PDFs
- 🌾 **Food Security Agent** using domain-specific PDFs and vector search
- ⚙️ **FastAPI Backend** for efficient API routing and orchestration
- 📚 **Hybrid Vector Search** with LanceDB and OpenAI Embeddings
- 🌐 **WebUI Interface** for seamless user interaction (React-based, separately hosted)

---

## 🧩 Architecture

```
                  +----------------------+
                  |      WebUI (React)   |
                  +----------+-----------+
                             |
                             ▼
               +-------------+--------------+
               |         FastAPI Backend     |
               |   (Agent Orchestration API) |
               +------+------+------+--------+
                      |      |      |
                      ▼      ▼      ▼
                 +--------+--------+--------+
                 | Web    | Clinical | Food |
                 | Agent  | Agent    | Agent|
                 +--------+--------+--------+
                      |      |      |
                      ▼      ▼      ▼
                 PDF RAG  PDF RAG  PDF RAG
               (VectorDB + OpenAI Embeddings)
```

---

## 🛠️ Tech Stack

| Layer            | Tools/Libraries                              |
|------------------|-----------------------------------------------|
| Language         | Python, JavaScript (React frontend)           |
| Backend Framework| FastAPI                                       |
| AI Models        | OpenAI GPT-4o (via Agno SDK)                  |
| Embeddings       | OpenAI `text-embedding-3-small`               |
| Vector DB        | LanceDB                                       |
| Knowledge Base   | PDF Documents (Clinical + Food Security)      |
| Search Tool      | DuckDuckGo (via Agno Tools)                   |

---

## 📂 Project Structure

```
.
├── agents/
│   ├── food_agent.py
│   ├── clinical_agent.py
│   └── web_search_agent.py
├── api/
│   └── main.py  # FastAPI app
├── data/
│   ├── clinical.pdf
│   └── food_security.pdf
├── requirements.txt
├── README.md
└── .env
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/yourusername/copilot-webui.git
cd copilot-webui
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Add Environment Variables

Create a `.env` file:

```
OPENAI_API_KEY=your_openai_api_key
```

### 4. Run the App

```bash
uvicorn api.main:app --reload
```

---

## 📘 Agent Definitions

### ✅ `food_agent`
- Uses a PDF-based knowledge base on food security
- Embedding via `OpenAIEmbedder`
- Hybrid search with LanceDB
- Augments missing data using DuckDuckGo

### ✅ `clinical_agent`
- Searches clinical datasets (PDFs) using RAG
- Tailored to respond to medical-related queries

### ✅ `web_search_agent`
- Focuses on generalized questions
- Uses DuckDuckGo search tools for real-time web data

---

## 🌐 Example Usage

Send a POST request to:

```
POST /query
{
  "message": "What are the latest developments in food security?"
}
```

Response:

```json
{
  "answer": "According to your knowledge base...",
  "agents_used": ["food_agent"]
}
```

---

## 🧠 Future Enhancements

- Add user authentication for secure access
- Frontend integration with chat interface
- Support additional domains (e.g., legal, finance)
- Agent performance analytics and feedback loop

---

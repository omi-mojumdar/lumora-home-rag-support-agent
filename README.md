# 🤖 Lumora Home — RAG Customer Support Agent

An AI-powered customer support agent built with n8n, Pinecone, and Google Gemini for a fictional e-commerce brand. It answers customer questions about products, shipping, returns, and policies instantly using Retrieval-Augmented Generation (RAG) — fully automated, zero manual work.

---

## 🚀 Demo

👉 [Watch Demo Video](https://drive.google.com/file/d/1vTvI_iqd1YlltGfOYkQlncpK34VeR68Q/view?usp=drive_link)

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| n8n | Workflow automation engine |
| Pinecone | Vector database for knowledge storage |
| Google Gemini | Embeddings + chat model |
| Google Drive | Knowledge base document storage |
| HTML / JavaScript | Chat frontend interface |
| n8n Webhook | Receives messages from the chat page |

---

## 🎯 Project Overview

E-commerce businesses struggle with:

❌ Support staff manually answering the same questions repeatedly  
❌ Slow response times outside business hours  
❌ Inconsistent answers from different team members  
❌ No scalable way to handle high enquiry volumes  
❌ Knowledge locked in documents nobody reads  

This system solves all of that:

✅ Instantly answers product, shipping, returns and payment questions  
✅ Retrieves answers only from the approved knowledge base  
✅ Responds 24/7 with no human needed for common queries  
✅ Falls back gracefully to support email for complex cases  
✅ Remembers conversation context within a session  

---

## ⚡ How It Works

```
Workflow A — Knowledge Ingestion
Google Drive (new file uploaded)
    ↓
Download File
    ↓
Default Data Loader (extract text)
    ↓
Recursive Character Text Splitter (chunk into ~500 token pieces)
    ↓
Embeddings Google Gemini (gemini-embedding-001 → 3072 dims)
    ↓
Pinecone Vector Store (index: lumorahomeecommerce)

Workflow B — Customer Support Agent
Website Chat → Webhook (POST: chatInput)
    ↓
AI Agent
    ├── Simple Memory (session context)
    ├── Google Gemini Chat Model (gemini-3.5-flash-lite)
    └── Pinecone Vector Store Tool (retrieve top 4 chunks)
        └── Embeddings Google Gemini (gemini-embedding-001)
    ↓
Respond to Webhook (return answer to chat page)
```

---

## 📷 Workflow Screenshot

<img width="1915" height="799" alt="image" src="https://github.com/user-attachments/assets/e6512644-97c3-4ecd-b372-56d02e5002bd" />


---

## 🔴 Workflow Nodes

### Workflow A — Ingestion (5 Nodes)

| Node | Name | Description |
|---|---|---|
| 1 | Google Drive Trigger | Fires when a new file is created in Drive |
| 2 | Download File | Downloads the knowledge base document |
| 3 | Default Data Loader | Extracts raw text from the file |
| 4 | Recursive Character Text Splitter | Splits text into chunks (500 tokens, 50 overlap) |
| 5 | Embeddings Google Gemini + Pinecone | Embeds chunks and stores in vector index |

### Workflow B — Support Agent (6 Nodes)

| Node | Name | Description |
|---|---|---|
| 1 | Webhook | Receives POST request from chat frontend |
| 2 | AI Agent | Orchestrates retrieval and response |
| 3 | Google Gemini Chat Model | Generates the answer (gemini-3.5-flash-lite) |
| 4 | Simple Memory | Maintains session conversation history |
| 5 | Pinecone Vector Store Tool | Retrieves top 4 relevant knowledge chunks |
| 6 | Respond to Webhook | Sends the answer back to the chat page |

---

## 📋 Knowledge Base Coverage (68 Chunks Indexed)

- Company overview and contact information
- Product catalog — Living Room & Lighting
- Product catalog — Kitchen & Dining
- Product catalog — Bedroom & Bath
- Shipping policy (domestic + international)
- Returns & refunds policy
- Payment methods and security
- Frequently asked questions (15 questions)
- Product care and maintenance guide
- Lumora Rewards loyalty program

---

## ✅ Demo Test Results

| Question | Result |
|---|---|
| "What is your return policy on furniture?" | ✅ Correct — 30 days, $99 White-Glove fee |
| "I received a damaged item, what do I do?" | ✅ Correct — email within 7 days with photos |
| "Do you sell candles?" | ✅ Correct — fallback triggered correctly |
| "Is the Moss Coffee Table top marble or wood?" | ✅ Correct — white marble, brass-finished base |

---

## 💡 What I Learned

- Building a two-workflow RAG architecture (ingestion + retrieval) in n8n
- Chunking and embedding documents into a Pinecone vector store
- Connecting a Webhook trigger to an AI Agent with tool use
- Using Google Gemini embeddings with 3072 dimensions
- Designing grounded AI responses with knowledge retrieval
- Building a working chat frontend connected to an n8n webhook
- Handling rate limits and model deprecation on free tier APIs

---

## 🔗 Links

- 📹 [Demo Video](https://drive.google.com/file/d/1vTvI_iqd1YlltGfOYkQlncpK34VeR68Q/view?usp=drive_link)
- 📁 [Workflow JSON](https://drive.google.com/file/d/16x9elAG9bgIGfC7TNYzqE1Endh8cbnlc/view?usp=drive_link)

---

## 👤 About Me

**Omi Mojumdar** — AI Automation Freelancer

- 🔗 [LinkedIn](https://linkedin.com/in/omi-mojumdar)
- 📧 omimojumdar88@gmail.com

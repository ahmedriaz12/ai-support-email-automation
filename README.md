# AI Customer Support Email Automation

### Multi-Agent Email Workflow using LangGraph + RAG + Gmail API

A production-ready AI customer support automation system built with **LangChain + LangGraph**.

This system monitors **Gmail**, classifies incoming emails, generates accurate responses using **Retrieval-Augmented Generation (RAG)**, verifies reply quality, and sends **approved replies automatically**.

---

## 1) Problem

Modern support teams often face:

* High email volume
* Repetitive product questions
* Slow response times
* Inconsistent reply quality

This project automates the full workflow using a **structured multi-agent architecture** where specialized agents collaborate to handle triage + response generation.

---

## 2) Architecture (LangGraph Workflow)

The system is implemented as a **LangGraph state machine**, where each node represents a specialized agent:

1. **Inbox Monitor** (Gmail API)
2. **Categorization Agent**
3. **RAG Retrieval Agent**
4. **Draft Generation Agent**
5. **Quality Assurance Agent**
6. **Email Sender**

Each step passes a structured state object forward to ensure a deterministic, production-style flow.

---

## 3) Key Features

### 3.1 Gmail Inbox Monitoring

* Continuously checks for new emails
* Extracts sender, subject, and body
* Fully automated once started

### 3.2 Intelligent Email Categorization

Classifies emails into:

* Customer Complaint
* Product Inquiry
* Customer Feedback
* Unrelated

Unrelated emails can be ignored automatically.

### 3.3 AI-Drafted Replies (RAG-Enabled)

* Drafts responses for complaints and feedback
* Uses **RAG** for product/service inquiries
* Generates structured, professional replies

### 3.4 Quality Assurance (QA) Agent

Before sending, every reply is validated for:

* Tone and clarity
* Relevance to the original message
* Formatting and completeness
* Missing/risky content

Only **approved** replies are sent automatically.

---

## 4) Tech Stack

* **LangGraph** (workflow orchestration)
* **LangChain** (LLM framework)
* **Groq** (Llama 3.1 70B)
* **Google Gemini** (embeddings)
* **Gmail API**
* **FastAPI + LangServe**
* **Python**

---

## 5) Project Structure

```text
langgraph-email-automation/
│
├── main.py               # Run workflow locally
├── deploy_api.py         # Deploy workflow as an API
├── create_index.py       # Build vector index for RAG
├── requirements.txt
├── .env
│
├── src/
│   ├── nodes.py          # LangGraph nodes (agents)
│   ├── prompts/          # Agent prompts
│   └── utils/            # Helpers (Gmail, parsing, etc.)
│
└── data/                 # Knowledge base documents for RAG
```

---

## 6) Installation

### 6.1 Prerequisites

* Python 3.8+
* Groq API Key
* Google Gemini API Key
* Gmail API credentials

### 6.2 Clone Repository

```bash
git clone https://github.com/ahmedriaz12/ai-support-email-automation.git
cd ai-support-email-automation
```

### 6.3 Create Virtual Environment

```bash
python -m venv venv
```

Activate:

**Mac/Linux**

```bash
source venv/bin/activate
```

**Windows**

```bat
venv\Scripts\activate
```

### 6.4 Install Dependencies

```bash
pip install -r requirements.txt
```

### 6.5 Environment Variables

Create a `.env` file in the project root:

```env
MY_EMAIL=your_email@gmail.com
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_gemini_api_key
```

### 6.6 Enable Gmail API

Enable Gmail API and download OAuth credentials (official guide):
[https://developers.google.com/gmail/api/quickstart/python](https://developers.google.com/gmail/api/quickstart/python)

---

## 7) Run Locally

```bash
python main.py
```

The system will:

* Check for new emails
* Categorize incoming messages
* Use RAG for inquiries (when needed)
* Run QA validation
* Send approved replies

---

## 8) Deploy as API

```bash
python deploy_api.py
```

Access:

* API: `http://localhost:8000`
* Swagger Docs: `http://localhost:8000/docs`
* Playground: `http://localhost:8000/playground`

---

## 9) Customization

### 9.1 Update Prompts

Edit prompts in:

```text
src/prompts/
```

### 9.2 Update Agent Logic

Modify node logic in:

```text
src/nodes.py
```

### 9.3 Add Knowledge Base Docs + Rebuild Index

1. Add files to:

```text
data/
```

2. Rebuild index:

```bash
python create_index.py
```

---

## 10) Future Improvements

* Human approval mode
* Ticketing system integration
* Attachment support
* Multi-language support
* Logging & monitoring
* Docker support
* Retry + rate-limit protection

---

## 11) License

MIT License

---

⭐ If you found this useful, consider starring the repository.

---

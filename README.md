# AI Customer Support Email Automation

### Multi-Agent Email Workflow using LangGraph + RAG + Gmail API

A production-ready AI-powered customer support automation system built with LangChain and LangGraph.

This system monitors Gmail, classifies incoming emails, generates accurate responses using Retrieval-Augmented Generation (RAG), verifies reply quality, and sends approved responses automatically.

---

## Overview

Modern support teams face:

- High email volume
- Repetitive product questions
- Slow response times
- Inconsistent reply quality

This project automates the entire workflow using a structured multi-agent architecture where specialized AI agents collaborate to handle email triage and response generation.

---

## Architecture

The system is built as a LangGraph workflow, where each node represents a specialized AI agent:

1. Inbox Monitor (Gmail API)
2. Categorization Agent
3. RAG Retrieval Agent
4. Draft Generation Agent
5. Quality Assurance Agent
6. Email Sender

Each step passes structured state to the next, ensuring deterministic flow and production-level reliability.

---

## Features

### Gmail Inbox Monitoring

- Continuously checks for new emails
- Extracts subject, sender, and body
- Runs fully automated once started

### 🗂 Intelligent Email Categorization

Classifies emails into:

- Customer Complaint
- Product Inquiry
- Customer Feedback
- Unrelated

Unrelated emails can be ignored automatically.

### AI Drafted Replies

- Drafts responses for complaints and feedback
- Uses RAG for product/service inquiries
- Generates structured, professional responses

### Quality Assurance Agent

Before sending, every email is verified for:

- Tone and clarity
- Relevance to original message
- Proper formatting
- Missing or risky information

Only approved emails are sent.

---

## Tech Stack

- LangGraph (Workflow Orchestration)
- LangChain (LLM Framework)
- Groq (Llama 3.1 70B)
- Google Gemini (Embeddings)
- Gmail API
- FastAPI + LangServe
- Python

---

## Project Structure

langgraph-email-automation/
│
├── main.py # Starts workflow locally
├── deploy_api.py # Deploys workflow as API
├── create_index.py # Builds vector store for RAG
├── requirements.txt
├── .env
│
├── src/
│ ├── nodes.py
│ ├── prompts/
│ └── utils/
│
└── data/

---

## ⚙️ Installation

### Prerequisites

- Python 3.8+
- Groq API key
- Google Gemini API key
- Gmail API credentials

### Clone Repository

git clone https://github.com/ahmedriaz12/ai-support-email-automation.git
cd ai-support-email-automation

### Create Virtual Environment

python -m venv venv

Activate:

Mac/Linux:
source venv/bin/activate

Windows:
venv\Scripts\activate

### Install Dependencies

pip install -r requirements.txt

### Environment Variables

Create a .env file in the root directory:

MY_EMAIL=your_email@gmail.com
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_gemini_api_key

### Enable Gmail API

Follow Google’s official guide to enable Gmail API and download credentials:
https://developers.google.com/gmail/api/quickstart/python

---

## Running Locally

python main.py

The system will:

- Check for new emails
- Categorize them
- Generate RAG-based responses if needed
- Verify quality
- Send approved emails

---

## Deploy as API

python deploy_api.py

Access:

- API: http://localhost:8000
- Swagger Docs: http://localhost:8000/docs
- Playground: http://localhost:8000/playground

---

## Customization

Modify agent prompts inside:
src/prompts/

Modify agent logic inside:
src/nodes.py

Add documents to /data and rebuild index:

python create_index.py

---

## Future Improvements

- Human approval mode
- Ticketing system integration
- Attachment support
- Multi-language support
- Logging & monitoring
- Docker support
- Retry & rate-limit protection

---

## License

MIT License

---

⭐ If you found this useful, consider starring the repository.

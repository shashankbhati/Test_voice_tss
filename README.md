Overview

This project is a voice-enabled AI agent prototype that demonstrates an end-to-end agentic workflow combining:

**Note:** I have changed my data as it was implented in my firm and have replaced with garbage data from chatgpt, also the function names

1. Speech-to-Text (ASR) using Deepgram
2. LLM reasoning + tool calling
3. Structured function execution (orders, drug lookup)
4. Text-to-Speech (TTS) voice response
5. Public endpoint exposure via ngrok

The goal is to simulate a real production-style conversational agent that can:

Answer your company related information questions

Place orders

Retrieve existing orders

Handle multi-turn dialogue through voice

This mirrors real agentic system architecture used in customer support, healthcare triage, and/or operations automation.

🏗️ Architecture
Voice Pipeline
User speech
   ↓
Deepgram ASR (speech → text)
   ↓
LLM reasoning + tool selection
   ↓
Python function execution (DB / logic)
   ↓
Response text
   ↓
Deepgram TTS (text → speech)
   ↓
Audio reply to user

Public Access

ngrok exposes the local FastAPI server securely to the internet

Enables webhook-based voice streaming and real-time testing

Agent Capabilities
1. Tool-Using Reasoning

The LLM can call structured functions:

get_info
place_order
lookup_order

This demonstrates agentic behavior:

Understanding intent
Selecting tools
Executing actions
Returning structured results

2. Stateful Interaction

Orders are stored in an in-memory database, allowing:
Multi-turn conversations
Order tracking
Context persistence during session

3. Voice Handling & Reliability

To improve real-world robustness:
Keyword boosting for drug names
Confirmation before order placement
Name spelling verification
Structured outputs to prevent hallucinations

**🛠️ Tech Stack**
Python / FastAPI – backend agent service

Deepgram – ASR + TTS voice pipeline

OpenAI-compatible LLM – reasoning & tool calling

ngrok – secure public tunneling

JSON function schema – structured tool interface

**Running the Project**

1. Install dependencies
pip install fastapi uvicorn requests python-dotenv

2. Set environment variables
DEEPGRAM_API_KEY=...
OPENAI_API_KEY=...

3. Start backend
uvicorn app.main:app --reload

4. Expose with ngrok
ngrok http 8000

**Purpose of This Project**

This prototype demonstrates core building blocks of production agentic systems:

Voice-enabled AI interaction

Tool-using LLM agents

Structured data integration

Real-time orchestration

External API connectivity

It serves as a foundation for scalable customer-ops or healthcare AI assistants.

# Step-by-Step Guide

Two separate chat setups. Pick whichever fits — local/offline or cloud.

## Part 1 — Local LLM Setup (dolphin-web)

Runs a model entirely on your own machine via Ollama. No API key, no internet needed once the model is pulled.

### 1. Install Ollama

Download and install from [ollama.com](https://ollama.com/). Confirm it works:

```bash
ollama --version
```

### 2. Pull the model

```bash
ollama pull dolphin-llama3
```

Ollama serves an API on `http://localhost:11434` by default — the app talks to it there.

### 3. Run the web app

```bash
cd "Local LLM Setup/dolphin-web"
pip install -r requirements.txt
uvicorn app:app --reload
```

### 4. Use it

Open `http://localhost:8000` in your browser. Type a prompt in the chat box — the FastAPI backend forwards it to the local `dolphin-llama3` model and streams back the reply. Everything stays on your machine.

If you want a different model, change `"model": "dolphin-llama3:latest"` in `app.py` to any model you've pulled with Ollama.

## Part 2 — Uncensored LLM (Groq)

A cloud-hosted chat that uses Groq's fast inference and a system prompt tuned to give direct technical answers.

### 1. Get a Groq API key

Sign up at [console.groq.com](https://console.groq.com/) and generate a key under **API Keys**.

### 2. Add your key

Open `Uncensored LLM/main.py` and replace:

```python
client = Groq(api_key="<Replace with your Groq API key>")
```

with your real key. (Better practice: load it from an environment variable instead of hardcoding.)

### 3. Run the app

```bash
cd "Uncensored LLM"
pip install -r requirements.txt
python main.py
```

### 4. Use it

Flask serves on `http://localhost:5000` by default. Open it, type a question, and the backend calls Groq's `llama-3.1-8b-instant` model with the tuned system prompt and returns the answer.

To adjust behavior, edit the `SYSTEM_PROMPT` string in `main.py`, or swap the `model` value for another Groq-hosted model.

## ⚠️ Authorization

The Uncensored LLM system prompt intentionally suppresses refusals for authorized security-research use. Keep it in a lab/research context — don't use it to produce real-world harmful output.

<div align="center">

# 🧠 LLM Operations

### Local & cloud LLM setups for AI-assisted security research

[![Python](https://img.shields.io/badge/python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Ollama](https://img.shields.io/badge/local-Ollama-000000?style=for-the-badge)](https://ollama.com/)
[![Groq](https://img.shields.io/badge/cloud-Groq-F55036?style=for-the-badge)](https://groq.com/)
[![License](https://img.shields.io/badge/license-Educational%20Use-blue?style=for-the-badge)](#disclaimer)

![GitHub repo size](https://img.shields.io/github/repo-size/Yaman-RedTeam/llm-operations?style=flat-square&color=orange)
![GitHub last commit](https://img.shields.io/github/last-commit/Yaman-RedTeam/llm-operations?style=flat-square&color=blueviolet)
![GitHub stars](https://img.shields.io/github/stars/Yaman-RedTeam/llm-operations?style=flat-square&color=yellow)

</div>

---

## 📖 Overview

Two minimal chat-interface setups for running an LLM as a security-research assistant — one fully local (Ollama), one cloud-hosted (Groq).

## 🧩 Projects

| Project | Stack | Description |
|---|---|---|
| **Local LLM Setup / dolphin-web** | FastAPI + Ollama | Offline chat UI that proxies prompts to a local `dolphin-llama3` model via Ollama's `/api/generate` endpoint. No API key, no internet required. |
| **Uncensored LLM** | Flask + Groq | Cloud-hosted chat UI using Groq's `llama-3.1-8b-instant`, with a system prompt tuned to give direct, unrestricted technical answers for offensive-security research (no refusals/disclaimers). |

## ⚙️ Prerequisites

- Python 3.11+
- [Ollama](https://ollama.com/) installed locally with the `dolphin-llama3` model pulled (for `Local LLM Setup`)
- A [Groq API key](https://console.groq.com/keys) (for `Uncensored LLM`)

## 🚀 Setup

> 📘 New here? See the full walkthrough in [GUIDE.md](./GUIDE.md).

### Local LLM Setup (dolphin-web)

```bash
ollama pull dolphin-llama3
cd "Local LLM Setup/dolphin-web"
pip install -r requirements.txt
uvicorn app:app --reload
```

### Uncensored LLM

```bash
cd "Uncensored LLM"
pip install -r requirements.txt
```

Set your Groq API key in `main.py` (replace `<Replace with your Groq API key>`), then:

```bash
python main.py
```

## 📁 Structure

```
llm-operations/
├── Local LLM Setup/
│   └── dolphin-web/
│       ├── app.py
│       ├── requirements.txt
│       └── static/index.html
└── Uncensored LLM/
    ├── main.py
    ├── requirements.txt
    └── templates/index.html
```

## ⚠️ Disclaimer

> The `Uncensored LLM` system prompt is deliberately configured to suppress refusals and disclaimers for **authorized security research and red-team use only**. Do not use it to generate or facilitate real-world harmful, illegal, or malicious activity. Use both projects only in environments and for purposes you are authorized for.

---

<div align="center">

Made with 🧠 + 🤖 for AI-assisted security research

</div>

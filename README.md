# 🧠 Telegram AI Agent with Long-Term Memory

> A production-ready Telegram chatbot with both short-term session memory and long-term persistent memory, powered by n8n, OpenAI GPT-4o-mini, and Google Docs as a memory store.

[![n8n](https://img.shields.io/badge/n8n-workflow-orange)](https://n8n.io)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-green)](https://openai.com)
[![Telegram](https://img.shields.io/badge/Telegram-Bot%20API-blue)](https://core.telegram.org/bots)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 📌 What It Does

Most AI chatbots forget everything when you close the chat. This bot doesn't. It maintains **two layers of memory**:

1. **Short-term memory** — Remembers the current conversation context
2. **Long-term memory** — Saves important facts to Google Docs, retrieves them in future sessions

This means the bot can remember your name, preferences, past requests, and notes — even days later.

---

## 🏗️ Architecture

```
User (Telegram)
      │
      ▼
Telegram Trigger (n8n)
      │
      ▼
┌─────────────────────────┐
│      AI Agent           │
│  (GPT-4o-mini)          │
│                         │
│  Tools:                 │
│  ├─ Retrieve LT Memory  │──► Google Docs (Long-Term Store)
│  ├─ Save LT Memory      │──► Google Docs (Long-Term Store)
│  └─ Session Buffer      │──► In-Memory (Short-Term)
└─────────────────────────┘
      │
      ▼
Telegram Reply
```

---

## ✨ Features

- **Dual Memory System** — Short-term (session) + Long-term (Google Docs)
- **Note Storage** — Save any information and retrieve it later
- **Context-Aware Responses** — Uses both memory layers for smart answers
- **Voice + Text Support** — Handles both message types
- **Persistent Across Sessions** — Memory survives bot restarts
- **No Database Required** — Uses Google Docs as free, human-readable storage

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Automation Engine | n8n |
| AI Model | OpenAI GPT-4o-mini |
| Messaging | Telegram Bot API |
| Long-Term Memory | Google Docs |
| Short-Term Memory | n8n Session Memory Buffer |

---

## 📋 Prerequisites

- n8n instance (cloud or self-hosted)
- OpenAI API Key
- Telegram Bot Token (from [@BotFather](https://t.me/botfather))
- Google account with Drive API access

---

## 🚀 Setup Guide

### Step 1 — Create Telegram Bot
1. Open Telegram and message [@BotFather](https://t.me/botfather)
2. Send `/newbot` and follow the instructions
3. Copy your **Bot Token**

### Step 2 — Prepare Google Docs Memory Store
1. Create a new Google Doc titled "AI Agent Memory"
2. Note the document ID from the URL: `docs.google.com/document/d/[THIS_IS_THE_ID]/edit`
3. Set up Google credentials in n8n (OAuth2)

### Step 3 — Import and Configure Workflow
1. Import `workflow.json` into n8n
2. Set credentials:
   - Telegram: paste your Bot Token
   - OpenAI: paste your API key
   - Google Docs: connect your Google account
3. Update the Google Doc ID in the workflow nodes

### Step 4 — Activate and Test
1. Activate the workflow in n8n
2. Open Telegram and send your bot a message
3. Say: "Remember that I prefer dark mode"
4. Start a new session and ask: "What are my preferences?"

---

## 💬 Example Interactions

```
User: "My name is Ahmet and I'm a software developer"
Bot:  "Nice to meet you, Ahmet! I've saved that you're a software developer."

[New session - days later]

User: "What do you know about me?"
Bot:  "You're Ahmet, a software developer. Is there anything else you'd like me to remember?"
```

---

## 📁 Project Structure

```
telegram-ai-agent-memory/
├── workflow.json          # Main n8n workflow
├── docs/
│   ├── setup-guide.md     # Detailed setup instructions
│   └── memory-schema.md   # How memory is structured
└── README.md
```

---

## 🎯 Use Cases

- **Personal Assistant** — Remembers your preferences, tasks, notes
- **Customer Service Bot** — Remembers past customer interactions
- **Study Assistant** — Saves study notes, reminds you of topics
- **Team Bot** — Shared memory for team channels

---

## 📄 License

MIT License

---

## 🔗 Related Projects

- [WhatsApp AI RAG Chatbot](../1-ai-whatsapp-rag-chatbot)
- [AI HR CV Screening](../3-ai-hr-cv-screening)

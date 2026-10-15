# 🤖 Multi-Modal Telegram Voice & Text AI Agent

A robust, production-ready n8n workflow template that powers an intelligent conversational agent capable of handling both **Voice (Audio)** and **Text** inputs seamlessly via Telegram. The agent leverages advanced Large Language Models, persistent memory, web search capabilities, and a comprehensive suite of Google Workspace integrations.

---

## 🏗️ Architecture & Workflow Overview

The workflow intake splits incoming Telegram messages based on their type (`Voice` or `Text`), processes audio files through Speech-to-Text (STT), routes them through an **AI Agent** node equipped with multi-tool capabilities, and returns either a text reply or a synthesized audio response (`TTS`).

```
[ Telegram Trigger ] 
       │
       ├──► (Text) ─────────► [ Input Variable / Sanitizer ] ──┐
       │                                                      │
       └──► (Voice) ──► [ Get File ] ──► [ STT (Whisper) ] ───┴──► [ AI Agent Node ] 
                                                                         │
                                       ┌─────────────────────────────────┴─────────────────────────────────┐
                                       ▼                                                                   ▼
                          [ Workspace & Tools Integration ]                                         [ Output Routing ]
                          • OpenAI Chat Model & Simple Memory                                      ├── (Text Mode) ──► [ Telegram (Send Message) ]
                          • Gmail (Send Email)                                                     └── (Voice Mode) ──► [ LLM Chain ] ──► [ TTS ] ──► [ Telegram ]
                          • SerpApi (Live Web Search)
                          • Google Docs (Create & Update)
                          • Google Sheets (Append Rows)
                          • Google Calendar (Create Events)
```

---

## ✨ Key Features & Capabilities

### 1. Dual-Channel Input Handling (Voice & Text)
* **Telegram Trigger:** Listens for incoming messages or voice notes from users in real-time.
* **Smart Routing (`Switch` Node):** Automatically detects message types and routes text directly or sends voice notes through transcription pipelines.
* **Speech-to-Text (STT):** Converts incoming voice recordings into clean text transcripts.

### 2. Autonomous AI Agent Core
* **Powered by OpenAI:** Utilizes advanced LLM chat models (`OpenAI Chat Model`) for intelligent reasoning, intent recognition, and tool selection.
* **Conversational Memory (`Simple Memory`):** Maintains context across multi-turn interactions for a fluid, natural conversational experience.

### 3. Integrated Tool Suite
The AI Agent is equipped with a comprehensive set of external tool nodes to execute real-world tasks dynamically:
* ✉️ **Gmail:** Send emails directly through conversational prompts.
* 🔍 **SerpApi:** Perform real-time web searches to fetch up-to-date information, news, or facts.
* 📝 **Google Docs:** Create new documents and update existing documentation on the fly.
* 📊 **Google Sheets:** Append structured data or logs directly into spreadsheets.
* 📅 **Google Calendar:** Schedule meetings, appointments, and events automatically.

### 4. Omnichannel Response & Voice Synthesis (TTS)
* **Text Replies:** Instantly sends formatted text responses back to the user via Telegram.
* **Voice Replies (TTS):** For voice-initiated queries, the agent processes responses through a secondary LLM chain, converts text to natural-sounding speech (`TTS`), and dispatches an audio voice note back to Telegram.

---

## 🛠️ Tech Stack & Nodes Used

* **Orchestration:** n8n
* **Messaging Interface:** Telegram Bot API
* **AI / ML:** OpenAI (GPT Models, Whisper STT, Text-to-Speech TTS)
* **Data & Productivity:** Google Workspace (Gmail, Google Docs, Google Sheets, Google Calendar)
* **Search / Utilities:** SerpApi

---

## 🚀 Getting Started

1. **Import the Workflow:** Download the n8n workflow JSON file and import it into your n8n instance.
2. **Configure Credentials:** Set up and authenticate your credentials for:
   * Telegram Bot API
   * OpenAI API
   * Google OAuth2 (Gmail, Docs, Sheets, Calendar)
   * SerpApi Key
3. **Activate the Workflow:** Toggle the workflow status to **Active** and start chatting or sending voice notes to your Telegram bot!
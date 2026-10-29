# Multimodal WhatsApp AI Agent (n8n Workflow)

An automated n8n workflow that routes and processes incoming WhatsApp text, audio voice notes, and image messages using Groq and OpenAI models.

## 📐 Workflow Architecture

1. **WhatsApp Trigger**: Listens for inbound messages on WhatsApp Business API.
2. **Switch Node (Router)**: Evaluates incoming payload type (`text`, `audio`, or `image`).
   - **Text**: Formatted via `Edit Fields` and sent directly to the AI Agent.
   - **Audio**: Downloaded via WhatsApp API, retrieved via HTTP, transcribed using OpenAI Whisper, and passed to the AI Agent.
   - **Image**: Downloaded via WhatsApp API, retrieved via HTTP, analyzed using OpenAI Vision, and passed to the AI Agent.
3. **AI Agent**: Orchestrates responses using **Groq Chat Model** and maintains chat context via **Simple Memory**.
4. **Send Message**: Delivers the final response back to the user on WhatsApp.

## 🛠️ Prerequisites

- An active **n8n** instance (Self-hosted or Cloud)
- **WhatsApp Business API** Cloud credentials
- **Groq API Key** (for fast reasoning model)
- **OpenAI API Key** (for Speech-to-Text transcription and Vision analysis)

## 🚀 Setup Instructions

1. **Import Workflow**: Download `workflow.json` from this repository and import it into your n8n workspace.
2. **Configure Credentials**:
   - Set up **WhatsApp API** credentials in the trigger and response nodes.
   - Add your **Groq API Key** to the `Groq Chat Model` node.
   - Add your **OpenAI API Key** to the `Transcribe a recording` and `Analyze image` nodes.
3. **Activate**: Enable the workflow and configure the webhook URL inside your Meta Developer Console.

## 📄 License
MIT

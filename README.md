# Prixm Solutions AI Business Agent (n8n Workflow)

## Overview
This n8n workflow operates a highly capable, professional AI business representative for **Prixm Solutions**. Designed to integrate directly into a chat widget or messaging platform via a webhook, this AI agent introduces visitors to the company, details core technical services, answers questions contextually, and seamlessly guides prospects toward booking a consultation or capturing their contact information.

## How It Works
1. **Chat Trigger / Webhook**: The workflow is initiated when a chat message is received (`When chat message received` node). This acts as the entry point for user inquiries.
2. **AI Agent Processing**: The core logic is handled by the `AI Agent` node, which acts as the intelligent brain of the operation. It is strictly programmed with the mission, services, and operational guardrails of Prixm Solutions.
3. **Google Gemini LLM**: The AI Agent is powered by the `Google Gemini Chat Model`, providing high-quality, natural language understanding and response generation.
4. **Contextual Memory**: A `Simple Memory` (Buffer Window) node ensures the AI remembers the ongoing conversation, allowing for natural, multi-turn interactions without losing context.
5. **Webhook Response**: Once the AI generates its response, the `Respond to Webhook` node sends the reply back to the user's chat interface.

## Core Capabilities Configured in the AI
The AI agent is explicitly instructed to act as a representative for Prixm Solutions, specializing in:
*   **AI & Workflow Automation:** Custom AI agents, WhatsApp bots, reporting automation, and CRM integrations (Odoo).
*   **IT Services & Digital Presence:** Website design, digital marketing, and ERP deployment.
*   **Cybersecurity & Data Protection:** Consulting based on established partnerships (Logsign, SealPath, DNSFilter).
*   **Lead Generation:** Automatically prompting users to leave their contact details (Name, Email) or directing them to the official contact portal (https://remarkable-lokum-9f6a93.netlify.app/contact).

## Prerequisites
To deploy this workflow, you need the following in your n8n environment:
*   **n8n Webhook Configuration**: The chat trigger is set to webhook mode. You will need to connect your frontend chat widget to the n8n webhook URL.
*   **Google Gemini API Key**: Required for the `Google Gemini Chat Model` node to function.

## Workflow Nodes Breakdown
*   `When chat message received` (`@n8n/n8n-nodes-langchain.chatTrigger`): The webhook listener that receives incoming user messages.
*   `AI Agent` (`@n8n/n8n-nodes-langchain.agent`): The orchestrator containing the system prompt, company knowledge base, and behavioral guardrails.
*   `Google Gemini Chat Model` (`@n8n/n8n-nodes-langchain.lmChatGoogleGemini`): The underlying language model powering the AI.
*   `Simple Memory` (`@n8n/n8n-nodes-langchain.memoryBufferWindow`): Retains recent chat history for context.
*   `Respond to Webhook` (`n8n-nodes-base.respondToWebhook`): Sends the AI's formulated reply back to the chat interface.

## Installation & Setup
1. Open your n8n workspace.
2. Create a new workflow and select **Import from File**, or copy the provided JSON and paste it into the canvas.
3. Open the `Google Gemini Chat Model` node and select or create your **Google Gemini (PaLM) API account** credentials.
4. Review the system prompt in the `AI Agent` node to ensure the company details and links align with your current offerings.
5. Activate the workflow.
6. Retrieve the **Test** or **Production Webhook URL** from the `When chat message received` node and configure your chat widget or frontend application to POST messages to this endpoint.

## Customization
*   **Adjusting the Persona:** You can modify the system prompt within the `AI Agent` node to change the AI's tone, update service descriptions, or alter the lead capture link.
*   **Connecting a Frontend:** This workflow is designed to be headless. You can connect it to custom web chats, WhatsApp APIs, or Slack integrations by adjusting how the webhook payload is formatted.

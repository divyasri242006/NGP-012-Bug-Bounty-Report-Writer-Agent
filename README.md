# NGP-012 — AI-Powered Bug Bounty Report Writer Agent

An AI-assisted cybersecurity reporting workflow built using n8n, Telegram, and an AI Agent.

## Abstract
This project automates the conversion of raw vulnerability notes into structured bug bounty reports. The AI Agent generates report details such as title, severity, verdict, reproduction steps, impact, and remediation. Reports are stored in an n8n Data Table and retrieved through Telegram commands.

## Features
- Telegram-based vulnerability note submission
- Authorized-chat validation
- Message parsing and routing
- AI-assisted structured report generation
- Data Table storage and report ID assignment
- `/status` and `/last 3` commands
- Long-message handling and execution logging

## Technology Stack
- n8n Workflow Automation
- Telegram Bot API
- OpenAI Chat Model
- Structured Output Parser
- n8n Data Tables

## Architecture
Telegram Trigger → Authorization → Parse Message → Route Message

- **Report notes:** AI Agent → Prepare Report → Save Report → Assign Report ID → Telegram Reply
- **`/status`:** Count Reports → Build Status Reply
- **`/last N`:** Get Last Reports → Build Last Reply
- **Delivery:** Chunk Reply → Split Chunks → Send Reply → Log Outcome

## Try the Telegram Bot
**[Open NGP-012 Bug Bounty Assistant](https://t.me/NGP012BugBountyAssistantBot)**

Commands:
- `/status` — view report statistics
- `/last 3` — retrieve recent reports
- Send vulnerability notes as a normal message to generate a structured report.

## Testing Results
- Live `/status` command returned four reports at the time of testing.
- Live `/last 3` returned reports NGP-012-004, NGP-012-003, and NGP-012-002.
- A sample note generated a formatted response identified as NGP-012-005, with Medium severity and a Suspected verdict.

Some failure scenarios remain unverified. Confirm that NGP-012-005 was saved in the production Data Table before claiming persistence.

## Security
Never publish bot tokens, API keys, credentials, or private information. AI-generated reports require human verification before being treated as confirmed vulnerabilities.

## Screenshots
Screenshots of the workflow architecture, routing, AI report generation, and Telegram output will be added to the `screenshots/` folder.

## Author
**Divyasri K.**  
**Project ID:** NGP-012

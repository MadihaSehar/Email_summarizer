# Gmail AI Auto-Reply & Classifier (n8n)

An AI-powered email automation built with **n8n**. It watches an inbox for new Gmail messages, uses an AI Agent to classify each email and draft a reply, and sends a summary back so nothing gets missed.

**Status:** ✅ Live and published in n8n.

## What it does

1. **Gmail Trigger** – fires whenever a new email arrives.
2. **AI Agent** (OpenAI chat model) – reads the email and:
   - Classifies it into a category: `urgent`, `spam`, or `normal`
   - Drafts a short, polite reply appropriate to that category
   - Returns the result as structured JSON: `{ "category": ..., "reply": ... }`
3. **Gmail (Send Email)** – sends a summary email back with the category and suggested reply, so the inbox owner always has a quick digest of what came in.

## Tech stack

- [n8n](https://n8n.io/) – workflow automation
- Gmail Trigger & Gmail nodes
- OpenAI Chat Model (via n8n AI Agent node)

## Workflow diagram

![workflow screenshot](workflow-screenshot.png)

## Setup

1. Import `workflow.json` into your n8n instance (`Import from File`).
2. Connect your own **Gmail** credentials to the Gmail Trigger and Gmail nodes.
3. Connect your own **OpenAI** API key to the Chat Model node.
4. Activate the workflow — new emails will trigger the AI classification and summary automatically.

## Example output

```json
{
  "category": "normal",
  "reply": "Thank you for your inquiry. I will check the status of order 456 and get back to you shortly."
}
```

## Roadmap / next steps

- [x] Send a summary email back with category + AI-drafted reply
- [ ] Auto-apply Gmail labels based on category (urgent / spam / normal)
- [ ] Flag phishing/suspicious emails using AI-based risk scoring
- [ ] Daily digest of all classified emails instead of per-email alerts

## Author

Built by Madiha as part of a self-directed AI automation + cybersecurity learning project.

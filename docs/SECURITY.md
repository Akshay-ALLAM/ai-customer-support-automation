# Security Notes

This repository is prepared as a public portfolio project.

## What Is Not Included

- No real API keys
- No OAuth tokens
- No exported n8n credential secrets
- No real Airtable base or table IDs
- No real customer data
- No live webhook URL

## Public Workflow Export

`workflow.json` is a scrubbed public export. After importing it into n8n, replace the placeholder Airtable IDs and configure your own credentials inside n8n.

## Before Reusing

Before publishing your own version, check:

- n8n credential IDs and names
- Airtable base/table IDs
- Webhook URLs
- API keys or tokens
- Screenshots with private data
- Git history for previously committed secrets

# Setup Guide

This guide explains how to reproduce the demo workflow in n8n.

## Requirements

- n8n account or self-hosted n8n instance
- Airtable account
- Google Gemini API credentials configured inside n8n
- Hoppscotch, Postman, or any REST client for testing

## 1. Import The Workflow

1. Open n8n.
2. Create a new workflow.
3. Import `workflow.json`.
4. Replace placeholder Airtable IDs inside the Airtable node:
   - `YOUR_AIRTABLE_BASE_ID`
   - `YOUR_AIRTABLE_TABLE_ID`
5. Configure your own Airtable OAuth credential.
6. Configure your own Google Gemini credential.

## 2. Create Airtable Table

Create a table named `customers` with these fields:

| Field | Type | Example |
|---|---|---|
| Customer ID | Single line text | `CUST001` |
| Name | Single line text | `Aarav Mehta` |
| Phone number | Phone number | `+33123456780` |
| Order ID | Single line text | `ORD-1001` |
| Order Status | Single line text | `Shipped` |
| Tracking Code | Single line text | `TRK-FR-1001` |
| Pincode | Number | `75001` |
| Address | Long text | `12 Rue Demo, Paris` |
| last updated | Date | `2026-07-20` |

The sample records in `sample-data/sample-customers.csv` are fictional.

## 3. Test The Webhook

Use the n8n test webhook URL while the workflow is in test mode.

```json
{
  "customer_id": "CUST001",
  "message": "Where is my order?"
}
```

Expected success response:

```json
{
  "success": true,
  "message": "Hi Aarav, your order ORD-1001 has been shipped. You can track it using tracking code TRK-FR-1001. The latest update was recorded on 2026-07-20."
}
```

Expected error response for an unknown customer:

```json
{
  "success": false,
  "message": "Customer ID not found"
}
```

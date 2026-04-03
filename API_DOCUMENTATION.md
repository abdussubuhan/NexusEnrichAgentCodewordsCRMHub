# Internal API Architecture

This system acts as the middleware between standard CRM platforms (HubSpot, Salesforce, Pipedrive) and data scrapers. It utilizes three highly accessible JSON API routes.

---

### 1. Inbound CRM Webhook
**Endpoint:** `POST /api/webhooks/crm`

Provides the "Data Watcher". This endpoint expects a POST payload from your CRM when a tag like `To Enrich` is applied to a lead.

**Expected Request Payload:**
```json
{
  "id": "12345",
  "company_name": "TestCorp",
  "contact_name": "Alice"
}
```

---

### 2. The Enrichment Node
**Endpoint:** `POST /api/enrich`

Triggered internally by the UI or the webhook pipeline. It simulates collecting external firmographic data (Apollo/LinkedIn) and formats it into the expected B2B CRM Standard.

**Returns:**
```json
{
  "success": true,
  "confidence_score": 92,
  "enriched_data": {
    "company_size": "50-200",
    "industry": "SaaS / B2B Automation",
    "linkedin_url": "https://linkedin.com/company/testcorp",
    "sales_brief": "TestCorp is prime for automation..."
  },
  "needs_review": false
}
```

---

### 3. Outbound CRM Patcher
**Endpoint:** `POST /api/crm/patch`

Used when an enrichment cycle crosses the `85%` confidence rating (or is manually triggered). This POSTs the enriched data dynamically back to your CRM's specific record.

**Expected Input:**
```json
{
  "id": "12345",
  "enriched_data": { ... }
}
```

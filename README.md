# NexusEnrich Agent (Codewords CRM Hub)

Welcome to the **NexusEnrich** Agent by Codewords. This software is a high-performance, bidirectional automation pipeline designed to sync external data sources with your Customer Relationship Management (CRM) platform safely.

## Key Features
- **Bidirectional Syncing**: Listen to CRM updates via robust Webhook API nodes, and Patch them safely utilizing the RESTful patch handlers.
- **LLM Enrichment Engine**: Pre-configured architecture intended to ping scraping APIs (Clearbit, LinkedIn, Apollo), parse the data against an LLM (e.g., GPT-4 or Claude), and generate standard firmographics.
- **Data Validation Logic**: The system includes a dynamic confidence-scorer. If enrichment confidence falls beneath 85%, leads are quarantined to prevent CRM data corruption.
- **Premium User Interface**: Features a custom dark-mode Dashboard. Contains visual confidence ranking components and a CSV bulk dropzone mapped directly for B2B standard fields.

## Project Structure
- `/src/app/page.tsx` - The primary Dashboard Interface.
- `/src/app/api/webhooks/crm/route.ts` - Webhook Listener for the CRM.
- `/src/app/api/enrich/route.ts` - The LLM enrichment node logic.
- `/src/app/api/crm/patch/route.ts` - The outgoing node patching the CRM.
- `/src/lib/utils/validation.ts` - Confidence scoring and review thresholds.

## Next Steps
To configure environment keys and get this deployed locally or in production, please read the included `DEPLOYMENT.md` file. For developer guides to map API fields, please reference `API_DOCUMENTATION.md`.

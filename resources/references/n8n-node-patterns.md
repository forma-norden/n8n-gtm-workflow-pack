# n8n Node Patterns

Common configurations for GTM automation workflows.

## 1. The Webhook Receiver (Ingestion)

Use this pattern to catch signals, form submissions, or Clay outputs.

**Nodes:**
- `Webhook` (HTTP Method: POST, Respond: Immediately or When Last Node Finishes)
- `Set` or `Edit Fields` (Extract nested payload data into flat keys)
- `IF` (Validate required fields exist before processing)

**Best Practice:** Always return a 200 OK immediately if the sending system doesn't need data back, then process asynchronously to avoid timeouts.

## 2. API Pagination (Data Extraction)

Use this pattern to pull large datasets from a CRM or enrichment API.

**Nodes:**
- `HTTP Request` (Call API)
- `IF` (Check if `next_page_token` exists in response)
- `Set` (Store token and aggregate data)
- Loop back to `HTTP Request` (Pass token in query params)

**Best Practice:** Add a safety `Code` node counter to break the loop after 100 iterations to prevent infinite loops.

## 3. The Bulk Processor (Split in Batches)

Use this pattern when dealing with hundreds of rows from Clay or a database to respect API rate limits.

**Nodes:**
- `Set` (Assemble array of items)
- `Split In Batches` (Set batch size to 10 or 50)
- `HTTP Request` (Process the batch)
- `Wait` (Optional: 1 second delay between batches)
- Loop back to `Split In Batches`

**Best Practice:** Group items logically before batching to reduce the total number of API calls.

## 4. The CRM Sync (Upsert Pattern)

Use this pattern to safely update CRMs without creating duplicates.

**Nodes:**
- `HubSpot` / `Salesforce` Node (Action: Search/Get)
- `IF` (Does contact exist?)
  - True -> `HubSpot` (Action: Update)
  - False -> `HubSpot` (Action: Create)

**Best Practice:** Search by email first, then company domain if email is missing. Always use Upsert when the API supports it natively.

## 5. The Error Handler (Reliability)

Use this pattern on *every* production workflow.

**Setup:**
1. Create a dedicated "Error Alert Workflow" with an `Execute Workflow Trigger` and a `Slack` or `Email` node.
2. In your main workflow settings, set the "Error Workflow" to the alert workflow.

**Node-Level Reliability:**
- On `HTTP Request` nodes making outbound calls, go to Settings -> `Continue On Fail: true`.
- Add an `IF` node after it checking if `$json.error` exists. Handle gracefully (e.g., mark as "failed_enrichment" instead of crashing).

## 6. The deduplicator

Use this pattern to filter out items you've already processed.

**Nodes:**
- `Code` (Custom logic to compare arrays) OR
- `Postgres` (Query to check if item hash/ID exists in processing log)
- `IF` (Exists in DB?)
  - True -> End (Do nothing)
  - False -> Process -> `Postgres` (Insert ID to processing log)

**Best Practice:** Always log successful executions to a database table if idempotency is critical (e.g., sending emails, charging cards).

# CLAUDE.md - n8n-gtm-workflow-pack

This repo defines production n8n workflow patterns for GTM systems.

## Skills in This Repo

| Skill | When to use it |
|-------|---------------|
| `n8n-lead-ingestion-enrichment` | collecting and normalizing lead data from many sources |
| `n8n-cold-outreach-orchestrator` | controlling send logic, sequence enrollment, and template rotation |
| `n8n-crm-conversation-sync` | writing outcome events and follow-up tasks to CRM |
| `n8n-lead-scoring-routing` | scoring and routing leads into owner-specific lanes |
| `n8n-workflow-reliability-guardrails` | applying retries, error workflows, and concurrency controls |
| `n8n-observability-cost-control` | monitoring workflow health and runtime cost behavior |

## Output Rule

Every output must include:

- workflow node sequence
- input and output contract
- failure behavior
- recovery behavior

## Testing Rule

Run tests from the `tests/` folder before production use.


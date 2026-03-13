# Ecosystem: n8n-gtm-workflow-pack

How this repo connects to the rest of the Forma Nôrden GTM library.

## Works With

| Repo | Relationship | When to use together |
|------|-------------|---------------------|
| `clay-claude-code-skill-pack` | Upstream/Parallel | n8n orchestrates Clay enrichment workflows via webhooks and API |
| `cold-email-copy-playbook` | Downstream | n8n automates sequence enrollment after copy is approved |
| `cold-email-deliverability-playbook` | Parallel | Deliverability monitoring integrated into n8n alerting |
| `buying-window-signal-workflow` | Upstream | Signal events trigger n8n workflows for processing |
| `signal-based-list-building-workflow` | Upstream | List building signals feed into n8n for enrichment routing |
| `linkedin-claude-code-workflow` | Parallel | LinkedIn engagement data flows through n8n for scoring |

## Suggested Skill Chains

1. **Automated enrichment pipeline**: Signal webhook > `n8n-lead-ingestion-enrichment` > `n8n-clay-integration` (enrich via Clay API) > `n8n-lead-scoring-routing` > `n8n-crm-conversation-sync`
2. **Reliable outbound automation**: `n8n-cold-outreach-orchestrator` (sequence) + `n8n-workflow-reliability-guardrails` (error handling) + `n8n-observability-cost-control` (monitoring)

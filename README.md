# n8n GTM Workflow Pack

Production workflow patterns for GTM teams using n8n to run enrichment, routing,
outbound execution, and RevOps handoffs without brittle automations.

This package condenses the original 20 tactical examples into reusable operator
workflows that can be adapted across stack variants.

## What's Inside

| File | What it does |
|------|-------------|
| `.claude/skills/n8n-lead-ingestion-enrichment.md` | Ingests leads from multiple sources, deduplicates, enriches, and validates output schema. |
| `.claude/skills/n8n-cold-outreach-orchestrator.md` | Controls sequence enrollment, template rotation, and send guardrails. |
| `.claude/skills/n8n-crm-conversation-sync.md` | Syncs call and email outcomes into CRM with task and follow-up actions. |
| `.claude/skills/n8n-lead-scoring-routing.md` | Scores leads and routes to sales, nurture, or monitor paths with Slack alerts. |
| `.claude/skills/n8n-workflow-reliability-guardrails.md` | Applies retries, error workflows, timeout policy, and concurrency controls. |
| `.claude/skills/n8n-observability-cost-control.md` | Tracks execution health, AI-node usage, and operational cost drift. |
| `tests/` | Prompt-based tests and validation checklists for all six skills. |

## Prerequisites

- [ ] n8n Cloud or self-hosted n8n instance
- [ ] Credentials for source systems (CRM, enrichment, sequencer, Slack)
- [ ] Environment separation (`sandbox`, `staging`, `production`)
- [ ] Data model for account, contact, score, route, owner

## Installation

1. Clone the repo:
   ```bash
   git clone https://github.com/forma-norden/n8n-gtm-workflow-pack.git
   ```
2. Copy `.claude/skills/` into your project:
   ```bash
   cp -r n8n-gtm-workflow-pack/.claude/skills your-project/.claude/
   ```
3. Load the relevant skill before designing or updating an n8n workflow.

## Usage

```text
Read .claude/skills/n8n-lead-scoring-routing.md

Inputs:
- inbound source: website + LinkedIn engagement
- scoring criteria: ICP + recency + engagement
- route policy: high -> AE, medium -> SDR, low -> nurture
- notification destination: Slack #inbound-alerts

Return:
1) node-level workflow plan
2) scoring logic
3) routing outputs
4) failure handling path
```

Expected output:

- node-level execution sequence
- deterministic scoring and route logic
- explicit error and retry behavior

## Who This Is For

GTM engineers, RevOps leads, VP Sales, and founders at B2B companies with 50 to 500 employees who are building or consolidating their
outbound infrastructure and want to reduce tool sprawl through
better-engineered GTM systems.

---

---

## From the Forma NÃ´rden GTM Library

This is a free resource from the Forma NÃ´rden open-source GTM library, built by 
[Yananai A. Chiwuta](https://yananaichiwuta.com/), GTM engineer and founder of 
[Forma NÃ´rden](https://formanorden.com/).

- [Open-source GTM systems](https://github.com/forma-norden): all repos in the library  
- [GTM engineering blog](https://formanorden.com/blog/): strategy, systems, and outbound deep-dives  
- [All resources](https://formanorden.com/resources/): guides, frameworks, and templates  

If this saves you time, star the repo and follow 
[Forma NÃ´rden on LinkedIn](https://www.linkedin.com/company/formanorden/).

Built by [Forma NÃ´rden](https://formanorden.com/): GTM engineering for B2B companies.

# Test: n8n-lead-ingestion-enrichment

Load skill: `.claude/skills/n8n-lead-ingestion-enrichment.md`

## Prompt

```text
Read .claude/skills/n8n-lead-ingestion-enrichment.md

Inputs:
- sources: Apollo export, LinkedIn engagement webhook, website form webhook
- dedupe keys: company_domain + email
- enrichment: Clay and Apollo
- required output: company_domain, full_name, title, email, validation_status, ready_for_routing

Return node sequence and quality gates.
```

## Must Pass Checklist

- [ ] Includes canonical mapping step
- [ ] Includes dedupe before enrichment
- [ ] Includes validation gate before write
- [ ] Includes output schema contract
- [ ] Includes fail conditions

## Failure Indicators

- Writes directly without dedupe
- No validation gate
- No required output schema


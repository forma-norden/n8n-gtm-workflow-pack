# Test: n8n-crm-conversation-sync

Load skill: `.claude/skills/n8n-crm-conversation-sync.md`

## Prompt

```text
Read .claude/skills/n8n-crm-conversation-sync.md

Inputs:
- event source: call summary webhook
- CRM: HubSpot
- owner mapping: by account owner
- follow-up SLA: 24 hours

Return sync workflow with idempotency and task creation logic.
```

## Must Pass Checklist

- [ ] Includes entity match step before write
- [ ] Includes idempotency guard
- [ ] Includes follow-up task creation
- [ ] Includes owner mapping rule
- [ ] Includes failure path when match confidence is low

## Failure Indicators

- Writes to CRM without match validation
- No idempotency strategy
- No follow-up task logic


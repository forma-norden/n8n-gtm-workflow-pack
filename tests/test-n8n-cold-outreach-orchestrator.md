# Test: n8n-cold-outreach-orchestrator

Load skill: `.claude/skills/n8n-cold-outreach-orchestrator.md`

## Prompt

```text
Read .claude/skills/n8n-cold-outreach-orchestrator.md

Inputs:
- list quality: validated only
- daily cap per inbox: 25
- suppression window: 21 days
- sequence branches: ABM, standard outbound, monitor

Return orchestration logic and send guardrails.
```

## Must Pass Checklist

- [ ] Includes suppression list check
- [ ] Includes cap control by inbox
- [ ] Includes template or branch assignment
- [ ] Includes status update path
- [ ] Includes fail conditions for missing controls

## Failure Indicators

- No suppression check
- No send cap logic
- No fail behavior for missing branch rules


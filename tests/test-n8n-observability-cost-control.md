# Test: n8n-observability-cost-control

Load skill: `.claude/skills/n8n-observability-cost-control.md`

## Prompt

```text
Read .claude/skills/n8n-observability-cost-control.md

Inputs:
- workflows: lead-ingest, scoring-route, outbound-enroll
- budget thresholds:
  - lead-ingest: $300/mo
  - scoring-route: $150/mo
  - outbound-enroll: $120/mo
- reporting cadence: weekly
- alert owner: revops-lead

Return observability model and cost-control actions.
```

## Must Pass Checklist

- [ ] Defines health metrics per workflow
- [ ] Defines budget threshold monitoring
- [ ] Includes drift alert conditions
- [ ] Includes cost-control actions
- [ ] Includes fail conditions for missing owners and thresholds

## Failure Indicators

- No metric definitions
- No budget controls
- No actions when thresholds are breached


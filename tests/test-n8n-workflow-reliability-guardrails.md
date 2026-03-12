# Test: n8n-workflow-reliability-guardrails

Load skill: `.claude/skills/n8n-workflow-reliability-guardrails.md`

## Prompt

```text
Read .claude/skills/n8n-workflow-reliability-guardrails.md

Inputs:
- criticality: high
- external API nodes: 4
- retry policy: exponential backoff, 3 attempts
- timeout policy: 30s per external call
- alert channel: Slack #workflow-alerts

Return guardrail policy and error workflow structure.
```

## Must Pass Checklist

- [ ] Includes retry strategy
- [ ] Includes timeout policy
- [ ] Includes error workflow destination
- [ ] Includes environment-specific controls
- [ ] Includes fail conditions

## Failure Indicators

- No error workflow
- No retry or timeout controls
- No alerting owner or channel


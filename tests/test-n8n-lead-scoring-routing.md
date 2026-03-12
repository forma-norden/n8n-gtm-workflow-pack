# Test: n8n-lead-scoring-routing

Load skill: `.claude/skills/n8n-lead-scoring-routing.md`

## Prompt

```text
Read .claude/skills/n8n-lead-scoring-routing.md

Inputs:
- fit weight: 60
- intent weight: 40
- hard disqualifiers: non-ICP industry, invalid email
- route policy: >=80 AE, 60-79 SDR, <60 nurture
- notify: Slack #lead-routing

Return scoring and routing workflow.
```

## Must Pass Checklist

- [ ] Uses deterministic weighted scoring
- [ ] Applies disqualifiers before route assignment
- [ ] Includes route policy by threshold
- [ ] Includes notification output
- [ ] Includes fail conditions

## Failure Indicators

- No weights
- No disqualifier handling
- Route assignment without score


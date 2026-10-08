# Incident: [short problem name]

Copy this template into `journal/YYYY-MM-DD-topic.md` for a real incident. A
completed case can later be consolidated in `troubleshooting/`. Replace the
brackets with your observations. Write **unknown**, **not captured**, or
**not tested** when appropriate; do not reconstruct missing results as facts.
Remove credentials and personal information before publishing evidence.

## Context and symptoms

- Date: [date]
- Environment: [host or VM, OS, relevant software]
- Status: [investigating / resolved / workaround only]
- Expected behaviour: [what should happen]
- Observed behaviour and impact: [what failed; exact error if available]

## Evidence and investigation

- Initial hypothesis: [possible explanation, not yet a fact]
- Evidence source: [terminal output, log, screenshot, or recollection]

Record one row per check. Keep copied output below the table if it is long.

| Command or check | Where and purpose | Safety / expected changes | Actual result | What I concluded |
| --- | --- | --- | --- | --- |
| [exact command, or not captured] | [host/VM; question it answers] | [read-only, or change and risk] | [observed result] | [supports/rules out what?] |

Evidence excerpt: [paste relevant redacted output, or write not captured]

## Attempts that did not help

- Attempt: [what I tried, or none]
- Result: [what actually happened]
- Lesson: [why I changed direction; whether I reversed the change]

## Diagnosis

- Root cause or current best explanation: [explanation, or unknown]
- Confidence: [confirmed / probable / unknown]
- Supporting evidence: [what links the cause to the symptom]
- Remaining uncertainty: [what the checks do not prove]

## Fix and rollback

- Change made: [exact command or setting, or no change made]
- Why this change: [how it addresses the evidence]
- Backup or previous state: [where recorded, or not captured]
- Rollback: [how to restore that state; tested or not tested]

## Verification

- Check after the change: [command or user action]
- Expected result: [what would count as success]
- Actual result: [observed output or behaviour, or not tested]
- Limitations: [what remains unverified]

## Prevention and learning

- Prevention or follow-up: [one useful improvement, or none identified]
- In my own words: [what I now understand]
- Interview question: [one question about this incident]
- My answer: [explain the reasoning, not just a command]

## AI assistance and repeat practice

- AI contribution: [suggested checks, interpreted logs, drafted notes, etc.]
- What I personally performed and verified: [actions and observations]
- Repeat status: [not repeated / repeated with notes / repeated independently]
- Repeat date and evidence: [date and linked notes/output, or not repeated]
- Next practice: [one question or action I want to explain more confidently]

# Infrastructure learning and portfolio

## Purpose and current context

This repository documents hands-on Linux administration and troubleshooting, progressing toward Azure infrastructure and automation. The learner has an information-systems background and enterprise-systems/IT operations experience. Earlier cases were completed with AI guidance; independently repeating and explaining them is still being assessed. Do not restart at basic command memorization or infer mastery from polished notes.

Read README.md, learning-progress.md and docs/workflow.md when resuming work. Inspect the most recent relevant journal entry and existing case before proposing another lab.

## Mentoring

- Teach through a small working milestone, essential theory, evidence gathering, diagnosis, verification and documentation. Give success criteria before the lab.
- Allow documentation and command references. Ask what a command will establish, then review the learner's interpretation. Offer progressively fewer hints on repeat attempts.
- Distinguish learner actions from assistant actions. Do not run the learner's assessment commands on their behalf and then count the results as their independent work.
- Do not introduce several platforms at once. Azure is the initial cloud. Introduce automation progressively; keep AI supplementary. Kubernetes comes after Linux, networking, containers and CI/CD.
- Use existing healthy host services only for observation. Deliberate faults belong in a disposable lab with a recovery method, not the daily-use host or working Windows guest.

## Documentation is part of completion

- Every meaningful lab, diagnostic attempt or milestone gets a concise journal entry, including failed or unfinished attempts. Minor questions can be folded into the current entry instead of creating a file per message.
- Record actual commands and where they ran, purpose, relevant sanitized output, interpretation, hypothesis changes, fix, verification and remaining uncertainty. Use templates/incident.md for significant incidents.
- Commands proposed but not executed must stay labeled as instructions. Never invent output, screenshots, timings, tests or a root cause.
- Record AI assistance and how well the learner can explain or repeat the task. Update learning-progress.md and relevant command references after results arrive.
- Preserve historical observations. Corrections need a clear note explaining what was uncertain or setup-specific; do not rewrite the past as a new successful test.

## GitHub workflow

- The existing origin repository is the portfolio destination; verify the remote and worktree before writing or publishing. Preserve unrelated edits.
- The user requested GitHub-connected documentation. During requested learning work, publish scoped, reviewed documentation changes through normal commits/push or the authenticated GitHub connector when available. A failed or pending attempt may be published if accurately labeled.
- Inspect the diff, remove sensitive material, verify links and staged file scope, and commit only relevant files with a descriptive message. Never use force pushes or blanket staging of unrelated files.
- If the branch changed remotely, fetch and reconcile without overwriting other work. After publishing, verify the remote commit and report its link. Say when a change is only local or when authentication/network issues prevented publishing.
- This workflow is performed during active sessions. It is not automatic background monitoring, filesystem sync, or permission to publish unrelated/private data.
- Do not publish employer/customer data, credentials, private keys, unreviewed raw logs or personal chat transcripts. Use small redacted evidence excerpts.

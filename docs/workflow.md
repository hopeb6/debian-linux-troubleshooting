# Learn, record, verify, publish

The portfolio grows alongside the learning. A task is documented even when the result is an error or an unresolved hypothesis. Being able to find and explain a command matters more than recalling every option.

## One source of truth

- GitHub: https://github.com/hopeb6/debian-linux-troubleshooting
- Existing local checkout: `/home/suby/debian-linux-troubleshooting`.
- Use that same checkout in Cursor and the corresponding Codex project. The downloaded `debian-linux-troubleshooting-github-ready` folder is a historical export, not a Git checkout.
- The separate personal website is another project. This repository is the source for the Linux case studies it may eventually showcase.

## During a learning session

1. Choose one task and state what success would look like. Inspect Git status and recent history before editing.
2. The learner predicts what a diagnostic check can establish, runs it, and shares the relevant output with an interpretation.
3. The mentor reviews evidence, offers hints, and helps distinguish an observation from an explanation. Change one relevant thing at a time when a fix is justified.
4. Record the attempt in `journal/YYYY-MM-DD-topic.md`. Use [the incident template](../templates/incident.md) for significant problems. Keep short practice entries short.
5. Update [learning progress](../learning-progress.md) and [the command notebook](../reference/command-notebook.md) when understanding improves. Summarize one useful takeaway and the next task.
6. Review and publish the relevant changes, then verify the GitHub commit. If publishing fails, keep the local record and report the blocker.

## What belongs where

| Location | Purpose |
| --- | --- |
| `troubleshooting/` | Existing case studies and later consolidated incident reports |
| `journal/` | Dated attempts, evidence, assistance used and reflection |
| `labs/` | Lab instructions, expected outcomes and repeat-practice tasks |
| `reference/` | Short question-based command references, not proof of execution |
| `templates/` | Reusable documentation structures |
| `learning-progress.md` | Current milestone and evidence of repeatability |

Add scripts, configuration and diagrams when a project produces them; do not create empty project scaffolds for future technologies.

## Publishing a checkpoint

Review with `git status --short` and `git diff`. Stage only the files you intend to publish, then inspect `git diff --cached` before committing. Use a message that describes the actual change, such as `docs: record virtualization inventory and interpretation`.

Normally a local commit is sent with `git push origin main`. Fetch and reconcile incoming work first if Git reports that the branch is behind; do not force-push. If another checkout or the GitHub connector published the changes, a clean checkout can be updated with `git pull --ff-only`.

The GitHub connector is a publishing route when available in the current session. Shell Git authentication is separate: a successful connector write does not prove that terminal SSH works. Do not claim automatic syncing; confirm each push or connector commit with the remote result.

## Evidence and privacy

- Show the relevant output, not a full private session transcript. Review screenshots as well as text.
- Omit credentials, private keys, business records and identifying customer information. Keep raw material in an ignored `private-evidence/` folder when needed; only sanitized excerpts belong in commits.
- Label a result as observed, reported from earlier notes, inferred, not captured, or not yet tested as appropriate.
- Using AI is allowed and documented. Upgrade a skill's status only after a new attempt demonstrates the learner's own explanation or repeatability.

## Useful publication checks

- Do referenced files exist and Markdown code fences close correctly?
- Do commands, output and claimed results agree?
- Does the entry distinguish proposed steps from steps actually performed?
- Are known limits, assistance used and next steps stated?
- Does the staged diff include only intended, reviewed files?

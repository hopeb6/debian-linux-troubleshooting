# Infrastructure skills calendar
## 12 October 2026 – 11 April 2027; review on 12 April

**Purpose:** learn to administer and troubleshoot servers, networks and the services they run; build honest GitHub evidence while pursuing suitable work.

**Status:** planned work, not completed skills. The first 12 weeks are the main learning block; weeks 13–26 are a conditional continuation, not a requirement to wait before applying. Dates are targets and shift if a prerequisite needs more practice.

**Time assumption:** 8.5 hours a week. Choose session times that suit your life in Uganda; no fixed clock times or reminders have been scheduled.

## 1. The weekly routine

| Day | Time | What to do |
| --- | --- | --- |
| Monday | 1 hour | Review last result; learn one concept needed for this week's task; predict what a check will show. |
| Tuesday | 1 hour | Build or configure one small part of the lab. |
| Wednesday | 1 hour | Review eligible vacancies and skill requirements; tailor an application where appropriate. |
| Thursday | 1 hour | Diagnose a symptom, test a configuration, or practise a relevant command. |
| Friday | 30 minutes | Review notes and update the question-based command notebook. No new topic. |
| Saturday | 3 hours | Two 75-minute practical blocks with a 15-minute break, then 15 minutes recording evidence. |
| Sunday | 1 hour | Repeat one task with notes but without step-by-step AI help (30 min); review/sanitize/publish evidence (20 min); choose next step (10 min). |

In ordinary one-hour technical sessions, use roughly 10 minutes for explanation, 40 for practice and 10 for notes. Documentation is included in the schedule, not extra homework.

**Missed session:** resume the next unfinished task; do not double the next day's workload.
**Busy week:** use 3 hours: 90 minutes on one lab task, 30 on repeat practice, 30 on notes, 30 on opportunities. Shift later dates rather than skipping prerequisites.
**Stuck for 20 minutes:** record expected versus actual behaviour and the relevant evidence, then ask for one hint. Stop immediately for safety concerns rather than experimenting on the host.

## 2. What counts as progress

For each milestone:
1. Make it work and record the actual result.
2. Explain why it works and what your checks do not prove.
3. Repeat a small task using your notes, without AI supplying every next command.
4. Where safe, diagnose a related variation in the isolated lab.
5. Publish a reviewed learning record; identify AI help honestly.

Track **Guided → Explained → Repeated with reference → Transferred**. A calendar date, screenshot or generated README does not prove competence. No command-memorization tests.

## 3. Main project and safety boundaries

Build one evolving project: **Small-business Linux server operations lab**.

Start with a disposable Debian server VM and a simple Nginx test website. Later add controlled access, backups, recovery, monitoring and automation. Move a small version to one cloud platform only after the local foundation is repeatable.

- Inspect available RAM and disk before deciding VM size. Do not assume the laptop can run multiple guests.
- Leave the daily-use Debian host and existing Windows VM healthy; use them only for authorized observation.
- Deliberate faults, test users and dummy data belong inside the lab VM.
- Keep a recovery method and console access before changing SSH or firewall settings.
- No public exposure, paid subscription, domain purchase or resource charges without a separate explicit decision.
- A VM snapshot helps recover a lab change; it is not a substitute for an independently tested data backup.
- Do not copy employer/customer data, credentials or private keys into the lab or portfolio.
- Azure is the provisional first cloud, subject to vacancy evidence and affordable access. Do not learn two clouds at once.
- No Kubernetes or AI incident-summary feature in this plan.

## 4. Weeks 1–12: the core calendar

Use Monday/Tuesday/Thursday/Saturday for each row's technical work. Wednesday and Sunday follow the routine above.

| Week / dates | Technical focus and tasks | Evidence required by Sunday |
| --- | --- | --- |
| 1 · 12–18 Oct | Finish the existing inventory interpretation; inspect host capacity read-only; choose safe VM resources; start an isolated Debian server installation if capacity permits. Review the first 10 vacancy descriptions. | Own explanation of VM versus network state; recorded capacity and lab design; VM installation result or exact blocker. No invented successful install. |
| 2 · 19–25 Oct | Finish VM setup if needed. Practise paths, files, users/groups, permissions and sudo on dummy accounts. Connect from host to guest using SSH after checking the guest's address. Review 10 more vacancies. | Explain host versus guest; demonstrate one allowed and one denied file-access test; connect by SSH or document the specific failure. |
| 3 · 26 Oct–1 Nov | Inspect guest IP address, subnet, default route, DNS and listening ports. Trace how host traffic reaches the guest. Review the final 10 vacancies and summarize recurring requirements. | Small network diagram; separate address, route, DNS and service observations; 30-row market review or transparent shortfall. |
| 4 · 2–8 Nov | Install Nginx in the guest, serve a test page, inspect its service status and logs, and verify local and host-to-guest HTTP access. | Explain the request path; deliberately stop only the lab service, diagnose and recover it. **Gate A review.** |
| 5 · 9–15 Nov | Practise SSH key access and limited administrative access. Set lab firewall rules after verifying console recovery. Test allowed and blocked connections. | Access-control checklist with test results; no private keys published. Explain each permitted service. |
| 6 · 16–22 Nov | Use package-management checks, service logs, disk/memory/process observations and a known test workload. Practise a safe guest configuration error and rollback. Do not exhaust host resources. | Incident note that distinguishes the observed symptom, evidence, cause, fix and verification. |
| 7 · 23–29 Nov | Back up test-site data and relevant configuration to a separate lab backup location. Change/delete only disposable test data, then restore and compare. | Verified restore, checksums or content comparison, observed recovery duration and limitations of the backup location. |
| 8 · 30 Nov–6 Dec | Rebuild the basic service in a clean guest or safe fresh lab state using your runbook. Diagnose one mentor-selected service, permission or DNS variation. | Rebuild outcome and incident explanation without step-by-step AI direction; references allowed. **Gate B review.** |
| 9 · 7–13 Dec | Learn enough Bash to write a read-only service/disk health check: variables, conditions, exit codes and clear output. | Script with normal/failure test cases; explain every line. No automatic privileged repair. |
| 10 · 14–20 Dec | Run the check on a schedule in the guest using one scheduler. Capture timestamped results and test one safe service failure. | Explain when the check runs, where results go, how failures appear and what it cannot detect. |
| 11 · 21–27 Dec | Consolidate SSH, networking, recovery and health checks. This is a deliberately lighter/catch-up week: no new platform. | Repeat the weakest earlier task; tidy one incident report and remove unsupported claims from the portfolio. |
| 12 · 28 Dec–3 Jan | Run a small operations assessment: reach the service, diagnose one fault, restore test data and explain the monitoring result. Review vacancy/application feedback. | Demonstration with notes but no command-by-command prompting; readiness decision for cloud. **Gate C review.** |

### Progress gates

**Gate A — 8 November:** can explain host/guest/network roles, connect to the guest, serve a test page and recover the stopped lab service.

**Gate B — 6 December:** can apply and test access controls safely, investigate logs, restore real test data and repeat the basic setup from notes.

**Gate C — 3 January:** can explain and test the health-check script and handle a related troubleshooting variation. Select cloud based on relevant vacancies and access/cost constraints.

If a gate is not met, use the next week's technical time to close the specific gap and shift dependent tasks. Keep applications and short market reviews going. Do not restart all previous lessons.

## 5. Weeks 13–26: conditional cloud and employment continuation

These dates apply only if the prerequisite gates are passed. If affordable cloud access is unavailable, repeat the equivalent local administration tasks and label them local; do not claim cloud experience.

| Week / dates | Planned task | Proof / decision |
| --- | --- | --- |
| 13 · 4–10 Jan | Confirm Azure or one market-supported alternative. Learn the relationship between account, subscription, resource group, identity and permissions. Review pricing and cleanup before deploying. | One-page architecture and cost/access decision; no spending implied. |
| 14 · 11–17 Jan | Use an approved lab environment to deploy a small Linux VM, network and controlled management access. | Reach the guest; explain addressing and allowed traffic; record resource inventory. |
| 15 · 18–24 Jan | Deploy the same test service; distinguish cloud network rules, guest firewall and application/service faults. | Diagnose one safe access problem from evidence; verify the fix. |
| 16 · 25–31 Jan | Practise basic role-based access and least privilege with test identities where the lab permits. | Allowed/denied action test and explanation of scope; mark unavailable features untested. |
| 17 · 1–7 Feb | Configure affordable monitoring/log access and test one failure signal. | Observed signal, detection delay and known blind spots. |
| 18 · 8–14 Feb | Implement an approved backup method and restore dummy service data. Review costs and remove unused resources. | Actual restore evidence, resource cleanup check and cost review. **Gate D: cloud operations review.** |
| 19 · 15–21 Feb | Use one CLI to inspect resources and automate one small repeatable task. Azure CLI if Azure was chosen; do not add Python and PowerShell simultaneously. | Script with prerequisites, safe defaults and a repeat test. |
| 20 · 22–28 Feb | Consolidate the local/cloud runbook and demonstrate recovery from a safe lab failure. | Another person could follow the runbook; no credentials embedded. |
| 21 · 1–7 Mar | Docker basics only if target roles repeatedly request containers and earlier gates are passed. Otherwise practise the highest-frequency unresolved requirement. | One tested task. For Docker: run the test app, inspect logs and explain ports and data persistence. |
| 22 · 8–14 Mar | Repeat week 21 with a small variation; otherwise repair a weak core skill. | Explanation and repeat result, not a new tool list. |
| 23 · 15–21 Mar | Capstone incident drill combining service, networking or access checks, with a safe recovery path. | Concise incident timeline and verified resolution; distinguish lab work from employment. |
| 24 · 22–28 Mar | Portfolio review: select two or three strongest cases and one project overview. Practise explaining decisions aloud. | A clear five-minute project demonstration and accurate CV evidence. |
| 25 · 29 Mar–4 Apr | Mock technical interviews and focused applications. Address one recurring technical weakness. | Interview practice notes, revised explanation and application log kept private. |
| 26 · 5–11 Apr | Repeat the capstone with fewer hints. Review applications, feedback, skills and remaining barriers. | Evidence-based next step on 12 April; no guaranteed job outcome. |

**Gate D:** demonstrate secure access, a reachable service, useful monitoring, a tested recovery method and verified cleanup in the selected cloud lab. Record any unavailable or untested part honestly.

## 6. Career work without taking over the learning week

### First three Wednesdays: market evidence
The mentor gathers and verifies listings; the learner reviews fit and maps evidence. Aim for 10 distinct descriptions each week:
- IT operations / infrastructure support;
- junior systems / Linux administration;
- cloud / technical support.

Tag each listing by family; the split may change based on actual availability. Do not pad the sample with duplicate or ineligible advertisements to reach 30.

Record title, employer, source URL, date checked, location eligibility, mandatory versus preferred skills, experience, advertised salary or "not disclosed", and A/B/C mapping:
- A: can perform and demonstrate;
- B: related experience, needs a transfer test;
- C: genuinely missing.

Include Uganda-based jobs, remote roles with confirmed eligibility for Uganda, and relocation roles with explicit sponsorship evidence. "Remote" alone is not proof of eligibility. Expired postings may inform skills research but are not live application targets.

Use frequency and entry barriers to prioritize skills, not to promise employability. Windows/AD/Entra may replace optional later modules if the evidence strongly supports them; do not pile them on top of the core workload.

### From week 4
Use Wednesday for one or two well-matched applications when available; fewer is acceptable if tailoring takes longer. Do not wait for week 26 or a certificate. Seek a brief conversation with one practitioner or hiring contact every two weeks if feasible. Draft messages can be prepared, but the mentor must not send applications or messages without explicit authorization.

At weeks 4, 8, 12, 18 and 26, review:
- Which eligible jobs actually recur?
- Which requirements can you now demonstrate?
- Are screening conversations occurring? If not, examine targeting, CV evidence and eligibility before buying another course.
- What feedback is available? Lack of replies alone does not identify a technical skill gap.

Keep salary requirements, contacts, applications and employer feedback in a private tracker, not the public technical repository. No salary or hiring outcome is guaranteed.

## 7. Documentation and GitHub

Use the existing repository, not a new repository for every week:
- Local: `/home/suby/debian-linux-troubleshooting`
- [GitHub portfolio](https://github.com/hopeb6/debian-linux-troubleshooting)
- [Progress tracker](https://github.com/hopeb6/debian-linux-troubleshooting/blob/main/learning-progress.md)
- [Documentation workflow](https://github.com/hopeb6/debian-linux-troubleshooting/blob/main/docs/workflow.md)
- [Existing inventory evidence](https://github.com/hopeb6/debian-linux-troubleshooting/blob/main/journal/2026-10-09-virtualization-inventory.md)

Every meaningful attempt gets a short dated journal entry: goal, commands and execution location, sanitized output, interpretation, changes, verification, assistance and next step. Proposed commands are not completed work. Record failures too.

Publish reviewed checkpoints during active learning sessions under the existing authorization, and verify publication. Sunday is the weekly tidy/review point, not a reason to leave significant work undocumented. Check the Git diff; never upload secrets, private keys, employer records or unreviewed raw logs. A failed push must be reported, not silently called synchronized.

## 8. First week: exact daily checklist

- [ ] **Mon 12 Oct, 1h:** read the saved inventory. Explain how the virtual network could be active while Windows was off, and why that does not prove guest internet access. Inspect available RAM/disk read-only with guidance; choose a safe lab size. Do not repeat already-recorded checks merely for completion.
- [ ] **Tue 13 Oct, 1h:** obtain a Debian installer from the official source, verify it as instructed, and create a separate VM if capacity permits. Record any download/setup blocker.
- [ ] **Wed 14 Oct, 1h:** review the mentor's first 10 eligible/relevant job descriptions and mark requirements A/B/C. Keep personal application information private.
- [ ] **Thu 15 Oct, 1h:** continue the guest installation and confirm console login. Record guest identity and what was actually installed.
- [ ] **Fri 16 Oct, 30m:** add the few commands used to the question-based notebook, with purpose and execution location.
- [ ] **Sat 17 Oct, 3h:** finish setup, practise identifying host versus guest and inspect the guest network. Test SSH only if its setup and safe access have been established. Take a recoverable baseline using an appropriate lab method.
- [ ] **Sun 18 Oct, 1h:** explain and repeat one observation with notes; review and publish sanitized evidence; select the next unfinished task.

Installation delays are not failure. Finish the safe setup in week 2 rather than rushing security or pretending the week was completed.

## 9. How to ask for help each session

"Continue my infrastructure skills calendar. Read the current progress and latest journal first. Today's available time is __ minutes. Give me one small practical objective, explain the necessary concept, and state what success looks like. Tell me where commands run and their risks. Let me perform the learning steps and interpret the results. Give hints before a full solution. Record actual evidence and AI assistance, then review and publish the scoped documentation. Do not add unrelated tools or skip an unmet prerequisite."

## 10. Reference choices and cloud guardrails

Use existing Debian/man-page references first, plus official documentation for the selected lab. Read only what the current milestone requires.

- [Debian Reference](https://www.debian.org/doc/manuals/debian-reference/)
- [Microsoft Learn: Azure management tasks assessment](https://learn.microsoft.com/en-us/credentials/applied-skills/get-started-with-azure-management-tasks/)
- [Microsoft Learn: Entra identities and access assessment](https://learn.microsoft.com/en-us/credentials/applied-skills/get-started-with-identities-and-access-using-microsoft-entra/)
- [Azure budgets: behaviour and limitations](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-acm-create-budgets)

An assessment lab is not an unrestricted permanent practice environment. Verify current access, prerequisites and charges before using any cloud exercise. Budget alerts do not stop consumption or impose a hard spending cap. Do not activate a time-limited credit period long before being ready to use it.

**Planning review:** 12 October 2026. This schedule is mentor-assisted planning, not proof that the listed tasks have been performed.

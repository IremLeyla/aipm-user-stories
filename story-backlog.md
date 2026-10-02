# Story Backlog: Policy Assistant Pilot

Scenario: an internal AI assistant helps support agents find answers in approved policy documents. Pilot length: four weeks.

**How to read this backlog**

- **Origin: PM-accepted** = written in the warm-up and accepted after critique (1a, 2a, 3b).
- **Origin: Agent-proposed** = suggested by the agent. Not yet approved by the PM. Accept, edit or reject before creating issues.
- **Origin: Agent-proposed, PM-accepted / PM-edited** = suggested by the agent, then approved (or changed) by the PM.
- ⚠️ **Assumption** = not validated. No user research or business data sits behind it.
- Acceptance criteria for every story are in [acceptance-criteria.md](acceptance-criteria.md). Epics and scope are in [epic-map.md](epic-map.md).

## Overview

| ID | Title | Epic | Work type | Story quality | Risk area | Origin |
|---|---|---|---|---|---|---|
| US-01 | Cite and link the policy source | E1 | Story | Needs refinement | Source quality | PM-accepted (1a) |
| US-02 | Say clearly when policy doesn't cover a question | E1 | Story | Needs refinement | Source quality | Agent-proposed, PM-accepted |
| US-03 | Maintain the approved document list | E1 | Story | Needs refinement | Source quality | Agent-proposed, PM-edited |
| US-04 | Review queue for flagged answers | E2 | Story | Needs refinement | Human review | PM-accepted (2a) |
| US-05 | Let agents flag an answer they doubt | E2 | Story | Needs refinement | Human review | Agent-proposed, PM-accepted |
| US-06 | Add legal-approved disclaimer wording | E2 | Story | Needs refinement | Legal | Agent-proposed, PM-accepted |
| US-07 | Pilot impact report | E3 | Story | Needs refinement | Reliability | PM-accepted (3b) |
| US-08 | Rate whether an answer was correct | E3 | Story | Needs refinement | Reliability | Agent-proposed, PM-accepted |
| DT-01 | Define the flagging criteria | E2 | Requirement | Needs refinement | Human review | Agent-proposed, PM-accepted |
| DT-02 | Agree success criteria and baseline data | E3 | Requirement | Needs refinement | Reliability | Agent-proposed, PM-accepted |
| NFR-01 | Log every answer for audit | E2 | Requirement | Needs refinement | Privacy | Agent-proposed, PM-edited |

US = user story. DT = decision task (not a user story, but blocks stories). NFR = non-functional requirement.

---

## E1: Source-grounded answers

### US-01: Cite and link the policy source

**As a** support agent,
**I want** each answer to cite and link the approved policy section it's based on,
**so that** I can verify it before replying to the customer.

- Open question: Who decides which documents are approved? (see US-03)
- ⚠️ Assumption: The policy documents have sections or headings that can be cited.
- ⚠️ Assumption: Agents will open the source when they're unsure.
- Blocks Ready: owner of the approved-document list is unknown.

### US-02: Say clearly when policy doesn't cover a question

**As a** support agent,
**I want** the assistant to tell me clearly when approved policy doesn't cover a question,
**so that** I don't pass on an unsupported answer.

- ⚠️ Assumption: The assistant can reliably tell "not covered" apart from "covered but hard to find".

### US-03: Maintain the approved document list

**As a** policy owner,
**I want** to be the only role that can add, edit or delete documents on the approved list, with a visible change history,
**so that** the assistant only answers from current, approved policy and every change can be traced.

- PM edit: only policy owners have access to change the list. Each change shows what was done (created, edited, deleted), when, which policy owner did it, and an optional comment.
- Open question: Who is the policy owner? A named person or team is needed.
- Open question: When a document is deleted, what happens to past answers that cited it? Keeping a read-only copy for audit may be needed.
- ⚠️ Assumption: The policy documents are up to date (from the original warm-up Story 1).

---

## E2: Human review and safety

### US-04: Review queue for flagged answers

**As a** team lead,
**I want** flagged answers to appear in a review queue,
**so that** I can approve or reject them before an agent uses them.

- Open question: How fast must a lead review a flagged answer?
- ⚠️ Assumption: The assistant sits inside the workflow where answers get sent, so blocking is possible.
- ⚠️ Assumption: Leads have capacity to review flagged answers.
- Blocks Ready: depends on DT-01 (what gets flagged).

### US-05: Let agents flag an answer they doubt

**As a** support agent,
**I want** to flag an answer I'm unsure about,
**so that** a team lead reviews it before I use it with a customer.

- Why proposed: it gives US-04 something to review in week 1 without waiting for automatic risk rules.
- ⚠️ Assumption: Agents will flag honestly and not too often or too rarely.

### US-06: Add legal-approved disclaimer wording

**As a** support agent,
**I want** answers that need a disclaimer to include the legal-approved wording automatically,
**so that** I don't have to write it myself and the wording is always correct.

- Open question: Which answer types need a disclaimer? Decided together with DT-01 (rules 1 and 2), so legal answers both in one session.
- Depends on: DT-01.
- ⚠️ Assumption: Legal delivers the wording within the four-week pilot.

### DT-01: Define the flagging criteria (decision task)

Agree with support leads and legal which answers the assistant must flag for review.

- Output: a written list of flag rules, owned by a named person. Legal also marks which rules need a disclaimer (feeds US-06).
- ⚠️ Assumption: Leads and legal are available to agree on this in week 1.
- Trade-off: more rules mean more flags and more work for leads.

**Example output (illustrative only: real rules must come from leads and legal)**

| # | Flag when the answer… | Reviewer | Test question |
|---|---|---|---|
| 1 | involves money: refunds, compensation, fees | Team lead | "Can I get a refund after 30 days?" |
| 2 | touches legal topics: cancellation rights, liability, warranty | Legal | "Am I allowed to cancel my contract early?" |
| 3 | involves personal data: deletion or access requests | Privacy officer | "Please delete all my data." |
| 4 | is built on sources that conflict, or on a document marked "under review" | Policy owner | A question answered differently by two policies |
| 5 | concerns a complaint or a threat of legal action | Team lead | "I'll take this to court." |
| 6 | was flagged by the agent manually (US-05) | Team lead | Any answer the agent flags |

### NFR-01: Log every answer for audit (non-functional requirement)

Every answer is logged with the question, the answer, cited sources, flag status and review decision.

- PM edit: only policy owners, team leads, legal, the privacy officer and engineers can read the log. The pilot sponsor has no access and uses the US-07 report instead.
- Open question: What may be logged? Questions may contain customer personal data.
- ⚠️ Assumption: A retention period and access rules can be agreed with privacy or legal.

---

## E3: Pilot evidence

### US-07: Pilot impact report

**As a** pilot sponsor,
**I want** a report comparing answer time and escalation rate before and during the pilot,
**so that** I can judge whether it meets the agreed success criteria.

- Open question: What counts as "success" for the pilot? (see DT-02)
- ⚠️ Assumption: Comparable data from before the pilot exists and can be accessed.
- ⚠️ Assumption: Four weeks produces enough tickets to compare.
- Blocks Ready: depends on DT-02.

### US-08: Rate whether an answer was correct

**As a** support agent,
**I want** to mark whether an assistant answer was correct and usable,
**so that** the pilot team has accuracy data for the impact report.

- Why proposed: US-07 needs a source for "answers judged wrong".
- ⚠️ Assumption: Agent ratings are good enough as an accuracy signal. They may need spot checks by leads.

### DT-02: Agree success criteria and baseline data (decision task)

Agree with the pilot sponsor what "success" means and which pre-pilot data will be the baseline.

- Output: written success thresholds and a confirmed baseline data source.
- ⚠️ Assumption: The sponsor is available in week 1.
- ⚠️ Risk: there is probably no pre-pilot baseline for wrong answers. The team needs another comparison point, or the sponsor accepts that this metric is only checked against a threshold.

**Example output (illustrative only: values in brackets are set by the sponsor)**

| Metric | Success criterion | Baseline source |
|---|---|---|
| Handling time | Median drops by at least `[X]%` for the same ticket types | Ticket system export, `[4 weeks]` before the pilot |
| Escalation rate | Not higher than before the pilot | Ticket system escalation counts, same period |
| Wrong answers | No more than `[Y]%` of rated answers marked "Wrong" (US-08) | ⚠️ Probably none; see the risk above |
| Rating coverage | At least `[Z]%` of answers rated | n/a |
| Stop rule | Any wrong answer on a legal topic that reaches a customer triggers an immediate review | n/a |

---

## GitHub issues

Created 2026-10-02 with `gh issue create` after PM approval. All 11 added to the **User Stories Workshop** board (project #6): Status Backlog, fields Work Type, Story Quality and Risk area set.

| ID | Issue |
|---|---|
| US-01 | [#1 Cite and link the policy source](https://github.com/IremLeyla/aipm-user-stories/issues/1) |
| US-02 | [#2 Say clearly when policy doesn't cover a question](https://github.com/IremLeyla/aipm-user-stories/issues/2) |
| US-03 | [#3 Maintain the approved document list](https://github.com/IremLeyla/aipm-user-stories/issues/3) |
| US-04 | [#4 Review queue for flagged answers](https://github.com/IremLeyla/aipm-user-stories/issues/4) |
| US-05 | [#5 Let agents flag an answer they doubt](https://github.com/IremLeyla/aipm-user-stories/issues/5) |
| US-06 | [#6 Add legal-approved disclaimer wording](https://github.com/IremLeyla/aipm-user-stories/issues/6) |
| DT-01 | [#7 Define the flagging criteria](https://github.com/IremLeyla/aipm-user-stories/issues/7) |
| NFR-01 | [#8 Log every answer for audit](https://github.com/IremLeyla/aipm-user-stories/issues/8) |
| US-07 | [#9 Pilot impact report](https://github.com/IremLeyla/aipm-user-stories/issues/9) |
| US-08 | [#10 Rate whether an answer was correct](https://github.com/IremLeyla/aipm-user-stories/issues/10) |
| DT-02 | [#11 Agree success criteria and baseline data](https://github.com/IremLeyla/aipm-user-stories/issues/11) |

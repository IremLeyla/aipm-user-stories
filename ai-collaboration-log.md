# AI Collaboration Log

## Phase 2: Agent critique of the three warm-up stories

Prompt: "Act as a backlog refinement partner for an AI Project Manager. Review our three draft user stories…" (INVEST, unclear roles/goals/benefits, smaller version, acceptance criteria, assumptions; no GitHub issues, no invented evidence).

| Prompt or request | Accepted | Edited | Rejected | Reason |
|---|---|---|---|---|
| Story 1 split → **1a** cite and link the approved policy section | ✅ |  |  | _to add_ |
| Story 1 split → 1b "not covered by approved policy" message | | | | Not selected in this round — _decision/reason to add_ |
| Story 2 split → **2a** lead review queue for flagged answers | ✅ |  |  | _to add_ |
| Story 2 split → 2b define flagging criteria (spike) | | | | Not selected in this round — _decision/reason to add_ |
| Story 2 split → 2c legal-approved disclaimer wording | | | | Not selected in this round — _decision/reason to add_ |
| Story 3 split → 3a agree success criteria and baseline (decision task) | | | | Not selected in this round — _decision/reason to add_ |
| Story 3 split → **3b** before/during report on handling time and escalation rate | ✅ |  |  | _to add_ |

Accepted stories with their acceptance criteria and assumptions are in [05.1 PM-Warm-Up.md](05.1%20PM-Warm-Up.md) under "Refined stories".

## Phase 3: GitHub Project

| Prompt or request | Accepted | Edited | Rejected | Reason |
|---|---|---|---|---|
| Create board `User Stories Workshop` with six columns and fields (done by PM in the browser) | ✅ | | | Board created by PM; to be verified with `gh` in Phase 5 |

## Phase 4: Agent-built backlog

Prompt: "Create the workshop backlog for the Policy Assistant Pilot… Include at least eight user stories… Do not create GitHub issues until I approve."

Files created: [story-backlog.md](story-backlog.md), [acceptance-criteria.md](acceptance-criteria.md), [epic-map.md](epic-map.md), [ready-done-agreements.md](ready-done-agreements.md). This log updated.

| Item | Origin | Accepted | Edited | Rejected | Reason |
|---|---|---|---|---|---|
| US-01, US-04, US-07 | PM-accepted in Phase 2 | ✅ | | | Carried over unchanged |
| US-02 Not-covered message | Agent-proposed (was 1b) | ✅ | | | _reason to add_ |
| US-03 Approved document list | Agent-proposed | | ✏️ | | PM: only policy owners may add, edit or delete documents; change history must show action, time, which policy owner, and an optional comment |
| US-05 Agent flags answer | Agent-proposed | ✅ | | | _reason to add_ |
| US-06 Legal disclaimer | Agent-proposed (was 2c) | ✅ | | | _reason to add_ |
| US-08 Rate answer | Agent-proposed | ✅ | | | _reason to add_ |
| DT-01 Flagging criteria | Agent-proposed (was 2b) | ✅ | | | PM asked for examples; accepted the illustrative flag rules as example output |
| DT-02 Success criteria and baseline | Agent-proposed (was 3a) | ✅ | | | PM asked for examples; accepted the illustrative thresholds as example output |
| NFR-01 Audit log | Agent-proposed | | ✏️ | | PM: read access for policy owners, team leads, legal, privacy officer and engineers; agent suggested privacy officer, engineers and sponsor; PM added the first two and excluded the pilot sponsor |
| Epic map, scope boundaries, Ready/Done draft | Agent-proposed | ✅ | | | PM accepted |

| Link US-06 to DT-01 | Agent-proposed | ✅ | | | Legal decides flag rules and disclaimer types in one session |
| Bracket placeholders (US-06, NFR-01, DT-02) | Agent-proposed | ✅ | | | Kept as open questions with a named decider; they block Ready |
| Out-of-scope list, Ready/Done draft | Agent-proposed | ✅ | | | PM accepted the epic map (incl. scope boundaries) and the Ready/Done draft |

Deferred until human approval: nothing outstanding for GitHub.

## Phase 5: Agent-operated GitHub

| Prompt or request | Accepted | Edited | Rejected | Reason |
|---|---|---|---|---|
| Install GitHub CLI (`brew install gh`) and sign in with `project` scope | ✅ | | | Needed for Phases 5 and 6; PM authorised in browser |
| Plan: 11 issues, no labels, no separate epic issues; repo is public | ✅ | | | PM approved ("yes") |
| Create 11 issues with `gh issue create --body-file` | ✅ | | | All created; verified with `gh issue list` |

Verification (`gh issue list`): 11 of 11 issues present, no duplicates, no title mismatches, every issue has acceptance criteria, bodies match the local files.

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

| Prompt or request | Accepted | Edited | Rejected | Reason |
|---|---|---|---|---|
| Add 11 issues to project #6, all in Backlog, set Work Type / Story Quality / Risk area | ✅ | | | PM approved ("yes"). Issues were already auto-added; fields set with `gh project item-edit`; verified with `gh project item-list` (11 items, all fields correct) |

---

# AI Project Manager Audit Summary (2026-10-02)

## Files created or changed

| File | Change |
|---|---|
| [05.1 PM-Warm-Up.md](05.1%20PM-Warm-Up.md) | PM's three original stories kept; "Refined stories" section added (1a, 2a, 3b) |
| [story-backlog.md](story-backlog.md) | Created: 8 user stories, 2 decision tasks, 1 NFR, with assumptions and issue links |
| [acceptance-criteria.md](acceptance-criteria.md) | Created: Given/When/Then criteria for all 11 items |
| [epic-map.md](epic-map.md) | Created: 3 epics, dependencies, scope boundaries |
| [ready-done-agreements.md](ready-done-agreements.md) | Created: Definition of Ready and Done, board column meanings |
| ai-collaboration-log.md | Created: decisions for every phase, plus this summary |

These files are local only. They are not committed or pushed to GitHub yet.

## GitHub issues created

11 issues ([#1](https://github.com/IremLeyla/aipm-user-stories/issues/1)–[#11](https://github.com/IremLeyla/aipm-user-stories/issues/11)) in `IremLeyla/aipm-user-stories` (public). All 11 are on the [User Stories Workshop board](https://github.com/users/IremLeyla/projects/6) in Backlog with Work Type, Story Quality (Needs refinement) and Risk area set. Verified against local files: no missing items, duplicates or mismatches.

## Where the PM corrected the agent

- **US-03:** PM restricted add/edit/delete to policy owners and specified the change history (action, time, which policy owner, optional comment).
- **NFR-01:** PM set log readers (policy owners, team leads, legal, privacy officer, engineers) and excluded the pilot sponsor.
- **Phase 2:** PM selected only 1a, 2a and 3b from the agent's split suggestions.

## Assumptions still needing validation

- Policy documents are up to date and have citable sections (US-01, US-03).
- Someone is named as policy owner (US-03).
- The assistant sits inside the send workflow, so flagged answers can actually be blocked (US-04).
- Leads have capacity to review flagged answers (US-04, US-05).
- Legal delivers disclaimer wording and flag rules within the four-week pilot (US-06, DT-01).
- Comparable pre-pilot data exists and can be accessed (US-07, DT-02).
- Agent ratings are a good enough accuracy signal (US-08).

## Open decisions (`[brackets]`)

| Item | Decision | Decider |
|---|---|---|
| US-06 / DT-01 | Which answer types need a disclaimer | Legal |
| NFR-01 | Log retention period | Privacy officer |
| DT-02 | Success thresholds `[X]`, `[Y]`, `[Z]` and baseline period | Pilot sponsor |

## Risks or weak stories to revisit

- **US-04:** if the assistant can't block sending, criterion 1 can't be met and the story needs rethinking.
- **US-07:** probably no pre-pilot baseline for wrong answers; that metric may only be checkable against a threshold.
- **US-03:** what happens to past answers that cited a deleted document is unresolved.
- **NFR-01:** questions may contain customer personal data; privacy review needed before logging starts.
- **Capacity:** 11 items for a four-week pilot has not been sized. Worth checking with the team which items are truly needed for the pilot.
- **Reasons column:** several accepted items in this log still have no recorded reason.

## Commands and tools used

- `brew install gh`; `gh auth login --web --scopes project` (PM authorised in the browser)
- Read-only checks: `gh auth status`, `gh repo view`, `gh label list`, `gh project list`, `gh project field-list`, `gh issue list`, `gh project item-list`
- Changes (each after PM approval): `gh issue create --body-file` (×11), `gh project item-add` and `gh project item-edit` (fields for 11 items)
- Local file edits in this workspace

## Refused or deferred until human approval

- Did not write the warm-up stories for the PM (Phase 1 is manual by design).
- Did not invent user research, thresholds, retention periods or disclaimer types; left them as `[brackets]` with a named decider.
- Did not create issues or touch the board until the PM said "yes" each time.
- Did not add labels or separate epic issues (proposed, PM kept it simple).
- Did not fill in the PM's reasons in this log.
- Did not commit or push the local files to GitHub.

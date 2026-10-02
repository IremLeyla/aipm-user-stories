# Acceptance Criteria: Policy Assistant Pilot

Stories are in [story-backlog.md](story-backlog.md). Values in `[brackets]` are placeholders that a human still has to decide. They are not facts.

## E1: Source-grounded answers

### US-01: Cite and link the policy source (PM-accepted)

1. Given an answer, when it's displayed, then it shows the document title, the section and a link that opens that section.
2. Given an answer drawn from more than one document, then every source is listed.
3. Given a document that isn't on the approved list, then it is never cited.

### US-02: Say clearly when policy doesn't cover a question (agent-proposed, PM-accepted)

1. Given a question that no approved document covers, then the assistant shows "I couldn't find this in approved policy" and gives no answer.
2. Given that message, then the agent sees a way to escalate the question, for example to a team lead.
3. Given a "not covered" result, then it is logged so policy gaps can be reviewed.

### US-03: Maintain the approved document list (agent-proposed, PM-edited)

1. Given a policy owner, when they add a document to the approved list, then the assistant can cite it.
2. Given a policy owner, when they edit a document, then the assistant cites the updated version.
3. Given a policy owner, when they delete a document, then the assistant no longer cites it.
4. Given a user who isn't a policy owner, then they can't add, edit or delete documents on the list.
5. Given any change, then the change history shows the action (created, edited or deleted), the date and time, which policy owner made it, and their comment if they left one.
6. Given a change, then the comment is optional and the change can be saved without one.

## E2: Human review and safety

### US-04: Review queue for flagged answers (PM-accepted)

1. Given a flagged answer, then the agent sees it marked "Needs review" and can't mark it as ready to send.
2. Given a flagged answer, then it appears in the lead's queue with the question, the answer and its sources.
3. Given a lead who approves or rejects an answer, then the agent sees that decision and any comment.

### US-05: Let agents flag an answer they doubt (agent-proposed, PM-accepted)

1. Given an answer, then the agent can flag it with one action and an optional comment.
2. Given a flagged answer, then it appears in the US-04 review queue.
3. Given a flagged answer, then it is marked "Needs review" until a lead decides.

### US-06: Add legal-approved disclaimer wording (agent-proposed, PM-accepted)

1. Given an answer of a type that needs a disclaimer `[types defined by legal in DT-01]`, then the approved wording is added unchanged.
2. Given that legal updates the wording, then new answers use the updated wording.
3. Given an answer type with no disclaimer rule, then no disclaimer is added.

### DT-01: Define the flagging criteria (decision task)

1. A written list of flag rules exists and has a named owner.
2. Support leads and legal have confirmed the list.
3. Each rule is specific enough to test against example questions.
4. Legal has marked which rules also need a disclaimer (input for US-06).

### NFR-01: Log every answer for audit (requirement)

1. Every answer is logged with the time, question, answer, cited sources, flag status and review decision.
2. Only policy owners, team leads, legal, the privacy officer and engineers can read the log.
3. Given any other user, including the pilot sponsor, then they can't open the log.
4. Log entries are deleted after `[retention period agreed with privacy or legal]`.

## E3: Pilot evidence

### US-07: Pilot impact report (PM-accepted)

1. The report shows median handling time before and during the pilot for the same ticket types.
2. The report shows the escalation rate and the rate of answers judged wrong (using an agreed definition) for both periods.
3. The report states the date range and the number of tickets in each period.
4. Each metric shows whether it meets the agreed success threshold.

### US-08: Rate whether an answer was correct (agent-proposed, PM-accepted)

1. Given an answer, then the agent can mark it "Correct", "Partly correct" or "Wrong".
2. Given a rating, then it is stored with the answer and is available to the US-07 report.
3. Given an answer that isn't rated, then it is counted as "Not rated" and not as correct.

### DT-02: Agree success criteria and baseline data (decision task)

1. Success thresholds for handling time, escalation rate and wrong-answer rate are written down `[values set by sponsor]`.
2. A baseline data source for the period before the pilot is confirmed as accessible.
3. The sponsor has signed off both.

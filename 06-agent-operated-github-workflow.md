# Agent-Operated GitHub Workflow

Use this file only after the group has draft stories. The goal is to let Claude
Code or Codex operate GitHub while the AI Project Manager approves and verifies.

## Setup Check

Run:

```bash
gh auth status
```

If project access is missing:

```bash
gh auth refresh -s project
```

Sources:

- [GitHub CLI `gh issue create`](https://cli.github.com/manual/gh_issue_create)
- [GitHub CLI `gh project`](https://cli.github.com/manual/gh_project)
- [Claude Code MCP](https://docs.anthropic.com/en/docs/claude-code/mcp)
- [Claude Code Skills](https://docs.anthropic.com/en/docs/claude-code/skills)
- [Codex GitHub integration](https://developers.openai.com/codex/integrations/github)

## Step 1: Ask for a Plan

```text
You are helping me act as an AI Project Manager.

Read the local backlog files.
Prepare a short plan to create the approved backlog in GitHub.

Include:
- issue titles;
- issue bodies;
- labels if useful;
- commands you want to run;
- assumptions that still need human validation.

Do not execute commands yet.
```

Approve only if the stories are specific, testable, and tied to the scenario.

## Step 2: Create Issues

After approval, let the agent run `gh issue create`.

Example:

```bash
gh issue create \
  --title "Show source metadata in search results" \
  --body "As a support agent,
I want each result to show the policy title, section, and last-updated date,
so that I can judge whether the source is trustworthy before answering a customer.

Acceptance criteria:
- Each result shows policy title, section heading, and last-updated date.
- Results from retired policy documents are excluded.
- If the date is missing, the result is labeled date unavailable.
- A support agent can open the referenced policy section from the result."
```

Ask the agent to save issue URLs in `story-backlog.md` or
`ai-collaboration-log.md`.

## Step 3: Verify GitHub State

Ask the agent to run:

```bash
gh issue list --limit 20
```

Then ask:

```text
Compare GitHub issues with story-backlog.md.

Report:
- missing issues;
- duplicates;
- title mismatches;
- stories without acceptance criteria;
- assumptions still needing validation.

Do not edit anything until I approve.
```

## Step 4: Add Issues to the Project

If time allows, add issues to the GitHub Project.

The agent should first inspect the project:

```bash
gh project list --owner <owner>
gh project item-list <project-number> --owner <owner>
```

Then ask:

```text
Find the project named User Stories Workshop.
Prepare the commands to add the approved issues to it.
Show the owner, project number, and issue URLs.
Do not execute until I approve.
```

If this takes too long, stop. Having verified issues is enough for the main
exercise.

## Step 5: MCP Comparison

If Claude Code or Codex has a connected GitHub tool or MCP server, compare it
with `gh`.

Prompt:

```text
Do you have a connected GitHub tool or MCP server available?

If yes:
- list what GitHub actions you can perform;
- propose one read-only check first;
- explain how permission boundaries work.

If no:
- explain what setup would be needed;
- continue using gh.
```

Use this comparison:

| Dimension | `gh` command line | MCP or connected tool |
|---|---|---|
| Visibility | Commands are explicit | Tool calls may be more abstract |
| Setup | GitHub CLI auth | Connector or MCP setup |
| Best use | Transparent workshop operation | Smoother multi-tool workflows |
| PM duty | Approve commands and verify output | Approve tool access and verify state |

## Final Audit Prompt

```text
Create a short AI Project Manager audit summary.

Include:
- files changed;
- issues created;
- project items added, if any;
- commands or tools used;
- assumptions still unvalidated;
- actions deferred for human approval.
```

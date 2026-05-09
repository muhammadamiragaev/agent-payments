---
tracker:
  kind: linear
  api_key: $LINEAR_API_KEY
  project_slug: "mvp-3de374e9878a"
  active_states:
    - Todo
    - In Progress
  terminal_states:
    - Done
    - Closed
    - Cancelled
    - Canceled
    - Duplicate

polling:
  interval_ms: 15000

workspace:
  root: /Users/web3muhammad/Documents/symphony-workspaces

hooks:
  after_create: |
    git clone git@github.com:muhammadamiragaev/agent-payments.git .

agent:
  max_concurrent_agents: 1
  max_turns: 5

codex:
  command: codex app-server
---

You are working on Linear issue {{ issue.identifier }}.

Title:
{{ issue.title }}

Description:
{{ issue.description }}

Rules:
- Work only inside the current workspace.
- Keep changes minimal and directly tied to the Linear issue.
- Do not add speculative abstractions.
- Do not edit unrelated files.
- Run relevant tests or checks before finishing.
- If the task is unclear, blocked, or requires secrets, stop and explain the blocker.
- When finished, summarize changed files and validation performed.


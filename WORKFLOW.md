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
  interval_ms: 60000

workspace:
  root: /Users/web3muhammad/Documents/symphony-workspaces

hooks:
  after_create: |
    git clone https://github.com/muhammadamiragaev/agent-payments.git .

agent:
  max_concurrent_agents: 1
  max_turns: 1

codex:
  command: codex app-server
  approval_policy: never
  thread_sandbox: danger-full-access
  turn_sandbox_policy:
    type: dangerFullAccess
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
- If the task requires repository changes, do not move the issue to Done until the changes are committed and pushed.
- Do not move the issue to Done when no repository files changed unless the task was explicitly analysis-only or no-op.
- When the task is complete, use the available Linear tool to move the issue to Done before your final response.
- Do not end with the issue still in Todo or In Progress unless you are blocked.
- When finished, summarize changed files, validation performed, commit/push status, and the final Linear state.

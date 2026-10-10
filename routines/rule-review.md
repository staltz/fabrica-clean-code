---
description: On each new commit to a pull request, check AGENTS.md and Cursor rules and comment on violations
trigger: { on: github.pull_request.synchronize }
connectors: [github]
side_effects:
  - github.pr_comment
---
New commits were pushed to a pull request.

Review whether the pull request in question is violating any of the rules in AGENTS.md. If there are any violations, then flag those as code review comments, preferably inline.

When you comment on the pull request, always have the first sentence be either "**Rules: passed.** ☘️" or "**Rules: violated.** 🥀"

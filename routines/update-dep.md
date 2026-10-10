---
description: Twice a week, bump one random dependency to its second-latest version and open a pull request if Socket scores pass
trigger: { on: schedule, cron: "0 5 * * 2,4" }
connectors: [github, socket]
side_effects:
  - github.push
  - github.open_pull_request
---
It's time for the scheduled dependency update.

Pick a random open source dependency in this repository, and with the help of the package manager, update it to its 2nd latest version. Use the Socket MCP to ensure that the minimum score (across the 5 score dimensions) of the new package version is at least 70%. If it is less then 70%, then abort yourself.

If problems arise such as breaking changes, adapt the codebase to continue functioning like before, perhaps you may need to fix CI failures as well. Then open a pull request (with a title that starts with "update-dep: ").

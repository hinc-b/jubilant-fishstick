---
name: update-github-info
on:
  schedule:
    - cron: "17 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
tools:
  edit: true
  github:
    toolsets:
      - repos
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    max: 1
---

# Update GitHub Info

Read `notes/mona-notes.md` before making any changes.

Use the repository's GitHub API tools to read any repository guidance or reference files you need. Do not use terminal, CLI, or sandboxed commands for repository guidance.

Fetch and review both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with a short, practical summary of the most useful current GitHub updates for developers. Keep the existing editorial angle, mention the source for every update, and preserve useful existing content unless it is outdated.

When a change is needed, use the edit tool only on `site/content/github-info.md`. Then use the `create-pull-request` safe output to open a draft pull request for Mona to review. Do not write directly to the default branch.

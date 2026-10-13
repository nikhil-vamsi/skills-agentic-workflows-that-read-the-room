---
name: update-github-info
description: Refresh GitHub Info with practical highlights from the GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
tools:
  edit: true
  web-fetch: {}
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    reviewers:
      - mona
    draft: false
    allowed-files:
      - site/content/github-info.md
---

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before making changes.

Use the web-fetch tool to read:

- https://github.blog/latest/
- https://github.blog/changelog/

Select recent, verifiable updates that fit Mona's editorial angle and help developers learn GitHub faster. Keep summaries short and practical, preserve the existing page's structure, and cite the specific source article or changelog entry for every new fact. Do not invent details or include an item unless its source supports it.

Update only `site/content/github-info.md`. If the sources do not warrant a change, report `noop`. Otherwise, propose the update through the configured create-pull-request safe output, with a concise description of the changes and sources, for Mona to review. Never write directly to the default branch.

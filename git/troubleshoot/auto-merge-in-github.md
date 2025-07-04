---
description: dev -> main
cover: ../../.gitbook/assets/image (173).png
coverY: -41.37142857142858
---

# Auto-merge in github

Yaml file for automerge

Path: .github/workflows/merge.yml

```yaml
name: automerge

on:
  push:
    branches: [ "dev" ]
    
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: pascalgn/automerge-action@v0.16.2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          MERGE_LABELS: "automerge,!work in progress"
          MERGE_REMOVE_LABELS: ""
          MERGE_METHOD: "merge"
          MERGE_COMMIT_MESSAGE: "pull-request-description"
          MERGE_FORKS: "false"
          MERGE_RETRIES: "6"
          MERGE_RETRY_SLEEP: "10000"
          MERGE_REQUIRED_APPROVALS: "0"
          UPDATE_LABELS: ""
          UPDATE_METHOD: "merge"
          BASE_BRANCHES: "main"
          # PULL_REQUEST: "8"

      - name: Merge pull requests (automerge-action)
        run: echo "Automerge action completed successfully"
```

Issue found on GitHub actions.

[![automerge](https://github.com/whoami-anoint/probex/actions/workflows/merge.yml/badge.svg)](https://github.com/whoami-anoint/probex/actions/workflows/merge.yml)

```
 env:
    GITHUB_TOKEN: ***
    MERGE_LABELS: automerge,!work in progress
    MERGE_REMOVE_LABELS: 
    MERGE_METHOD: merge
    MERGE_COMMIT_MESSAGE: pull-request-description
    MERGE_FORKS: false
    MERGE_RETRIES: 6
    MERGE_RETRY_SLEEP: 10000
    MERGE_REQUIRED_APPROVALS: 0
    UPDATE_LABELS: 
    UPDATE_METHOD: merge
    BASE_BRANCHES: main
2024-02-12T10:52:06.080Z INFO  Event name: push
2024-02-12T10:52:06.478Z INFO  Open PRs: 1
2024-02-12T10:52:06.478Z INFO  Updating PR #19 Update text.txt
2024-02-12T10:52:06.755Z INFO  No update necessary, mergeable_state: clean
2024-02-12T10:52:06.756Z INFO  1 PRs based on dev have been updated
2024-02-12T10:52:06.756Z INFO  Action result: undefined
2024-02-12T10:52:06.756Z ERROR invalid result!
```

Doubt on:&#x20;

**Merge conflict**\
Resources:&#x20;

[https://stackoverflow.com/questions/161813/how-do-i-resolve-merge-conflicts-in-a-git-repository](https://stackoverflow.com/questions/161813/how-do-i-resolve-merge-conflicts-in-a-git-repository)\
[https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows](https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows)\
\
Custom actions: \
[https://docs.github.com/en/actions/creating-actions/about-custom-actions](https://docs.github.com/en/actions/creating-actions/about-custom-actions)


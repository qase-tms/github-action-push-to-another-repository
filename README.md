# github-action-push-to-another-repository
Completed action for pushing and creating PR in the Github repo from the actions

## Example

```yaml
name: generate-client

on:
  push:
    branches:
      - test-branch

jobs:
  generate_js_client:
    runs-on: ubuntu-latest
    steps:
      - name: Commit and push changes
        uses: qase-tms/github-action-push-to-another-repository@main
        with:
          target-repo-owner: 'qase-tms'
          target-repo-name: 'qase-javascript'
          target-repo-path: 'qase-javascript'
          source-repo-path: 'specs'
          build-command: './Taskfile typescript'
          source-copy-dir: ./specs/examples/sdk/ts/*
          target-copy-dir: ./qase-javascript/qaseio/src
          commit-message: '[build] update client'
          git-username: 'Andranik Petrosyan'
          git-email: 'apetrosyan@qase.io'
          base-pr-branch: 'master'
          pr-title: 'Specs updated'
          pr-body: 'This PR is auto-generated'
          token: ${{ secrets.API_TOKEN_GITHUB }}
```
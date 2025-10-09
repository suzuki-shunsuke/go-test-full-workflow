# go-test-full-workflow

GitHub Actions Reusable Workflow to test Go application

## How to use

```yaml
---
name: test
on:
  pull_request: {}
jobs:
  test:
    uses: suzuki-shunsuke/go-test-full-workflow/.github/workflows/test.yaml@10238675cfaeb021a013ac656c58babe6ff69a62 # v5.0.0
    with:
      aqua_policy_config: aqua-policy.yaml
      aqua_version: v2.55.0
      go-version: 1.25.2
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
    permissions:
      pull-requests: write
      contents: read # To checkout private repository
```

## Requirements

```sh
aqua g -i golangci/golangci-lint reviewdog/reviewdog suzuki-shunsuke/ghalint crate-ci/typos goreleaser/goreleaser google/go-licenses 
```

GitHub App

- `contents: write`: To update aqua-checksums.json and merge pull requests
- `pull-requests: write`: To enable automerge

## LICENSE

[MIT](LICENSE)

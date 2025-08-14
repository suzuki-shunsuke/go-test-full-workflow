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
    uses: suzuki-shunsuke/go-test-full-workflow/.github/workflows/test.yaml@98b1d118f22667c10788ac678906b0caef8909ba # v2.0.0
    with:
      aqua_policy_config: aqua-policy.yaml
      aqua_version: v2.44.0
      go-version: 1.24.0
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
    permissions:
      pull-requests: write
      contents: read # To checkout private repository
```

## Requirements

```sh
aqua g -i golangci/golangci-lint reviewdog/reviewdog suzuki-shunsuke/ghalint crate-ci/typos
```

GitHub App

- `contents: write`: To update aqua-checksums.json and merge pull requests
- `pull-requests: write`: To enable automerge

## LICENSE

[MIT](LICENSE)

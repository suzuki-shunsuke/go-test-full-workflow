# go-test-full-workflow

GitHub Actions Reusable Workflow to test Go application

## How to use

```yaml
---
name: test
on:
  pull_request: {}
permissions: {}
jobs:
  test:
    uses: suzuki-shunsuke/go-test-full-workflow/.github/workflows/test.yaml@main
    with:
      aqua_policy_config: aqua-policy.yaml
      aqua_version: v1.32.3
      go-version: 1.19.5
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
    permissions:
      pull-requests: write
      contents: read # To checkout private repository
```

## Requirements

```sh
aqua g -i int128/ghcp golangci/golangci-lint reviewdog/reviewdog suzuki-shunsuke/ghalint
```

GitHub App

* `contents: write`: To update aqua-checksums.json and merge pull requests
* `pull-requests: write`: To enable automerge

## LICENSE

[MIT](LICENSE)

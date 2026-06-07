# go-test-full-workflow

[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/suzuki-shunsuke/go-test-full-workflow)
[workflow](.github/workflows/test.yaml)

GitHub Actions Reusable Workflow to test Go application

## How to use

```yaml
---
name: test
on: pull_request
jobs:
  test:
    uses: suzuki-shunsuke/go-test-full-workflow/.github/workflows/test.yaml@596bc52a7f02dd896d3351e61e4dfa661c1f3304 # v5.0.1
    with:
      aqua_version: v2.59.1
      go-version-file: go.mod
    secrets:
      TAKUMI_GUARD_BOT_ID: ${{secrets.TAKUMI_GUARD_BOT_ID}} # Optional. https://github.com/flatt-security/setup-takumi-guard-golang
    permissions:
      pull-requests: write
      contents: read # To checkout private repository
      id-token: write # For takumi guard. https://github.com/flatt-security/setup-takumi-guard-golang
```

## Requirements

```sh
aqua g -i golangci/golangci-lint reviewdog/reviewdog suzuki-shunsuke/ghalint crate-ci/typos goreleaser/goreleaser google/go-licenses 
```

## LICENSE

[MIT](LICENSE)

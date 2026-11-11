# sharkops-io/.github

Shared GitHub Actions for every sharkops-io repo. Each repo's own workflow is a
short caller; no build steps are copied into repos.

| Workflow | Does | Ported from (GitLab) |
|---|---|---|
| `secret-scan.yml` | gitleaks over full history, with the hex-credential and YAML name/value rules | `security/secret-scan.yml` |
| `go.yml` | golangci-lint + `go test -race` | `go/ci.yml` |
| `image.yml` | Buildx build; push to GHCR on main (`:main`, `:sha-*`) and tags (`:vX`, `:latest`) | `docker/build.yml` |
| `chart.yml` | helm lint/template, examples, helm-unittest; on a `X.Y.Z` tag pushes to `oci://ghcr.io/sharkops-io/charts` | each chart's `.gitlab-ci.yml` |
| `import-from-gitlab.yml` | One-off crane copy of release tags from registry.gitlab.com, same digests | (migration only) |
| `promtool.yml` | `promtool check/test` on `examples/rules.yaml` when present | `prometheus/rules.yml` |

A caller, for an exporter:

```yaml
name: ci
on:
  pull_request:
  push:
    branches: [main]
    tags: ["v*"]
jobs:
  secret-scan:
    uses: sharkops-io/.github/.github/workflows/secret-scan.yml@main
  go:
    uses: sharkops-io/.github/.github/workflows/go.yml@main
  rules:
    uses: sharkops-io/.github/.github/workflows/promtool.yml@main
  image:
    needs: [secret-scan, go, rules]
    uses: sharkops-io/.github/.github/workflows/image.yml@main
    permissions: { contents: read, packages: write }
```

## License

Apache License 2.0. See [LICENSE](LICENSE).

Open-source building blocks from a Kubernetes cluster run through GitOps:
Helm charts, Prometheus exporters and CI images. Everything here is
Apache-2.0 licensed.

### Helm charts

Published to `oci://ghcr.io/sharkops-io/charts`.

| Chart | What it is |
|---|---|
| [sharkops-universal](https://github.com/sharkops-io/sharkops-universal) | Run any container image: Deployment, Service, Ingress, PVCs, probes, env from ConfigMaps and Secrets |
| [cnpg-cluster](https://github.com/sharkops-io/cnpg-cluster) | A CloudNativePG Postgres cluster with Barman Cloud WAL archiving to S3-compatible storage |
| [oidc-proxy-ingress](https://github.com/sharkops-io/oidc-proxy-ingress) | Put an in-cluster service behind oauth2-proxy and an Ingress, against any OIDC issuer |
| [sharkops-netpol](https://github.com/sharkops-io/sharkops-netpol) | Default-deny ingress NetworkPolicy plus a Cilium ingress policy for a namespace |

```sh
helm install app oci://ghcr.io/sharkops-io/charts/sharkops-universal --version <version>
```

### Prometheus exporters

| Exporter | Exports |
|---|---|
| [adguard-exporter](https://github.com/sharkops-io/adguard-exporter) | AdGuard Home |
| [unas-protect-exporter](https://github.com/sharkops-io/unas-protect-exporter) | UniFi UNAS and UniFi Protect |
| [gameserver-exporter](https://github.com/sharkops-io/gameserver-exporter) | Palworld and Satisfactory dedicated servers |
| [netpol-coverage-exporter](https://github.com/sharkops-io/netpol-coverage-exporter) | Per-pod NetworkPolicy and CiliumNetworkPolicy coverage |
| [exporter-common](https://github.com/sharkops-io/exporter-common) | The Go library they share |

### Images and tools

| Repo | What it is |
|---|---|
| [k8s-cli-tools](https://github.com/sharkops-io/k8s-cli-tools) | Multi-arch CI image with kubectl, Helm, helmfile, kustomize and the Rancher CLI |
| [docker-api-gateway](https://github.com/sharkops-io/docker-api-gateway) | A read-only slice of the Docker Engine API behind a bearer token |
| [.github](https://github.com/sharkops-io/.github) | The shared GitHub Actions workflows every repo here calls |

Images are on GHCR under `ghcr.io/sharkops-io/<repo>`.

# static-site

[![Hosted By: Cloudsmith](https://img.shields.io/badge/OSS%20hosting%20by-cloudsmith-blue?logo=cloudsmith&style=for-the-badge)](https://cloudsmith.com)

This is a Helm Chart for a hardened Apache Web Server with content sync with a GitHub repository, and https certificate sourced from LetsEncrypt.

The Helm Chart contains the following resources:

- clusterissuer.yaml: Set the `issuer` definition in values.yaml
- certificate.yaml: Set the `certificate` definition in values.yaml
- configmap.yaml: This loads a minimal `httpd.conf` file, with security hardening appropriate for a static site
- deployment.yaml: This spins up Apache, with a git-sync-sidecar, and uses the `httpd.conf` configmap
- ingress.yaml: Set the `ingres` definition in values.yaml
- service.yaml: Service endpoint for the deployment
- serviceaccount.yaml: Service Account for the deployment

Package repository hosting is graciously provided by  [Cloudsmith](https://cloudsmith.com).

```text
Cloudsmith is the only fully hosted, cloud-native, universal package management solution, that
enables your organization to create, store and share packages in any format, to any place, with total
confidence.
```

## GitHub pages and ArtefactHUB

For more control - specifically to manage the index.yaml file, a new gitHub repo was created for podzone charts, with a gitHub Pages site publishing the index and chart artefacts.

- Github Pages: <https://motttt.github.io/charts/>
- Github Pages Index: <https://motttt.github.io/charts/index.yaml>
- ArtefactHUB: <https://artifacthub.io/packages/search?user=MoTTTT>

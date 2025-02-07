# tangle

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.0](https://img.shields.io/badge/AppVersion-0.0.0-informational?style=flat-square)

Tangle is a helper app that makes using multiple ArgoCDs in a hub & spoke model fun and easy!.

**Homepage:** <https://github.com/ivanklee86/tangle>

## Source Code

* <https://github.com/ivanklee86/tangle>
* <https://github.com/ivanklee86/tangle-charts/charts/tangle>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `3` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| deployment.affinity | object | `{}` |  |
| deployment.livenessProbe.httpGet.path | string | `"/health"` |  |
| deployment.livenessProbe.httpGet.port | string | `"http"` |  |
| deployment.nodeSelector | object | `{}` |  |
| deployment.podAnnotations | object | `{}` |  |
| deployment.podLabels | object | `{}` |  |
| deployment.podSecurityContext | object | `{}` |  |
| deployment.readinessProbe.httpGet.path | string | `"/health"` |  |
| deployment.readinessProbe.httpGet.port | string | `"http"` |  |
| deployment.resources | object | `{}` |  |
| deployment.securityContext | object | `{}` |  |
| deployment.tolerations | list | `[]` |  |
| deployment.volumeMounts | list | `[]` |  |
| deployment.volumes | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/ivanklee86/tangle"` |  |
| image.tag | string | `"v0.0.1"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `"tangle"` |  |
| replicaCount | int | `1` |  |
| service.port | int | `8080` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tangle.argoCDs | object | `{}` | Configures connection to ArgoCDs. |
| tangle.configPath | string | `"/etc/tangle"` | Path configuration file is mounted. |
| tangle.sortOrder | list | `[]` |  |
| tangle.tokenSecrets | list | `[]` |  |

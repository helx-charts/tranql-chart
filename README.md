# tranql

![Version: 0.4.2](https://img.shields.io/badge/Version-0.4.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.4.0](https://img.shields.io/badge/AppVersion-0.4.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | redis | 15.4.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| existingRedis | object | `{"host":"","password":"","port":"","secret":"","secretPasswordKey":""}` | Existing redis configuration, if used this will take presidence over redis connection deployed by enabling redis. |
| gunicorn.workerCount | int | `4` | (int) Gunicorn worker count |
| gunicorn.workerTimeout | int | `1600` | (int) Gunicorn worker timeout |
| image | string | `"helxplatform/tranql"` | Image repository |
| imageTagOverride | string | `""` | Overrids default is Chart.appversion image tag |
| ingress.annotations."cert-manager.io/cluster-issuer" | string | `"letsencrypt"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.host | string | `""` |  |
| ingress.pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls.secretName | string | `""` |  |
| port | int | `8081` | (int) Tranql web server port |
| redis.auth.enable | bool | `true` |  |
| redis.auth.password | string | `"changeme"` |  |
| redis.clusterDomain | string | `"cluster.local"` |  |
| redis.commonConfiguration | string | `"appendonly no"` |  |
| redis.enabled | bool | `true` |  |
| redis.image.repository | string | `"redislabs/redisgraph"` |  |
| redis.image.tag | string | `"2.8.4"` |  |
| redis.master.command | string | `""` |  |
| redis.master.extraFlags[0] | string | `"--loadmodule"` |  |
| redis.master.extraFlags[1] | string | `"/usr/lib/redis/modules/redisgraph.so"` |  |
| redis.master.extraFlags[2] | string | `"THREAD_COUNT"` |  |
| redis.master.extraFlags[3] | string | `"8"` |  |
| redis.master.extraFlags[4] | string | `"OMP_THREAD_COUNT"` |  |
| redis.master.extraFlags[5] | string | `"16"` |  |
| redis.master.extraFlags[6] | string | `"--appendonly"` |  |
| redis.master.extraFlags[7] | string | `"no"` |  |
| redis.master.initContainers[0].args[0] | string | `"https://stars.renci.org/var/kgx_data/roger_graph_v3.0.rdb"` |  |
| redis.master.initContainers[0].args[1] | string | `"-O"` |  |
| redis.master.initContainers[0].args[2] | string | `"/data/dump.rdb"` |  |
| redis.master.initContainers[0].command[0] | string | `"wget"` |  |
| redis.master.initContainers[0].image | string | `"busybox"` |  |
| redis.master.initContainers[0].name | string | `"init-db"` |  |
| redis.master.initContainers[0].securityContext.runAsGroup | int | `1001` |  |
| redis.master.initContainers[0].securityContext.runAsUser | int | `1001` |  |
| redis.master.initContainers[0].volumeMounts[0].mountPath | string | `"/data"` |  |
| redis.master.initContainers[0].volumeMounts[0].name | string | `"redis-data"` |  |
| redis.master.livenessProbe.enabled | bool | `false` |  |
| redis.master.persistence.size | string | `"15Gi"` |  |
| redis.master.readinessProbe.enabled | bool | `true` |  |
| redis.master.readinessProbe.failureThreshold | int | `1` |  |
| redis.master.readinessProbe.periodSeconds | int | `1` |  |
| redis.master.resources.limits.cpu | string | `"1000m"` |  |
| redis.master.resources.limits.memory | string | `"15Gi"` |  |
| redis.master.resources.requests.cpu | string | `"200m"` |  |
| redis.master.resources.requests.memory | string | `"12Gi"` |  |
| redis.replica.autoscaling.enabled | bool | `true` |  |
| redis.replica.autoscaling.maxReplicas | int | `2` |  |
| redis.replica.autoscaling.minReplicas | int | `1` |  |
| redis.replica.autoscaling.targetCPU | int | `100` |  |
| redis.replica.extraFlags[0] | string | `"--loadmodule"` |  |
| redis.replica.extraFlags[1] | string | `"/usr/lib/redis/modules/redisgraph.so"` |  |
| redis.replica.extraFlags[2] | string | `"THREAD_COUNT"` |  |
| redis.replica.extraFlags[3] | string | `"8"` |  |
| redis.replica.extraFlags[4] | string | `"OMP_THREAD_COUNT"` |  |
| redis.replica.extraFlags[5] | string | `"16"` |  |
| redis.replica.livenessProbe.enabled | bool | `false` |  |
| redis.replica.persistence.size | string | `"15Gi"` |  |
| redis.replica.readinessProbe.enabled | bool | `true` |  |
| redis.replica.readinessProbe.failureThreshold | int | `1` |  |
| redis.replica.readinessProbe.periodSeconds | int | `1` |  |
| redis.replica.readinessProbe.successThreshold | int | `5` |  |
| redis.replica.resources.limits.cpu | string | `"2000m"` |  |
| redis.replica.resources.limits.memory | string | `"15Gi"` |  |
| redis.replica.resources.requests.cpu | string | `"1000m"` |  |
| redis.replica.resources.requests.memory | string | `"12Gi"` |  |
| redis.usePassword | bool | `true` |  |
| replicas | int | `1` | (int) Number of tranql webserver replicas |
| resources | object | `{"limits":{"cpu":"1000m","memory":"5Gi"},"requests":{"cpu":"250m","memory":"2Gi"}}` | Resources for Tranql containers |
| service.type | string | `"ClusterIP"` | (string) Tranql k8s service type |
| tranql_redis_query_timeout | int | `10000` | Tranql query timeout sent to redis in milliseconds |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.6.0](https://github.com/norwoodj/helm-docs/releases/v1.6.0)

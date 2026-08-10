# test-app

![Version: 0.2.8-rc.1](https://img.shields.io/badge/Version-0.2.8--rc.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.3.0-rc](https://img.shields.io/badge/AppVersion-0.3.0--rc-informational?style=flat-square)

A Helm chart to deploy test-app.

## Values

### General

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| commonLabels | object | `{}` | Add labels to all the deployed resources |
| extraObjects | list | `[]` | Add extra specs dynamically to this chart. |
| fullnameOverride | string | `""` | String to fully override the default application name. |
| nameOverride | string | `""` | Provide a name in place of the default application name. |

### Global

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.env | object | `{}` | Map or array of environment variables to inject into all containers (`valueFrom` supported). |
| global.envCm | object | `{}` | Map of environment variables to inject into a configmap loaded by all containers (`valueFrom` not supported). |
| global.envSecret | object | `{}` | Map of environment variables to inject into a secret loaded by all containers (`valueFrom` not supported). |
| global.httpRoute | object | `{}` | Globally shared httproute configuration. |
| global.imageRegistry | string | `""` | Global Docker image registry |
| global.ingress | object | `{}` | Globally shared ingress configuration. |

### Client

#### General

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.affinity | object | `{}` | Affinity used for app pod. |
| client.args | list | `[]` | Client container command args. |
| client.command | list | `[]` | Client container command. |
| client.containerPort | int | `8080` | Client container port number. |
| client.containerPortName | string | `"http"` | Client container port name. |
| client.env | object | `{}` | Map or array of environment variables to inject into the app container (`valueFrom` supported). |
| client.envCm | object | `{}` | Map of environment variables to inject into a configmap loaded by the app container (`valueFrom` not supported). |
| client.envFrom | list | `[]` | Client container env variables loaded from configmap or secret reference. |
| client.envSecret | object | `{}` | Map of environment variables to inject into a secret loaded by the app container (`valueFrom` not supported). |
| client.extraContainers | list | `[]` | Extra containers to add to the app pod as sidecars. |
| client.extraPorts | list | `[]` | Client extra container ports. |
| client.hostAliases | list | `[]` | Host aliases that will be injected at pod-level into /etc/hosts. |
| client.imagePullSecrets | list | `[]` | Image credentials configuration. |
| client.initContainers | list | `[]` | Init containers to add to the app pod. |
| client.nodeSelector | object | `{}` | Default node selector for app. |
| client.podAnnotations | object | `{}` | Annotations for the app deployed pods. |
| client.podLabels | object | `{}` | Labels for the app deployed pods. |
| client.podSecurityContext | object | `{}` | Toggle and define pod-level security context. |
| client.replicaCount | int | `1` | The number of application controller pods to run. |
| client.revisionHistoryLimit | int | `3` | Revision history limit for the app. |
| client.securityContext | object | `{}` | Toggle and define container-level security context. |
| client.statefulset | bool | `false` | Should the app run as a StatefulSet instead of a Deployment. |
| client.tolerations | list | `[]` | Default tolerations for app. |
| client.volumeClaims | list | `[]` | List of volumeClaims to add. |
| client.volumeMounts | list | `[]` | List of mounts to add (normally used with `volumes` or `volumeClaims`). |
| client.volumes | list | `[]` | List of volumes to add. |

#### Autoscaling

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.autoscaling.enabled | bool | `false` | Enable Horizontal Pod Autoscaler for the app. |
| client.autoscaling.maxReplicas | int | `3` | Maximum number of replicas for the app. |
| client.autoscaling.minReplicas | int | `1` | Minimum number of replicas for the app. |
| client.autoscaling.targetCPUUtilizationPercentage | int | `80` | Average CPU utilization percentage for the app. |
| client.autoscaling.targetMemoryUtilizationPercentage | int | `80` | Average memory utilization percentage for the app. |

#### GrpcRoute

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.grpcRoute.annotations | object | `{}` | Additional GRPCRoute annotations. |
| client.grpcRoute.enabled | bool | `false` | Enable a GRPCRoute resource for this service. |
| client.grpcRoute.hostnames | list | `[]` | Hostnames for the GRPCRoute to match. |
| client.grpcRoute.labels | object | `{}` | Additional GRPCRoute labels. |
| client.grpcRoute.parentRefs | list | `[]` | Parent references (Gateways) to attach the GRPCRoute to. |
| client.grpcRoute.rules | list | `[]` | Routing rules for the GRPCRoute. |

#### HttpRoute

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.httpRoute.annotations | object | `{}` | Additional HTTPRoute annotations. |
| client.httpRoute.enabled | bool | `false` | Enable an HTTPRoute resource for this service. |
| client.httpRoute.hostnames | list | `[]` | Hostnames for the HTTPRoute to match. |
| client.httpRoute.labels | object | `{}` | Additional HTTPRoute labels. |
| client.httpRoute.parentRefs | list | `[]` | Parent references (Gateways) to attach the HTTPRoute to. |
| client.httpRoute.rules | list | `[]` | Routing rules for the HTTPRoute. |

#### Image

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the app. |
| client.image.registry | string | `"harbor.sdid.cpin.numerique-interieur.com"` | Registry to use for the app. |
| client.image.repository | string | `"tobi/client"` | Repository to use for the app. |
| client.image.tag | string | `""` | Tag to use for the app. Overrides the image tag whose default is the chart appVersion. |

#### Ingress

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.ingress.annotations | object | `{}` | Additional ingress annotations. |
| client.ingress.className | string | `""` | Defines which ingress controller will implement the resource. |
| client.ingress.enabled | bool | `false` | Whether or not ingress should be enabled. |
| client.ingress.hosts[0].backend.portNumber | string | `nil` | Port used by the backend service linked to the host record (leave null to use the app service port). @schema type:[integer, null] |
| client.ingress.hosts[0].backend.serviceName | string | `""` | Name of the backend service linked to the host record (leave empty to use the app service). |
| client.ingress.hosts[0].name | string | `"domain.local"` | Name of the host record. |
| client.ingress.hosts[0].path | string | `"/"` | Path of the host record to manage routing. |
| client.ingress.hosts[0].pathType | string | `"Prefix"` | Path type of the host record. |
| client.ingress.labels | object | `{}` | Additional ingress labels. |
| client.ingress.tls | list | `[]` | Enable TLS configuration. |

#### Metrics

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.metrics.enabled | bool | `false` | Deploy metrics service. |
| client.metrics.service.annotations | object | `{}` | Metrics service annotations. |
| client.metrics.service.labels | object | `{}` | Metrics service labels. |
| client.metrics.service.port | int | `9000` | Metrics service port. |
| client.metrics.service.targetPort | int | `9000` | Metrics service target port. |
| client.metrics.serviceMonitor.annotations | object | `{}` | Prometheus ServiceMonitor annotations. |
| client.metrics.serviceMonitor.enabled | bool | `false` | Enable a prometheus ServiceMonitor. |
| client.metrics.serviceMonitor.endpoints[0].basicAuth.password | string | `""` | The secret in the service monitor namespace that contains the password for authentication. |
| client.metrics.serviceMonitor.endpoints[0].basicAuth.username | string | `""` | The secret in the service monitor namespace that contains the username for authentication. |
| client.metrics.serviceMonitor.endpoints[0].bearerTokenSecret.key | string | `""` | Secret key to mount to read bearer token for scraping targets. The secret needs to be in the same namespace as the service monitor and accessible by the Prometheus Operator. |
| client.metrics.serviceMonitor.endpoints[0].bearerTokenSecret.name | string | `""` | Secret name to mount to read bearer token for scraping targets. The secret needs to be in the same namespace as the service monitor and accessible by the Prometheus Operator. |
| client.metrics.serviceMonitor.endpoints[0].honorLabels | bool | `false` | When true, honorLabels preserves the metric’s labels when they collide with the target’s labels. |
| client.metrics.serviceMonitor.endpoints[0].interval | string | `"30s"` | Prometheus ServiceMonitor interval. |
| client.metrics.serviceMonitor.endpoints[0].metricRelabelings | list | `[]` | Prometheus MetricRelabelConfigs to apply to samples before ingestion. |
| client.metrics.serviceMonitor.endpoints[0].path | string | `"/metrics"` | Path used by the Prometheus ServiceMonitor to scrape metrics. |
| client.metrics.serviceMonitor.endpoints[0].relabelings | list | `[]` | Prometheus RelabelConfigs to apply to samples before scraping. |
| client.metrics.serviceMonitor.endpoints[0].scheme | string | `""` | Prometheus ServiceMonitor scheme. |
| client.metrics.serviceMonitor.endpoints[0].scrapeTimeout | string | `"10s"` | Prometheus ServiceMonitor scrapeTimeout. If empty, Prometheus uses the global scrape timeout unless it is less than the target's scrape interval value in which the latter is used. |
| client.metrics.serviceMonitor.endpoints[0].selector | object | `{}` | Prometheus ServiceMonitor selector. |
| client.metrics.serviceMonitor.endpoints[0].tlsConfig | object | `{}` | Prometheus ServiceMonitor tlsConfig. |
| client.metrics.serviceMonitor.labels | object | `{}` | Prometheus ServiceMonitor labels. |

#### NetworkPolicy

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.networkPolicy.create | bool | `false` | Create NetworkPolicy object for the app. |
| client.networkPolicy.egress | list | `[]` | Egress rules for the NetworkPolicy object. |
| client.networkPolicy.ingress | list | `[]` | Ingress rules for the NetworkPolicy object. |
| client.networkPolicy.policyTypes | list | `["Ingress"]` | Policy types used in the NetworkPolicy object. |

#### Pdb

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.pdb.annotations | object | `{}` | Annotations to be added to app pdb. |
| client.pdb.enabled | bool | `false` | Deploy a PodDisruptionBudget for the app |
| client.pdb.labels | object | `{}` | Labels to be added to app pdb. |
| client.pdb.maxUnavailable | string | `""` | Number of pods that are unavailable after eviction as number or percentage (eg.: 50%). Has higher precedence over `client.pdb.minAvailable`. |
| client.pdb.minAvailable | string | `""` (defaults to 0 if not specified) | Number of pods that are available after eviction as number or percentage (eg.: 50%). |

#### Probes

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.probes.livenessProbe.failureThreshold | int | `3` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| client.probes.livenessProbe.httpGet.path | string | `"/"` | Client container healthcheck endpoint (livenessProbe is defined using `toYaml` so it is possible to override it completely). |
| client.probes.livenessProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| client.probes.livenessProbe.initialDelaySeconds | int | `30` | Number of seconds after the container has started before probe is initiated. |
| client.probes.livenessProbe.periodSeconds | int | `30` | How often (in seconds) to perform the probe. |
| client.probes.livenessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| client.probes.livenessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |
| client.probes.readinessProbe.failureThreshold | int | `2` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| client.probes.readinessProbe.httpGet.path | string | `"/"` | Client container healthcheck endpoint (readinessProbe is defined using `toYaml` so it is possible to override it completely). |
| client.probes.readinessProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| client.probes.readinessProbe.initialDelaySeconds | int | `10` | Number of seconds after the container has started before probe is initiated. |
| client.probes.readinessProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| client.probes.readinessProbe.successThreshold | int | `2` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| client.probes.readinessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |
| client.probes.startupProbe.failureThreshold | int | `10` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| client.probes.startupProbe.httpGet.path | string | `"/"` | Client container healthcheck endpoint (startupProbe is defined using `toYaml` so it is possible to override it completely). |
| client.probes.startupProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| client.probes.startupProbe.initialDelaySeconds | int | `0` | Number of seconds after the container has started before probe is initiated. |
| client.probes.startupProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| client.probes.startupProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| client.probes.startupProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |

#### Resources

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.resources.limits.cpu | string | `"100m"` | CPU limit for the app. |
| client.resources.limits.memory | string | `"256Mi"` | Memory limit for the app. |
| client.resources.requests.cpu | string | `"100m"` | CPU request for the app. |
| client.resources.requests.memory | string | `"256Mi"` | Memory request for the app. |

#### Service

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.service.extraPorts | list | `[]` | Extra service ports. |
| client.service.nodePort | int | `31000` | Port used when type is `NodePort` to expose the service on the given node port. |
| client.service.port | int | `80` | Port used by the service. |
| client.service.portName | string | `"http"` | Port name used by the service. |
| client.service.protocol | string | `"TCP"` | Protocol used by the service. |
| client.service.type | string | `"ClusterIP"` | Type of service to create for the app. |

#### ServiceAccount

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.serviceAccount.annotations | object | `{}` | Annotations applied to created service account. |
| client.serviceAccount.automountServiceAccountToken | bool | `false` | Should the service account access token be automount in the pod. |
| client.serviceAccount.clusterRole.create | bool | `false` | Should the clusterRole be created. |
| client.serviceAccount.clusterRole.rules | list | `[]` | ClusterRole rules associated with the service account. |
| client.serviceAccount.create | bool | `false` | Create a service account. |
| client.serviceAccount.enabled | bool | `false` | Enable the service account. |
| client.serviceAccount.name | string | `""` | Service account name. |
| client.serviceAccount.role.create | bool | `false` | Should the role be created. |
| client.serviceAccount.role.rules | list | `[]` | Role rules associated with the service account. |

#### Strategy

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| client.strategy.rollingUpdate.maxSurge | int | `1` | The maximum number of pods that can be scheduled above the desired number of pods. |
| client.strategy.rollingUpdate.maxUnavailable | int | `1` | The maximum number of pods that can be unavailable during the update process. |
| client.strategy.type | string | `"RollingUpdate"` | Strategy type used to replace old Pods by new ones, can be `Recreate` or `RollingUpdate`. |

### Gateway

#### General

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| gateway.addresses | list | `[]` | Gateway addresses configuration. |
| gateway.annotations | object | `{}` | Additional gateway annotations. |
| gateway.className | string | `""` | GatewayClass name. Required when creating a Gateway. |
| gateway.create | bool | `false` | Create a Gateway resource. Usually, you reference an existing Gateway managed by the infrastructure team. |
| gateway.labels | object | `{}` | Additional gateway labels. |
| gateway.listeners | list | `[]` | Gateway listeners configuration. |
| gateway.name | string | `""` | Name of the Gateway resource. If not set, uses the release fullname. |

### Server

#### General

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.affinity | object | `{}` | Affinity used for app pod. |
| server.args | list | `[]` | Server container command args. |
| server.command | list | `[]` | Server container command. |
| server.containerPort | int | `8080` | Server container port number. |
| server.containerPortName | string | `"http"` | Server container port name. |
| server.env | object | `{}` | Map or array of environment variables to inject into the app container (`valueFrom` supported). |
| server.envCm | object | `{}` | Map of environment variables to inject into a configmap loaded by the app container (`valueFrom` not supported). |
| server.envFrom | list | `[]` | Server container env variables loaded from configmap or secret reference. |
| server.envSecret | object | `{}` | Map of environment variables to inject into a secret loaded by the app container (`valueFrom` not supported). |
| server.extraContainers | list | `[]` | Extra containers to add to the app pod as sidecars. |
| server.extraPorts | list | `[]` | Server extra container ports. |
| server.hostAliases | list | `[]` | Host aliases that will be injected at pod-level into /etc/hosts. |
| server.imagePullSecrets | list | `[]` | Image credentials configuration. |
| server.initContainers | list | `[]` | Init containers to add to the app pod. |
| server.nodeSelector | object | `{}` | Default node selector for app. |
| server.podAnnotations | object | `{}` | Annotations for the app deployed pods. |
| server.podLabels | object | `{}` | Labels for the app deployed pods. |
| server.podSecurityContext | object | `{}` | Toggle and define pod-level security context. |
| server.replicaCount | int | `1` | The number of application controller pods to run. |
| server.revisionHistoryLimit | int | `3` | Revision history limit for the app. |
| server.securityContext | object | `{}` | Toggle and define container-level security context. |
| server.statefulset | bool | `false` | Should the app run as a StatefulSet instead of a Deployment. |
| server.tolerations | list | `[]` | Default tolerations for app. |
| server.volumeClaims | list | `[]` | List of volumeClaims to add. |
| server.volumeMounts | list | `[]` | List of mounts to add (normally used with `volumes` or `volumeClaims`). |
| server.volumes | list | `[]` | List of volumes to add. |

#### Autoscaling

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.autoscaling.enabled | bool | `false` | Enable Horizontal Pod Autoscaler for the app. |
| server.autoscaling.maxReplicas | int | `3` | Maximum number of replicas for the app. |
| server.autoscaling.minReplicas | int | `1` | Minimum number of replicas for the app. |
| server.autoscaling.targetCPUUtilizationPercentage | int | `80` | Average CPU utilization percentage for the app. |
| server.autoscaling.targetMemoryUtilizationPercentage | int | `80` | Average memory utilization percentage for the app. |

#### GrpcRoute

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.grpcRoute.annotations | object | `{}` | Additional GRPCRoute annotations. |
| server.grpcRoute.enabled | bool | `false` | Enable a GRPCRoute resource for this service. |
| server.grpcRoute.hostnames | list | `[]` | Hostnames for the GRPCRoute to match. |
| server.grpcRoute.labels | object | `{}` | Additional GRPCRoute labels. |
| server.grpcRoute.parentRefs | list | `[]` | Parent references (Gateways) to attach the GRPCRoute to. |
| server.grpcRoute.rules | list | `[]` | Routing rules for the GRPCRoute. |

#### HttpRoute

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.httpRoute.annotations | object | `{}` | Additional HTTPRoute annotations. |
| server.httpRoute.enabled | bool | `false` | Enable an HTTPRoute resource for this service. |
| server.httpRoute.hostnames | list | `[]` | Hostnames for the HTTPRoute to match. |
| server.httpRoute.labels | object | `{}` | Additional HTTPRoute labels. |
| server.httpRoute.parentRefs | list | `[]` | Parent references (Gateways) to attach the HTTPRoute to. |
| server.httpRoute.rules | list | `[]` | Routing rules for the HTTPRoute. |

#### Image

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the app. |
| server.image.registry | string | `"harbor.sdid.cpin.numerique-interieur.com"` | Registry to use for the app. |
| server.image.repository | string | `"tobi/server"` | Repository to use for the app. |
| server.image.tag | string | `""` | Tag to use for the app. Overrides the image tag whose default is the chart appVersion. |

#### Ingress

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.ingress.annotations | object | `{}` | Additional ingress annotations. |
| server.ingress.className | string | `""` | Defines which ingress controller will implement the resource. |
| server.ingress.enabled | bool | `false` | Whether or not ingress should be enabled. |
| server.ingress.hosts[0].backend.portNumber | string | `nil` | Port used by the backend service linked to the host record (leave null to use the app service port). @schema type:[integer, null] |
| server.ingress.hosts[0].backend.serviceName | string | `""` | Name of the backend service linked to the host record (leave empty to use the app service). |
| server.ingress.hosts[0].name | string | `"domain.local"` | Name of the host record. |
| server.ingress.hosts[0].path | string | `"/"` | Path of the host record to manage routing. |
| server.ingress.hosts[0].pathType | string | `"Prefix"` | Path type of the host record. |
| server.ingress.labels | object | `{}` | Additional ingress labels. |
| server.ingress.tls | list | `[]` | Enable TLS configuration. |

#### Metrics

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.metrics.enabled | bool | `false` | Deploy metrics service. |
| server.metrics.service.annotations | object | `{}` | Metrics service annotations. |
| server.metrics.service.labels | object | `{}` | Metrics service labels. |
| server.metrics.service.port | int | `9000` | Metrics service port. |
| server.metrics.service.targetPort | int | `9000` | Metrics service target port. |
| server.metrics.serviceMonitor.annotations | object | `{}` | Prometheus ServiceMonitor annotations. |
| server.metrics.serviceMonitor.enabled | bool | `false` | Enable a prometheus ServiceMonitor. |
| server.metrics.serviceMonitor.endpoints[0].basicAuth.password | string | `""` | The secret in the service monitor namespace that contains the password for authentication. |
| server.metrics.serviceMonitor.endpoints[0].basicAuth.username | string | `""` | The secret in the service monitor namespace that contains the username for authentication. |
| server.metrics.serviceMonitor.endpoints[0].bearerTokenSecret.key | string | `""` | Secret key to mount to read bearer token for scraping targets. The secret needs to be in the same namespace as the service monitor and accessible by the Prometheus Operator. |
| server.metrics.serviceMonitor.endpoints[0].bearerTokenSecret.name | string | `""` | Secret name to mount to read bearer token for scraping targets. The secret needs to be in the same namespace as the service monitor and accessible by the Prometheus Operator. |
| server.metrics.serviceMonitor.endpoints[0].honorLabels | bool | `false` | When true, honorLabels preserves the metric’s labels when they collide with the target’s labels. |
| server.metrics.serviceMonitor.endpoints[0].interval | string | `"30s"` | Prometheus ServiceMonitor interval. |
| server.metrics.serviceMonitor.endpoints[0].metricRelabelings | list | `[]` | Prometheus MetricRelabelConfigs to apply to samples before ingestion. |
| server.metrics.serviceMonitor.endpoints[0].path | string | `"/metrics"` | Path used by the Prometheus ServiceMonitor to scrape metrics. |
| server.metrics.serviceMonitor.endpoints[0].relabelings | list | `[]` | Prometheus RelabelConfigs to apply to samples before scraping. |
| server.metrics.serviceMonitor.endpoints[0].scheme | string | `""` | Prometheus ServiceMonitor scheme. |
| server.metrics.serviceMonitor.endpoints[0].scrapeTimeout | string | `"10s"` | Prometheus ServiceMonitor scrapeTimeout. If empty, Prometheus uses the global scrape timeout unless it is less than the target's scrape interval value in which the latter is used. |
| server.metrics.serviceMonitor.endpoints[0].selector | object | `{}` | Prometheus ServiceMonitor selector. |
| server.metrics.serviceMonitor.endpoints[0].tlsConfig | object | `{}` | Prometheus ServiceMonitor tlsConfig. |
| server.metrics.serviceMonitor.labels | object | `{}` | Prometheus ServiceMonitor labels. |

#### NetworkPolicy

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.networkPolicy.create | bool | `false` | Create NetworkPolicy object for the app. |
| server.networkPolicy.egress | list | `[]` | Egress rules for the NetworkPolicy object. |
| server.networkPolicy.ingress | list | `[]` | Ingress rules for the NetworkPolicy object. |
| server.networkPolicy.policyTypes | list | `["Ingress"]` | Policy types used in the NetworkPolicy object. |

#### Pdb

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.pdb.annotations | object | `{}` | Annotations to be added to app pdb. |
| server.pdb.enabled | bool | `false` | Deploy a PodDisruptionBudget for the app |
| server.pdb.labels | object | `{}` | Labels to be added to app pdb. |
| server.pdb.maxUnavailable | string | `""` | Number of pods that are unavailable after eviction as number or percentage (eg.: 50%). Has higher precedence over `server.pdb.minAvailable`. |
| server.pdb.minAvailable | string | `""` (defaults to 0 if not specified) | Number of pods that are available after eviction as number or percentage (eg.: 50%). |

#### Probes

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.probes.livenessProbe.failureThreshold | int | `3` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| server.probes.livenessProbe.httpGet.path | string | `"/"` | Server container healthcheck endpoint (livenessProbe is defined using `toYaml` so it is possible to override it completely). |
| server.probes.livenessProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| server.probes.livenessProbe.initialDelaySeconds | int | `30` | Number of seconds after the container has started before probe is initiated. |
| server.probes.livenessProbe.periodSeconds | int | `30` | How often (in seconds) to perform the probe. |
| server.probes.livenessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| server.probes.livenessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |
| server.probes.readinessProbe.failureThreshold | int | `2` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| server.probes.readinessProbe.httpGet.path | string | `"/"` | Server container healthcheck endpoint (readinessProbe is defined using `toYaml` so it is possible to override it completely). |
| server.probes.readinessProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| server.probes.readinessProbe.initialDelaySeconds | int | `10` | Number of seconds after the container has started before probe is initiated. |
| server.probes.readinessProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| server.probes.readinessProbe.successThreshold | int | `2` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| server.probes.readinessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |
| server.probes.startupProbe.failureThreshold | int | `10` | Minimum consecutive failures for the probe to be considered failed after having succeeded. |
| server.probes.startupProbe.httpGet.path | string | `"/"` | Server container healthcheck endpoint (startupProbe is defined using `toYaml` so it is possible to override it completely). |
| server.probes.startupProbe.httpGet.port | int | `8080` | Port to use for healthcheck (defaults to container port). |
| server.probes.startupProbe.initialDelaySeconds | int | `0` | Number of seconds after the container has started before probe is initiated. |
| server.probes.startupProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| server.probes.startupProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| server.probes.startupProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out. |

#### Resources

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.resources.limits.cpu | string | `"100m"` | CPU limit for the app. |
| server.resources.limits.memory | string | `"256Mi"` | Memory limit for the app. |
| server.resources.requests.cpu | string | `"100m"` | CPU request for the app. |
| server.resources.requests.memory | string | `"256Mi"` | Memory request for the app. |

#### Service

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.service.extraPorts | list | `[]` | Extra service ports. |
| server.service.nodePort | int | `31000` | Port used when type is `NodePort` to expose the service on the given node port. |
| server.service.port | int | `80` | Port used by the service. |
| server.service.portName | string | `"http"` | Port name used by the service. |
| server.service.protocol | string | `"TCP"` | Protocol used by the service. |
| server.service.type | string | `"ClusterIP"` | Type of service to create for the app. |

#### ServiceAccount

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.serviceAccount.annotations | object | `{}` | Annotations applied to created service account. |
| server.serviceAccount.automountServiceAccountToken | bool | `false` | Should the service account access token be automount in the pod. |
| server.serviceAccount.clusterRole.create | bool | `false` | Should the clusterRole be created. |
| server.serviceAccount.clusterRole.rules | list | `[]` | ClusterRole rules associated with the service account. |
| server.serviceAccount.create | bool | `false` | Create a service account. |
| server.serviceAccount.enabled | bool | `false` | Enable the service account. |
| server.serviceAccount.name | string | `""` | Service account name. |
| server.serviceAccount.role.create | bool | `false` | Should the role be created. |
| server.serviceAccount.role.rules | list | `[]` | Role rules associated with the service account. |

#### Strategy

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| server.strategy.rollingUpdate.maxSurge | int | `1` | The maximum number of pods that can be scheduled above the desired number of pods. |
| server.strategy.rollingUpdate.maxUnavailable | int | `1` | The maximum number of pods that can be unavailable during the update process. |
| server.strategy.type | string | `"RollingUpdate"` | Strategy type used to replace old Pods by new ones, can be `Recreate` or `RollingUpdate`. |

## Sources

**Source code:**

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)

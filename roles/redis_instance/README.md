# redis_instance

Role to deploy Redis instances on a Kubernetes cluster.
It supports standalone, replication, cluster and sentinel modes
using the OpsTree Redis Operator helm charts.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [redis_instance_acl_secret_name](#redis_instance_acl_secret_name)
  - [redis_instance_affinity](#redis_instance_affinity)
  - [redis_instance_annotations](#redis_instance_annotations)
  - [redis_instance_chart_map](#redis_instance_chart_map)
  - [redis_instance_cluster_follower_replicas](#redis_instance_cluster_follower_replicas)
  - [redis_instance_cluster_helm_version](#redis_instance_cluster_helm_version)
  - [redis_instance_cluster_leader_replicas](#redis_instance_cluster_leader_replicas)
  - [redis_instance_cluster_persistence_enabled](#redis_instance_cluster_persistence_enabled)
  - [redis_instance_cluster_size](#redis_instance_cluster_size)
  - [redis_instance_cluster_version](#redis_instance_cluster_version)
  - [redis_instance_enabled](#redis_instance_enabled)
  - [redis_instance_env](#redis_instance_env)
  - [redis_instance_exporter_enabled](#redis_instance_exporter_enabled)
  - [redis_instance_exporter_image](#redis_instance_exporter_image)
  - [redis_instance_exporter_resources](#redis_instance_exporter_resources)
  - [redis_instance_exporter_tag](#redis_instance_exporter_tag)
  - [redis_instance_external_config_data](#redis_instance_external_config_data)
  - [redis_instance_external_config_enabled](#redis_instance_external_config_enabled)
  - [redis_instance_external_service_enabled](#redis_instance_external_service_enabled)
  - [redis_instance_external_service_port](#redis_instance_external_service_port)
  - [redis_instance_external_service_type](#redis_instance_external_service_type)
  - [redis_instance_helm_repo_name](#redis_instance_helm_repo_name)
  - [redis_instance_helm_repo_url](#redis_instance_helm_repo_url)
  - [redis_instance_image](#redis_instance_image)
  - [redis_instance_image_pull_policy](#redis_instance_image_pull_policy)
  - [redis_instance_init_container_enabled](#redis_instance_init_container_enabled)
  - [redis_instance_labels](#redis_instance_labels)
  - [redis_instance_mode](#redis_instance_mode)
  - [redis_instance_name](#redis_instance_name)
  - [redis_instance_namespace](#redis_instance_namespace)
  - [redis_instance_node_selector](#redis_instance_node_selector)
  - [redis_instance_pdb_enabled](#redis_instance_pdb_enabled)
  - [redis_instance_pdb_min_available](#redis_instance_pdb_min_available)
  - [redis_instance_pod_security_context](#redis_instance_pod_security_context)
  - [redis_instance_priority_class](#redis_instance_priority_class)
  - [redis_instance_replication_helm_version](#redis_instance_replication_helm_version)
  - [redis_instance_resources](#redis_instance_resources)
  - [redis_instance_secret_key](#redis_instance_secret_key)
  - [redis_instance_secret_name](#redis_instance_secret_name)
  - [redis_instance_security_context](#redis_instance_security_context)
  - [redis_instance_sentinel_down_after_milliseconds](#redis_instance_sentinel_down_after_milliseconds)
  - [redis_instance_sentinel_failover_timeout](#redis_instance_sentinel_failover_timeout)
  - [redis_instance_sentinel_helm_version](#redis_instance_sentinel_helm_version)
  - [redis_instance_sentinel_master_group_name](#redis_instance_sentinel_master_group_name)
  - [redis_instance_sentinel_parallel_syncs](#redis_instance_sentinel_parallel_syncs)
  - [redis_instance_sentinel_quorum](#redis_instance_sentinel_quorum)
  - [redis_instance_sentinel_replication_name](#redis_instance_sentinel_replication_name)
  - [redis_instance_service_account_name](#redis_instance_service_account_name)
  - [redis_instance_service_monitor_enabled](#redis_instance_service_monitor_enabled)
  - [redis_instance_service_monitor_interval](#redis_instance_service_monitor_interval)
  - [redis_instance_service_monitor_scrape_timeout](#redis_instance_service_monitor_scrape_timeout)
  - [redis_instance_service_type](#redis_instance_service_type)
  - [redis_instance_sidecars](#redis_instance_sidecars)
  - [redis_instance_standalone_helm_version](#redis_instance_standalone_helm_version)
  - [redis_instance_storage_access_modes](#redis_instance_storage_access_modes)
  - [redis_instance_storage_class](#redis_instance_storage_class)
  - [redis_instance_storage_size](#redis_instance_storage_size)
  - [redis_instance_tag](#redis_instance_tag)
  - [redis_instance_tls_secret_name](#redis_instance_tls_secret_name)
  - [redis_instance_tolerations](#redis_instance_tolerations)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### redis_instance_acl_secret_name

Secret name for ACL configuration

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_acl_secret_name: ''
```

### redis_instance_affinity

Affinity for the pods

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_affinity: {}
```

### redis_instance_annotations

Additional annotations

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_annotations: {}
```

### redis_instance_chart_map

#### Default value

```YAML
redis_instance_chart_map:
  standalone:
    chart_ref: '{{ redis_instance_helm_repo_name }}/redis'
    chart_version: '{{ redis_instance_standalone_helm_version }}'
    template: redis_instance_standalone_helm_values.yml.j2
  replication:
    chart_ref: '{{ redis_instance_helm_repo_name }}/redis-replication'
    chart_version: '{{ redis_instance_replication_helm_version }}'
    template: redis_instance_replication_helm_values.yml.j2
  cluster:
    chart_ref: '{{ redis_instance_helm_repo_name }}/redis-cluster'
    chart_version: '{{ redis_instance_cluster_helm_version }}'
    template: redis_instance_cluster_helm_values.yml.j2
  sentinel:
    chart_ref: '{{ redis_instance_helm_repo_name }}/redis-sentinel'
    chart_version: '{{ redis_instance_sentinel_helm_version }}'
    template: redis_instance_sentinel_helm_values.yml.j2
```

### redis_instance_cluster_follower_replicas

Number of follower replicas (cluster mode only)

**_Type:_** int<br />

#### Default value

```YAML
redis_instance_cluster_follower_replicas: 3
```

### redis_instance_cluster_helm_version

Helm chart version for cluster mode

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_cluster_helm_version: 0.17.4
```

### redis_instance_cluster_leader_replicas

Number of leader replicas (cluster mode only)

**_Type:_** int<br />

#### Default value

```YAML
redis_instance_cluster_leader_replicas: 3
```

### redis_instance_cluster_persistence_enabled

Enable persistence (cluster mode only)

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_cluster_persistence_enabled: true
```

### redis_instance_cluster_size

Number of replicas (used in replication, cluster, sentinel modes)

**_Type:_** int<br />

#### Default value

```YAML
redis_instance_cluster_size: 3
```

### redis_instance_cluster_version

Redis cluster version (cluster mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_cluster_version: v7
```

### redis_instance_enabled

Should Redis instance helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_enabled: true
```

### redis_instance_env

Additional environment variables

**_Type:_** list<br />

#### Default value

```YAML
redis_instance_env: []
```

### redis_instance_exporter_enabled

Enable Redis exporter sidecar

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_exporter_enabled: false
```

### redis_instance_exporter_image

Redis exporter image

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_exporter_image: quay.io/opstree/redis-exporter
```

### redis_instance_exporter_resources

Redis exporter resources

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_exporter_resources: {}
```

### redis_instance_exporter_tag

Redis exporter image tag

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_exporter_tag: v1.44.0
```

### redis_instance_external_config_data

External Redis configuration data

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_external_config_data: ''
```

### redis_instance_external_config_enabled

Enable external Redis configuration

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_external_config_enabled: false
```

### redis_instance_external_service_enabled

Enable external service

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_external_service_enabled: false
```

### redis_instance_external_service_port

Port for external service

**_Type:_** int<br />

#### Default value

```YAML
redis_instance_external_service_port: 6379
```

### redis_instance_external_service_type

Service type for external service

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_external_service_type: NodePort
```

### redis_instance_helm_repo_name

#### Default value

```YAML
redis_instance_helm_repo_name: ot-helm
```

### redis_instance_helm_repo_url

#### Default value

```YAML
redis_instance_helm_repo_url: https://ot-container-kit.github.io/helm-charts/
```

### redis_instance_image

Redis image repository

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_image: quay.io/opstree/redis
```

### redis_instance_image_pull_policy

Image pull policy

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_image_pull_policy: IfNotPresent
```

### redis_instance_init_container_enabled

Enable init container

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_init_container_enabled: false
```

### redis_instance_labels

Additional labels

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_labels: {}
```

### redis_instance_mode

Redis deployment mode. Must be one of: standalone, replication, cluster, sentinel

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_mode: standalone
```

### redis_instance_name

Redis instance helm release name

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_name: redis
```

### redis_instance_namespace

K8s namespace to deploy Redis instance

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_namespace: redis
```

### redis_instance_node_selector

Node selector for the pods

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_node_selector: {}
```

### redis_instance_pdb_enabled

Enable PodDisruptionBudget (replication and sentinel modes)

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_pdb_enabled: false
```

### redis_instance_pdb_min_available

Minimum available pods for PDB

**_Type:_** int<br />

#### Default value

```YAML
redis_instance_pdb_min_available: 1
```

### redis_instance_pod_security_context

Pod security context

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_pod_security_context:
  runAsUser: 1000
  fsGroup: 1000
```

### redis_instance_priority_class

PriorityClass for the pods

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_priority_class: ''
```

### redis_instance_replication_helm_version

Helm chart version for replication mode

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_replication_helm_version: 0.17.0
```

### redis_instance_resources

Resource requests and limits

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_resources: {}
```

### redis_instance_secret_key

Secret key for Redis password

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_secret_key: ''
```

### redis_instance_secret_name

Secret name for Redis password

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_secret_name: ''
```

### redis_instance_security_context

Container security context

**_Type:_** dict<br />

#### Default value

```YAML
redis_instance_security_context: {}
```

### redis_instance_sentinel_down_after_milliseconds

Time before master is considered down in ms (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_down_after_milliseconds: ''
```

### redis_instance_sentinel_failover_timeout

Failover timeout in ms (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_failover_timeout: ''
```

### redis_instance_sentinel_helm_version

Helm chart version for sentinel mode

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_helm_version: 0.16.12
```

### redis_instance_sentinel_master_group_name

Sentinel master group name (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_master_group_name: ''
```

### redis_instance_sentinel_parallel_syncs

Number of replicas to reconfigure in parallel (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_parallel_syncs: ''
```

### redis_instance_sentinel_quorum

Sentinel quorum (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_quorum: ''
```

### redis_instance_sentinel_replication_name

Name of the Redis replication to monitor (sentinel mode only)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_sentinel_replication_name: redis-replication
```

### redis_instance_service_account_name

Service account name

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_service_account_name: ''
```

### redis_instance_service_monitor_enabled

Enable ServiceMonitor

**_Type:_** boolean<br />

#### Default value

```YAML
redis_instance_service_monitor_enabled: false
```

### redis_instance_service_monitor_interval

Scrape interval for ServiceMonitor

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_service_monitor_interval: 30s
```

### redis_instance_service_monitor_scrape_timeout

Scrape timeout for ServiceMonitor

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_service_monitor_scrape_timeout: 10s
```

### redis_instance_service_type

Kubernetes service type (ClusterIP, NodePort, LoadBalancer)

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_service_type: ClusterIP
```

### redis_instance_sidecars

Additional sidecar containers

**_Type:_** list<br />

#### Default value

```YAML
redis_instance_sidecars: []
```

### redis_instance_standalone_helm_version

Helm chart version for standalone mode

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_standalone_helm_version: 0.16.9
```

### redis_instance_storage_access_modes

Access modes for persistent volume

**_Type:_** list<br />

#### Default value

```YAML
redis_instance_storage_access_modes:
  - ReadWriteOnce
```

### redis_instance_storage_class

Storage class for persistent volume

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_storage_class: ''
```

### redis_instance_storage_size

Storage size for persistent volume

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_storage_size: 1Gi
```

### redis_instance_tag

Redis image tag

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_tag: v7.0.15
```

### redis_instance_tls_secret_name

Secret name for TLS certificates

**_Type:_** string<br />

#### Default value

```YAML
redis_instance_tls_secret_name: ''
```

### redis_instance_tolerations

Tolerations for the pods

**_Type:_** list<br />

#### Default value

```YAML
redis_instance_tolerations: []
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

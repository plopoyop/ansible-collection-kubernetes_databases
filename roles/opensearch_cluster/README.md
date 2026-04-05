# opensearch_cluster

Role to deploy OpenSearch instances on a Kubernetes cluster.
It deploys OpenSearch clusters via the opensearch-cluster helm chart using the OpenSearch Operator.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [opensearch_cluster_enabled](#opensearch_cluster_enabled)
  - [opensearch_cluster_helm_chart_ref](#opensearch_cluster_helm_chart_ref)
  - [opensearch_cluster_helm_repo_name](#opensearch_cluster_helm_repo_name)
  - [opensearch_cluster_helm_repo_url](#opensearch_cluster_helm_repo_url)
  - [opensearch_cluster_helm_version](#opensearch_cluster_helm_version)
  - [opensearch_cluster_name](#opensearch_cluster_name)
  - [opensearch_cluster_namespace](#opensearch_cluster_namespace)
  - [opensearch_cluster_values_override](#opensearch_cluster_values_override)
  - [opensearch_default_cluster](#opensearch_default_cluster)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### opensearch_cluster_enabled

Should OpenSearch instance helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_cluster_enabled: true
```

### opensearch_cluster_helm_chart_ref

#### Default value

```YAML
opensearch_cluster_helm_chart_ref: '{{ opensearch_cluster_helm_repo_name }}/opensearch-cluster'
```

### opensearch_cluster_helm_repo_name

#### Default value

```YAML
opensearch_cluster_helm_repo_name: opensearch-operator
```

### opensearch_cluster_helm_repo_url

#### Default value

```YAML
opensearch_cluster_helm_repo_url: 
  https://opensearch-project.github.io/opensearch-k8s-operator/
```

### opensearch_cluster_helm_version

OpenSearch cluster helm chart version

**_Type:_** string<br />

#### Default value

```YAML
opensearch_cluster_helm_version: 3.2.2
```

### opensearch_cluster_name

OpenSearch instance helm release name

**_Type:_** string<br />

#### Default value

```YAML
opensearch_cluster_name: opensearch-cluster
```

### opensearch_cluster_namespace

K8s namespace to deploy OpenSearch instance

**_Type:_** string<br />

#### Default value

```YAML
opensearch_cluster_namespace: opensearch
```

### opensearch_cluster_values_override

Overrides for default values

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_cluster_values_override: {}
```

#### Example usage

```YAML
 opensearch_cluster_values_override:
   version: "2.16.0"
   dashboards_version: "2.16.0"
   dashboards_enabled: false
   node_pools:
     - component: "masters"
       disk_size: "50Gi"
       replicas: 3
       roles:
         - "master"
       resources:
         requests:
           memory: "4Gi"
           cpu: "1000m"
         limits:
           memory: "4Gi"
           cpu: "1000m"
     - component: "data"
       disk_size: "100Gi"
       replicas: 3
       roles:
         - "data"
       resources:
         requests:
           memory: "8Gi"
           cpu: "2000m"
         limits:
           memory: "8Gi"
           cpu: "2000m"
```

### opensearch_default_cluster

Default values for helm chart deployment

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_default_cluster:
  name: '{{ opensearch_cluster_name }}'
  namespace: '{{ opensearch_cluster_namespace }}'
  version: 2.19.0
  image: docker.io/opensearchproject/opensearch
  image_pull_policy: IfNotPresent
  http_port: 9200
  set_vm_max_map_count: true
  service_type: ClusterIP
  additional_config: {}
  node_pools:
    - component: masters
      disk_size: 30Gi
      replicas: 3
      roles:
        - master
        - data
      resources:
        requests:
          memory: 2Gi
          cpu: 500m
        limits:
          memory: 2Gi
          cpu: 500m
  dashboards_enabled: true
  dashboards_version: 2.19.0
  dashboards_image: docker.io/opensearchproject/opensearch-dashboards
  dashboards_replicas: 1
  dashboards_resources: {}
  dashboards_service_type: ClusterIP
  tls_http_generate: true
  tls_transport_generate: true
  tls_transport_per_node: true
  admin_credentials_secret: {}
  security_config_secret: {}
  monitoring_enabled: false
  smart_scaler: true
  init_helper_image: docker.io/busybox
  init_helper_version: '1.36'
  opensearch_ingress_enabled: false
  dashboards_ingress_enabled: false
  roles: []
  users: []
  users_role_binding: []
  tenants: []
  action_groups: []
  component_templates: []
  index_templates: []
  ism_policies: []
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

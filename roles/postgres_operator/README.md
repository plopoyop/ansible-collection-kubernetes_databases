# postgres_operator

Role to install the Zalando Postgres Operator on a Kubernetes cluster.
It installs the operator via its helm chart to manage PostgreSQL clusters.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [postgres_operator_additional_helm_values](#postgres_operator_additional_helm_values)
  - [postgres_operator_cluster_domain](#postgres_operator_cluster_domain)
  - [postgres_operator_cpu_limit](#postgres_operator_cpu_limit)
  - [postgres_operator_cpu_request](#postgres_operator_cpu_request)
  - [postgres_operator_deployment_name](#postgres_operator_deployment_name)
  - [postgres_operator_docker_image](#postgres_operator_docker_image)
  - [postgres_operator_enable_crd_registration](#postgres_operator_enable_crd_registration)
  - [postgres_operator_enable_pod_disruption_budget](#postgres_operator_enable_pod_disruption_budget)
  - [postgres_operator_enable_pvc_deletion](#postgres_operator_enable_pvc_deletion)
  - [postgres_operator_enabled](#postgres_operator_enabled)
  - [postgres_operator_extra_envs](#postgres_operator_extra_envs)
  - [postgres_operator_helm_chart_ref](#postgres_operator_helm_chart_ref)
  - [postgres_operator_helm_chart_version](#postgres_operator_helm_chart_version)
  - [postgres_operator_helm_repo_name](#postgres_operator_helm_repo_name)
  - [postgres_operator_helm_repo_url](#postgres_operator_helm_repo_url)
  - [postgres_operator_memory_limit](#postgres_operator_memory_limit)
  - [postgres_operator_memory_request](#postgres_operator_memory_request)
  - [postgres_operator_namespace](#postgres_operator_namespace)
  - [postgres_operator_pod_security_context](#postgres_operator_pod_security_context)
  - [postgres_operator_priority_class](#postgres_operator_priority_class)
  - [postgres_operator_ui_additional_helm_values](#postgres_operator_ui_additional_helm_values)
  - [postgres_operator_ui_cpu_limit](#postgres_operator_ui_cpu_limit)
  - [postgres_operator_ui_cpu_request](#postgres_operator_ui_cpu_request)
  - [postgres_operator_ui_deployment_name](#postgres_operator_ui_deployment_name)
  - [postgres_operator_ui_enabled](#postgres_operator_ui_enabled)
  - [postgres_operator_ui_extra_envs](#postgres_operator_ui_extra_envs)
  - [postgres_operator_ui_helm_chart_ref](#postgres_operator_ui_helm_chart_ref)
  - [postgres_operator_ui_helm_chart_version](#postgres_operator_ui_helm_chart_version)
  - [postgres_operator_ui_helm_repo_name](#postgres_operator_ui_helm_repo_name)
  - [postgres_operator_ui_helm_repo_url](#postgres_operator_ui_helm_repo_url)
  - [postgres_operator_ui_ingress_annotations](#postgres_operator_ui_ingress_annotations)
  - [postgres_operator_ui_ingress_class_name](#postgres_operator_ui_ingress_class_name)
  - [postgres_operator_ui_ingress_enabled](#postgres_operator_ui_ingress_enabled)
  - [postgres_operator_ui_ingress_hosts](#postgres_operator_ui_ingress_hosts)
  - [postgres_operator_ui_ingress_tls](#postgres_operator_ui_ingress_tls)
  - [postgres_operator_ui_memory_limit](#postgres_operator_ui_memory_limit)
  - [postgres_operator_ui_memory_request](#postgres_operator_ui_memory_request)
  - [postgres_operator_ui_resources_visible](#postgres_operator_ui_resources_visible)
  - [postgres_operator_ui_target_namespace](#postgres_operator_ui_target_namespace)
  - [postgres_operator_ui_teams](#postgres_operator_ui_teams)
  - [postgres_operator_watched_namespace](#postgres_operator_watched_namespace)
  - [postgres_operator_workers](#postgres_operator_workers)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### postgres_operator_additional_helm_values

Additional Helm chart values to merge with the generated values.
Use this to configure any chart option not exposed as a dedicated variable.
ref: https://github.com/zalando/postgres-operator/blob/master/charts/postgres-operator/values.yaml

**_Type:_** dict<br />

#### Default value

```YAML
postgres_operator_additional_helm_values: {}
```

### postgres_operator_cluster_domain

Kubernetes cluster domain

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_cluster_domain: cluster.local
```

### postgres_operator_cpu_limit

CPU limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_cpu_limit: 500m
```

### postgres_operator_cpu_request

CPU request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_cpu_request: 100m
```

### postgres_operator_deployment_name

Deployment name for postgres operator chart

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_deployment_name: postgres-operator
```

### postgres_operator_docker_image

Spilo docker image used for PostgreSQL instances

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_docker_image: ghcr.io/zalando/spilo-18:4.1-p1
```

### postgres_operator_enable_crd_registration

Enable automatic CRD registration by the operator

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_enable_crd_registration: true
```

### postgres_operator_enable_pod_disruption_budget

Enable pod disruption budgets for PostgreSQL clusters

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_enable_pod_disruption_budget: true
```

### postgres_operator_enable_pvc_deletion

Enable deletion of persistent volume claims when clusters are deleted

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_enable_pvc_deletion: true
```

### postgres_operator_enabled

Should Zalando Postgres Operator helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_enabled: true
```

### postgres_operator_extra_envs

Additional environment variables for the operator pod

**_Type:_** list<br />

#### Default value

```YAML
postgres_operator_extra_envs: []
```

#### Example usage

```YAML
 postgres_operator_extra_envs:
  - name: MY_ENV_VAR
    value: my-value
```

### postgres_operator_helm_chart_ref

#### Default value

```YAML
postgres_operator_helm_chart_ref: '{{ postgres_operator_helm_repo_name }}/postgres-operator'
```

### postgres_operator_helm_chart_version

Helm chart version to install

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_helm_chart_version: 1.15.1
```

### postgres_operator_helm_repo_name

#### Default value

```YAML
postgres_operator_helm_repo_name: postgres-operator-charts
```

### postgres_operator_helm_repo_url

#### Default value

```YAML
postgres_operator_helm_repo_url: 
  https://opensource.zalando.com/postgres-operator/charts/postgres-operator
```

### postgres_operator_memory_limit

Memory limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_memory_limit: 500Mi
```

### postgres_operator_memory_request

Memory request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_memory_request: 250Mi
```

### postgres_operator_namespace

K8s namespace to install the postgres operator chart

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_namespace: postgres-operator
```

### postgres_operator_pod_security_context

Security context for operator pod

**_Type:_** dict<br />

#### Default value

```YAML
postgres_operator_pod_security_context:
  runAsUser: 1000
  runAsNonRoot: true
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
```

### postgres_operator_priority_class

PriorityClass configuration for operator
ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_priority_class: ''
```

### postgres_operator_ui_additional_helm_values

Additional Helm chart values to merge with the generated UI values.
Use this to configure any chart option not exposed as a dedicated variable.
ref: https://github.com/zalando/postgres-operator/blob/master/charts/postgres-operator-ui/values.yaml

**_Type:_** dict<br />

#### Default value

```YAML
postgres_operator_ui_additional_helm_values: {}
```

### postgres_operator_ui_cpu_limit

CPU limit for operator UI pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_cpu_limit: 200m
```

### postgres_operator_ui_cpu_request

CPU request for operator UI pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_cpu_request: 100m
```

### postgres_operator_ui_deployment_name

Deployment name for postgres operator UI chart

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_deployment_name: postgres-operator-ui
```

### postgres_operator_ui_enabled

Should Zalando Postgres Operator UI helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_ui_enabled: false
```

### postgres_operator_ui_extra_envs

Additional environment variables for the operator UI pod

**_Type:_** list<br />

#### Default value

```YAML
postgres_operator_ui_extra_envs: []
```

### postgres_operator_ui_helm_chart_ref

#### Default value

```YAML
postgres_operator_ui_helm_chart_ref: '{{ postgres_operator_ui_helm_repo_name }}/postgres-operator-ui'
```

### postgres_operator_ui_helm_chart_version

Helm chart version to install for the operator UI

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_helm_chart_version: 1.15.1
```

### postgres_operator_ui_helm_repo_name

#### Default value

```YAML
postgres_operator_ui_helm_repo_name: postgres-operator-ui-charts
```

### postgres_operator_ui_helm_repo_url

#### Default value

```YAML
postgres_operator_ui_helm_repo_url: 
  https://opensource.zalando.com/postgres-operator/charts/postgres-operator-ui
```

### postgres_operator_ui_ingress_annotations

Ingress annotations for operator UI

**_Type:_** dict<br />

#### Default value

```YAML
postgres_operator_ui_ingress_annotations: {}
```

### postgres_operator_ui_ingress_class_name

Ingress class name for operator UI

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_ingress_class_name: ''
```

### postgres_operator_ui_ingress_enabled

Enable ingress for operator UI

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_ui_ingress_enabled: false
```

### postgres_operator_ui_ingress_hosts

Ingress hosts configuration for operator UI

**_Type:_** list<br />

#### Default value

```YAML
postgres_operator_ui_ingress_hosts: []
```

#### Example usage

```YAML
 postgres_operator_ui_ingress_hosts:
  - host: ui.example.org
    paths: ["/"]
```

### postgres_operator_ui_ingress_tls

Ingress TLS configuration for operator UI

**_Type:_** list<br />

#### Default value

```YAML
postgres_operator_ui_ingress_tls: []
```

### postgres_operator_ui_memory_limit

Memory limit for operator UI pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_memory_limit: 200Mi
```

### postgres_operator_ui_memory_request

Memory request for operator UI pod

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_memory_request: 100Mi
```

### postgres_operator_ui_resources_visible

Show resources configuration in the UI

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_operator_ui_resources_visible: false
```

### postgres_operator_ui_target_namespace

Target namespace for viewing/creating clusters in the UI. Use "*" for all namespaces

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_ui_target_namespace: '*'
```

### postgres_operator_ui_teams

List of teams displayed in the UI

**_Type:_** list<br />

#### Default value

```YAML
postgres_operator_ui_teams:
  - acid
```

### postgres_operator_watched_namespace

Namespace to watch for PostgreSQL resources. Use "*" to watch all namespaces

**_Type:_** string<br />

#### Default value

```YAML
postgres_operator_watched_namespace: '*'
```

### postgres_operator_workers

Number of worker routines the operator uses to process events

**_Type:_** int<br />

#### Default value

```YAML
postgres_operator_workers: 8
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

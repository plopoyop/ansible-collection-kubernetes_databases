# opensearch_operator

Role to install the OpenSearch Operator on a Kubernetes cluster.
It installs the OpenSearch Operator via its helm chart.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [opensearch_operator_certmanager_enabled](#opensearch_operator_certmanager_enabled)
  - [opensearch_operator_cpu_limit](#opensearch_operator_cpu_limit)
  - [opensearch_operator_cpu_request](#opensearch_operator_cpu_request)
  - [opensearch_operator_deployment_name](#opensearch_operator_deployment_name)
  - [opensearch_operator_dns_base](#opensearch_operator_dns_base)
  - [opensearch_operator_enabled](#opensearch_operator_enabled)
  - [opensearch_operator_extra_env](#opensearch_operator_extra_env)
  - [opensearch_operator_helm_chart_ref](#opensearch_operator_helm_chart_ref)
  - [opensearch_operator_helm_repo_name](#opensearch_operator_helm_repo_name)
  - [opensearch_operator_helm_repo_url](#opensearch_operator_helm_repo_url)
  - [opensearch_operator_helm_version](#opensearch_operator_helm_version)
  - [opensearch_operator_image_pull_policy](#opensearch_operator_image_pull_policy)
  - [opensearch_operator_image_repository](#opensearch_operator_image_repository)
  - [opensearch_operator_image_tag](#opensearch_operator_image_tag)
  - [opensearch_operator_install_crds](#opensearch_operator_install_crds)
  - [opensearch_operator_log_level](#opensearch_operator_log_level)
  - [opensearch_operator_manager_security_context](#opensearch_operator_manager_security_context)
  - [opensearch_operator_memory_limit](#opensearch_operator_memory_limit)
  - [opensearch_operator_memory_request](#opensearch_operator_memory_request)
  - [opensearch_operator_metrics_bind_address](#opensearch_operator_metrics_bind_address)
  - [opensearch_operator_namespace](#opensearch_operator_namespace)
  - [opensearch_operator_node_selector](#opensearch_operator_node_selector)
  - [opensearch_operator_parallel_recovery_enabled](#opensearch_operator_parallel_recovery_enabled)
  - [opensearch_operator_pod_annotations](#opensearch_operator_pod_annotations)
  - [opensearch_operator_pod_labels](#opensearch_operator_pod_labels)
  - [opensearch_operator_pprof_enabled](#opensearch_operator_pprof_enabled)
  - [opensearch_operator_priority_class](#opensearch_operator_priority_class)
  - [opensearch_operator_security_context](#opensearch_operator_security_context)
  - [opensearch_operator_service_account_create](#opensearch_operator_service_account_create)
  - [opensearch_operator_service_account_name](#opensearch_operator_service_account_name)
  - [opensearch_operator_tolerations](#opensearch_operator_tolerations)
  - [opensearch_operator_use_role_bindings](#opensearch_operator_use_role_bindings)
  - [opensearch_operator_watch_namespace](#opensearch_operator_watch_namespace)
  - [opensearch_operator_webhook_enabled](#opensearch_operator_webhook_enabled)
  - [opensearch_operator_webhook_failure_policy](#opensearch_operator_webhook_failure_policy)
  - [opensearch_operator_webhook_port](#opensearch_operator_webhook_port)
  - [opensearch_operator_webhook_secret_name](#opensearch_operator_webhook_secret_name)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### opensearch_operator_certmanager_enabled

Enable cert-manager for automatic webhook certificate management

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_certmanager_enabled: true
```

### opensearch_operator_cpu_limit

CPU limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_cpu_limit: 1000m
```

### opensearch_operator_cpu_request

CPU request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_cpu_request: 200m
```

### opensearch_operator_deployment_name

Deployment name for OpenSearch operator chart

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_deployment_name: opensearch-operator
```

### opensearch_operator_dns_base

DNS domain suffix for Kubernetes service discovery

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_dns_base: cluster.local
```

### opensearch_operator_enabled

Should OpenSearch Operator helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_enabled: true
```

### opensearch_operator_extra_env

Additional environment variables for the manager

**_Type:_** list<br />

#### Default value

```YAML
opensearch_operator_extra_env: []
```

### opensearch_operator_helm_chart_ref

#### Default value

```YAML
opensearch_operator_helm_chart_ref: '{{ opensearch_operator_helm_repo_name }}/opensearch-operator'
```

### opensearch_operator_helm_repo_name

#### Default value

```YAML
opensearch_operator_helm_repo_name: opensearch-operator
```

### opensearch_operator_helm_repo_url

#### Default value

```YAML
opensearch_operator_helm_repo_url: 
  https://opensearch-project.github.io/opensearch-k8s-operator/
```

### opensearch_operator_helm_version

Helm chart version to install

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_helm_version: 3.0.2
```

### opensearch_operator_image_pull_policy

Image pull policy

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_image_pull_policy: Always
```

### opensearch_operator_image_repository

Image repository for the operator

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_image_repository: opensearchproject/opensearch-operator
```

### opensearch_operator_image_tag

Image tag (defaults to appVersion if empty)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_image_tag: ''
```

### opensearch_operator_install_crds

Install CRDs with Helm

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_install_crds: true
```

### opensearch_operator_log_level

Log level (debug, info, warn, error)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_log_level: info
```

### opensearch_operator_manager_security_context

Manager container security context

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_operator_manager_security_context:
  allowPrivilegeEscalation: false
```

### opensearch_operator_memory_limit

Memory limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_memory_limit: 500Mi
```

### opensearch_operator_memory_request

Memory request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_memory_request: 350Mi
```

### opensearch_operator_metrics_bind_address

Address the metrics endpoint binds to

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_metrics_bind_address: 127.0.0.1:8080
```

### opensearch_operator_namespace

K8s namespace to install the OpenSearch operator chart

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_namespace: opensearch-operator
```

### opensearch_operator_node_selector

Node selector for the operator pod

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_operator_node_selector: {}
```

### opensearch_operator_parallel_recovery_enabled

Enable experimental parallel recovery

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_parallel_recovery_enabled: true
```

### opensearch_operator_pod_annotations

Additional pod annotations

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_operator_pod_annotations: {}
```

### opensearch_operator_pod_labels

Additional pod labels

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_operator_pod_labels: {}
```

### opensearch_operator_pprof_enabled

Enable pprof endpoints on port 6060 (debugging only)

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_pprof_enabled: false
```

### opensearch_operator_priority_class

PriorityClass for the operator pod

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_priority_class: ''
```

### opensearch_operator_security_context

Pod security context

**_Type:_** dict<br />

#### Default value

```YAML
opensearch_operator_security_context:
  runAsNonRoot: true
```

### opensearch_operator_service_account_create

Create a service account

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_service_account_create: true
```

### opensearch_operator_service_account_name

Service account name (generated if empty)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_service_account_name: ''
```

### opensearch_operator_tolerations

Tolerations for the operator pod

**_Type:_** list<br />

#### Default value

```YAML
opensearch_operator_tolerations: []
```

### opensearch_operator_use_role_bindings

Use namespace-scoped RoleBindings instead of ClusterRoleBindings

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_use_role_bindings: false
```

### opensearch_operator_watch_namespace

Namespace to watch (empty = all namespaces, comma-separated for multiple)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_watch_namespace: ''
```

### opensearch_operator_webhook_enabled

Enable validation webhooks

**_Type:_** boolean<br />

#### Default value

```YAML
opensearch_operator_webhook_enabled: true
```

### opensearch_operator_webhook_failure_policy

Failure policy for webhooks (Fail or Ignore)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_webhook_failure_policy: Fail
```

### opensearch_operator_webhook_port

Port exposed by the webhook server

**_Type:_** int<br />

#### Default value

```YAML
opensearch_operator_webhook_port: 9443
```

### opensearch_operator_webhook_secret_name

Secret name for webhook TLS certificates (when cert-manager is disabled)

**_Type:_** string<br />

#### Default value

```YAML
opensearch_operator_webhook_secret_name: ''
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

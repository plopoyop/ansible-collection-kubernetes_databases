# redis_operator

Role to install the Redis Operator on a Kubernetes cluster.
It installs the OpsTree Redis Operator via its helm chart.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [redis_operator_affinity](#redis_operator_affinity)
  - [redis_operator_certmanager_enabled](#redis_operator_certmanager_enabled)
  - [redis_operator_cpu_limit](#redis_operator_cpu_limit)
  - [redis_operator_cpu_request](#redis_operator_cpu_request)
  - [redis_operator_deployment_name](#redis_operator_deployment_name)
  - [redis_operator_enabled](#redis_operator_enabled)
  - [redis_operator_env](#redis_operator_env)
  - [redis_operator_extra_args](#redis_operator_extra_args)
  - [redis_operator_feature_gates](#redis_operator_feature_gates)
  - [redis_operator_helm_chart_ref](#redis_operator_helm_chart_ref)
  - [redis_operator_helm_repo_name](#redis_operator_helm_repo_name)
  - [redis_operator_helm_repo_url](#redis_operator_helm_repo_url)
  - [redis_operator_helm_version](#redis_operator_helm_version)
  - [redis_operator_image_name](#redis_operator_image_name)
  - [redis_operator_image_pull_policy](#redis_operator_image_pull_policy)
  - [redis_operator_image_tag](#redis_operator_image_tag)
  - [redis_operator_issuer_create](#redis_operator_issuer_create)
  - [redis_operator_issuer_email](#redis_operator_issuer_email)
  - [redis_operator_issuer_kind](#redis_operator_issuer_kind)
  - [redis_operator_issuer_name](#redis_operator_issuer_name)
  - [redis_operator_issuer_private_key_secret_name](#redis_operator_issuer_private_key_secret_name)
  - [redis_operator_issuer_server](#redis_operator_issuer_server)
  - [redis_operator_issuer_solver_enabled](#redis_operator_issuer_solver_enabled)
  - [redis_operator_issuer_solver_ingress_class](#redis_operator_issuer_solver_ingress_class)
  - [redis_operator_issuer_type](#redis_operator_issuer_type)
  - [redis_operator_manager_config](#redis_operator_manager_config)
  - [redis_operator_memory_limit](#redis_operator_memory_limit)
  - [redis_operator_memory_request](#redis_operator_memory_request)
  - [redis_operator_metrics_bind_address](#redis_operator_metrics_bind_address)
  - [redis_operator_metrics_enabled](#redis_operator_metrics_enabled)
  - [redis_operator_namespace](#redis_operator_namespace)
  - [redis_operator_node_selector](#redis_operator_node_selector)
  - [redis_operator_pod_annotations](#redis_operator_pod_annotations)
  - [redis_operator_pod_labels](#redis_operator_pod_labels)
  - [redis_operator_pod_security_context](#redis_operator_pod_security_context)
  - [redis_operator_pprof_enabled](#redis_operator_pprof_enabled)
  - [redis_operator_priority_class](#redis_operator_priority_class)
  - [redis_operator_replicas](#redis_operator_replicas)
  - [redis_operator_security_context](#redis_operator_security_context)
  - [redis_operator_service_dns_domain](#redis_operator_service_dns_domain)
  - [redis_operator_tolerations](#redis_operator_tolerations)
  - [redis_operator_watch_namespace](#redis_operator_watch_namespace)
  - [redis_operator_webhook](#redis_operator_webhook)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### redis_operator_affinity

Affinity for the operator pod

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_affinity: {}
```

### redis_operator_certmanager_enabled

Use cert-manager for certificate management (only effective when webhook=true)

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_certmanager_enabled: false
```

### redis_operator_cpu_limit

CPU limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_cpu_limit: 500m
```

### redis_operator_cpu_request

CPU request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_cpu_request: 500m
```

### redis_operator_deployment_name

Deployment name for redis operator chart

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_deployment_name: redis-operator
```

### redis_operator_enabled

Should Redis Operator helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_enabled: true
```

### redis_operator_env

Additional environment variables

**_Type:_** list<br />

#### Default value

```YAML
redis_operator_env: []
```

### redis_operator_extra_args

Additional arguments for redis-operator container

**_Type:_** list<br />

#### Default value

```YAML
redis_operator_extra_args: []
```

### redis_operator_feature_gates

Feature gates for alpha/experimental features

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_feature_gates:
  GenerateConfigInInitContainer: false
```

### redis_operator_helm_chart_ref

#### Default value

```YAML
redis_operator_helm_chart_ref: '{{ redis_operator_helm_repo_name }}/redis-operator'
```

### redis_operator_helm_repo_name

#### Default value

```YAML
redis_operator_helm_repo_name: ot-helm
```

### redis_operator_helm_repo_url

#### Default value

```YAML
redis_operator_helm_repo_url: https://ot-container-kit.github.io/helm-charts/
```

### redis_operator_helm_version

Helm chart version to install

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_helm_version: 0.24.0
```

### redis_operator_image_name

Image repository for the redis operator

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_image_name: quay.io/opstree/redis-operator
```

### redis_operator_image_pull_policy

Image pull policy

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_image_pull_policy: Always
```

### redis_operator_image_tag

Image tag (defaults to chart appVersion if empty)

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_image_tag: ''
```

### redis_operator_issuer_create

Whether to create the issuer

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_issuer_create: true
```

### redis_operator_issuer_email

Email for the ACME issuer

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_email: ''
```

### redis_operator_issuer_kind

Kind of issuer (Issuer or ClusterIssuer)

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_kind: Issuer
```

### redis_operator_issuer_name

Name of the issuer

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_name: redis-operator-issuer
```

### redis_operator_issuer_private_key_secret_name

Secret name for the ACME private key

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_private_key_secret_name: letsencrypt-prod
```

### redis_operator_issuer_server

ACME server URL

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_server: https://acme-v02.api.letsencrypt.org/directory
```

### redis_operator_issuer_solver_enabled

Enable HTTP01 solver for ACME

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_issuer_solver_enabled: true
```

### redis_operator_issuer_solver_ingress_class

Ingress class for the HTTP01 solver

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_solver_ingress_class: nginx
```

### redis_operator_issuer_type

Type of issuer (selfSigned or acme)

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_issuer_type: selfSigned
```

### redis_operator_manager_config

Config values for the operator manager

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_manager_config:
  kubeClientTimeout: 60s
  kubeClientQPS: 0.0
```

### redis_operator_memory_limit

Memory limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_memory_limit: 500Mi
```

### redis_operator_memory_request

Memory request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_memory_request: 500Mi
```

### redis_operator_metrics_bind_address

Address the metrics endpoint binds to

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_metrics_bind_address: :8080
```

### redis_operator_metrics_enabled

Enable metrics server

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_metrics_enabled: true
```

### redis_operator_namespace

K8s namespace to install the redis operator chart

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_namespace: redis-operator
```

### redis_operator_node_selector

Node selector for the operator pod

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_node_selector: {}
```

### redis_operator_pod_annotations

Additional pod annotations

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_pod_annotations: {}
```

### redis_operator_pod_labels

Additional pod labels

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_pod_labels: {}
```

### redis_operator_pod_security_context

Security context for the operator pod

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_pod_security_context: {}
```

### redis_operator_pprof_enabled

Enable pprof server for performance profiling

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_pprof_enabled: false
```

### redis_operator_priority_class

PriorityClass configuration for operator

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_priority_class: ''
```

### redis_operator_replicas

Number of replicas for redis operator

**_Type:_** int<br />

#### Default value

```YAML
redis_operator_replicas: 1
```

### redis_operator_security_context

Security context for the operator container

**_Type:_** dict<br />

#### Default value

```YAML
redis_operator_security_context: {}
```

### redis_operator_service_dns_domain

DNS domain suffix for Kubernetes service discovery

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_service_dns_domain: cluster.local
```

### redis_operator_tolerations

Tolerations for the operator pod

**_Type:_** list<br />

#### Default value

```YAML
redis_operator_tolerations: []
```

### redis_operator_watch_namespace

Namespace to watch (empty = all namespaces)

**_Type:_** string<br />

#### Default value

```YAML
redis_operator_watch_namespace: ''
```

### redis_operator_webhook

Enable webhook server for masterSlaveAntiAffinity feature

**_Type:_** boolean<br />

#### Default value

```YAML
redis_operator_webhook: false
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

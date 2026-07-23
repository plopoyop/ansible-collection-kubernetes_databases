# mongodb_operator

Role to install Install Mongodb for Kubernetes operaror on a cluster.
It install community operator via its helm chart and deploy mongodb replicatset.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [mongodb_operator_cpu_limit](#mongodb_operator_cpu_limit)
  - [mongodb_operator_cpu_request](#mongodb_operator_cpu_request)
  - [mongodb_operator_crds_upgrade_enabled](#mongodb_operator_crds_upgrade_enabled)
  - [mongodb_operator_deployment_name](#mongodb_operator_deployment_name)
  - [mongodb_operator_enabled](#mongodb_operator_enabled)
  - [mongodb_operator_extra_envs](#mongodb_operator_extra_envs)
  - [mongodb_operator_helm_version](#mongodb_operator_helm_version)
  - [mongodb_operator_memory_limit](#mongodb_operator_memory_limit)
  - [mongodb_operator_memory_request](#mongodb_operator_memory_request)
  - [mongodb_operator_namespace](#mongodb_operator_namespace)
  - [mongodb_operator_pod_security_context](#mongodb_operator_pod_security_context)
  - [mongodb_operator_priority_class](#mongodb_operator_priority_class)
  - [mongodb_operator_replicas](#mongodb_operator_replicas)
  - [mongodb_operator_security_context](#mongodb_operator_security_context)
  - [mongodb_operator_watch_namespace](#mongodb_operator_watch_namespace)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.17`

## Default Variables

### mongodb_operator_cpu_limit

CPU limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_cpu_limit: 1100m
```

### mongodb_operator_cpu_request

CPU request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_cpu_request: 500m
```

### mongodb_operator_crds_upgrade_enabled

Apply operator CRDs (server-side, force conflicts) before helm upgrade.
Helm does not update CRDs automatically (HIP-0011), so we render the
target chart with `helm_template --include-crds` and apply only the
CustomResourceDefinition resources. Skipped on first install since
`helm install` already applies CRDs from the chart's `crds/` directory.

**_Type:_** boolean<br />

#### Default value

```YAML
mongodb_operator_crds_upgrade_enabled: true
```

### mongodb_operator_deployment_name

Deployment name for mongodb community operator chart

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_deployment_name: mongodb-operator
```

### mongodb_operator_enabled

Should MongoDb for Kubernetes Operator helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
mongodb_operator_enabled: true
```

### mongodb_operator_extra_envs

Additional environment variables

**_Type:_** list<br />

#### Default value

```YAML
mongodb_operator_extra_envs: []
```

#### Example usage

```YAML
 mongodb_operator_extra_envs:
  - name: CLUSTER_DOMAIN
    value: my-cluster.domain
```

### mongodb_operator_helm_version

Helm chart version to install

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_helm_version: 1.9.1
```

### mongodb_operator_memory_limit

Memory limit for operator pod

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_memory_limit: 1Gi
```

### mongodb_operator_memory_request

Memory request for operator pod

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_memory_request: 200Mi
```

### mongodb_operator_namespace

K8s namespace to install the mongodb community operator chart

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_namespace: mongodb
```

### mongodb_operator_pod_security_context

security context for operator pod

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_operator_pod_security_context:
  runAsNonRoot: true
  runAsUser: 2000
```

### mongodb_operator_priority_class

PriorityClass configuration for operator
ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_priority_class: ''
```

### mongodb_operator_replicas

Number of replicat for mongodb operator

**_Type:_** int<br />

#### Default value

```YAML
mongodb_operator_replicas: 1
```

### mongodb_operator_security_context

security context for operator

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_operator_security_context: {}
```

### mongodb_operator_watch_namespace

To configure the Operator to watch resources in another namespace

**_Type:_** string<br />

#### Default value

```YAML
mongodb_operator_watch_namespace: '*'
```

## Discovered Tags

**_always_**

**_crds_**

**_helm_chart_**

**_helm_repository_**

**_namespace_**

## Dependencies

None.

## License

MPL-2.0

## Author

Clément Hubert

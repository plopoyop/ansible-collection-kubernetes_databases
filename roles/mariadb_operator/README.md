# mariadb_operator

Role to install the MariaDB Operator on a Kubernetes cluster.
It installs the operator CRDs and operator via their helm charts.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [mariadb_operator_additional_helm_values](#mariadb_operator_additional_helm_values)
  - [mariadb_operator_affinity](#mariadb_operator_affinity)
  - [mariadb_operator_cert_controller_enabled](#mariadb_operator_cert_controller_enabled)
  - [mariadb_operator_cert_controller_ha_enabled](#mariadb_operator_cert_controller_ha_enabled)
  - [mariadb_operator_cert_controller_ha_replicas](#mariadb_operator_cert_controller_ha_replicas)
  - [mariadb_operator_cert_controller_resources](#mariadb_operator_cert_controller_resources)
  - [mariadb_operator_cluster_name](#mariadb_operator_cluster_name)
  - [mariadb_operator_crds_deployment_name](#mariadb_operator_crds_deployment_name)
  - [mariadb_operator_crds_enabled](#mariadb_operator_crds_enabled)
  - [mariadb_operator_crds_helm_chart_ref](#mariadb_operator_crds_helm_chart_ref)
  - [mariadb_operator_crds_helm_chart_version](#mariadb_operator_crds_helm_chart_version)
  - [mariadb_operator_current_namespace_only](#mariadb_operator_current_namespace_only)
  - [mariadb_operator_deployment_name](#mariadb_operator_deployment_name)
  - [mariadb_operator_enabled](#mariadb_operator_enabled)
  - [mariadb_operator_extra_envs](#mariadb_operator_extra_envs)
  - [mariadb_operator_ha_enabled](#mariadb_operator_ha_enabled)
  - [mariadb_operator_ha_replicas](#mariadb_operator_ha_replicas)
  - [mariadb_operator_helm_chart_ref](#mariadb_operator_helm_chart_ref)
  - [mariadb_operator_helm_chart_version](#mariadb_operator_helm_chart_version)
  - [mariadb_operator_helm_repo_name](#mariadb_operator_helm_repo_name)
  - [mariadb_operator_helm_repo_url](#mariadb_operator_helm_repo_url)
  - [mariadb_operator_log_level](#mariadb_operator_log_level)
  - [mariadb_operator_metrics_enabled](#mariadb_operator_metrics_enabled)
  - [mariadb_operator_namespace](#mariadb_operator_namespace)
  - [mariadb_operator_node_selector](#mariadb_operator_node_selector)
  - [mariadb_operator_pdb_enabled](#mariadb_operator_pdb_enabled)
  - [mariadb_operator_pdb_max_unavailable](#mariadb_operator_pdb_max_unavailable)
  - [mariadb_operator_pod_security_context](#mariadb_operator_pod_security_context)
  - [mariadb_operator_resources](#mariadb_operator_resources)
  - [mariadb_operator_security_context](#mariadb_operator_security_context)
  - [mariadb_operator_tolerations](#mariadb_operator_tolerations)
  - [mariadb_operator_webhook_cert_manager_enabled](#mariadb_operator_webhook_cert_manager_enabled)
  - [mariadb_operator_webhook_enabled](#mariadb_operator_webhook_enabled)
  - [mariadb_operator_webhook_ha_enabled](#mariadb_operator_webhook_ha_enabled)
  - [mariadb_operator_webhook_ha_replicas](#mariadb_operator_webhook_ha_replicas)
  - [mariadb_operator_webhook_resources](#mariadb_operator_webhook_resources)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### mariadb_operator_additional_helm_values

Additional Helm chart values to merge with the generated values.
Use this to configure any chart option not exposed as a dedicated variable.
ref: https://github.com/mariadb-operator/mariadb-operator/blob/main/deploy/charts/mariadb-operator/values.yaml

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_additional_helm_values: {}
```

### mariadb_operator_affinity

Affinity for operator pod

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_affinity: {}
```

### mariadb_operator_cert_controller_enabled

Enable the cert-controller for TLS certificate provisioning

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_cert_controller_enabled: true
```

### mariadb_operator_cert_controller_ha_enabled

Enable high availability for the cert-controller

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_cert_controller_ha_enabled: false
```

### mariadb_operator_cert_controller_ha_replicas

Number of cert-controller replicas for HA mode

**_Type:_** int<br />

#### Default value

```YAML
mariadb_operator_cert_controller_ha_replicas: 3
```

### mariadb_operator_cert_controller_resources

Resources for cert-controller container

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_cert_controller_resources: {}
```

#### Example usage

```YAML
mariadb_operator_cert_controller_resources:
  requests:
    cpu: 10m
    memory: 32Mi
```

### mariadb_operator_cluster_name

Kubernetes cluster DNS name

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_cluster_name: cluster.local
```

### mariadb_operator_crds_deployment_name

Deployment name for mariadb operator CRDs chart

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_crds_deployment_name: mariadb-operator-crds
```

### mariadb_operator_crds_enabled

Should MariaDB Operator CRDs helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_crds_enabled: true
```

### mariadb_operator_crds_helm_chart_ref

#### Default value

```YAML
mariadb_operator_crds_helm_chart_ref: '{{ mariadb_operator_helm_repo_name }}/mariadb-operator-crds'
```

### mariadb_operator_crds_helm_chart_version

Helm chart version to install for the CRDs

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_crds_helm_chart_version: 26.3.0
```

### mariadb_operator_current_namespace_only

Whether the operator should watch CRDs only in its own namespace

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_current_namespace_only: false
```

### mariadb_operator_deployment_name

Deployment name for mariadb operator chart

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_deployment_name: mariadb-operator
```

### mariadb_operator_enabled

Should MariaDB Operator helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_enabled: true
```

### mariadb_operator_extra_envs

Additional environment variables for the operator pod

**_Type:_** list<br />

#### Default value

```YAML
mariadb_operator_extra_envs: []
```

### mariadb_operator_ha_enabled

Enable high availability of the controller

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_ha_enabled: false
```

### mariadb_operator_ha_replicas

Number of replicas for HA mode

**_Type:_** int<br />

#### Default value

```YAML
mariadb_operator_ha_replicas: 3
```

### mariadb_operator_helm_chart_ref

#### Default value

```YAML
mariadb_operator_helm_chart_ref: '{{ mariadb_operator_helm_repo_name }}/mariadb-operator'
```

### mariadb_operator_helm_chart_version

Helm chart version to install for the operator

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_helm_chart_version: 25.10.4
```

### mariadb_operator_helm_repo_name

#### Default value

```YAML
mariadb_operator_helm_repo_name: mariadb-operator
```

### mariadb_operator_helm_repo_url

#### Default value

```YAML
mariadb_operator_helm_repo_url: https://helm.mariadb.com/mariadb-operator
```

### mariadb_operator_log_level

Controller log level

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_log_level: INFO
```

### mariadb_operator_metrics_enabled

Enable operator internal metrics (requires Prometheus)

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_metrics_enabled: false
```

### mariadb_operator_namespace

K8s namespace to install the mariadb operator charts

**_Type:_** string<br />

#### Default value

```YAML
mariadb_operator_namespace: mariadb-operator
```

### mariadb_operator_node_selector

Node selectors for operator pod

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_node_selector: {}
```

### mariadb_operator_pdb_enabled

Enable PodDisruptionBudget for the controller

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_pdb_enabled: false
```

### mariadb_operator_pdb_max_unavailable

Maximum number of unavailable pods

**_Type:_** int<br />

#### Default value

```YAML
mariadb_operator_pdb_max_unavailable: 1
```

### mariadb_operator_pod_security_context

Security context for operator pod

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_pod_security_context: {}
```

### mariadb_operator_resources

Resources for operator controller container

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_resources: {}
```

#### Example usage

```YAML
mariadb_operator_resources:
  requests:
    cpu: 10m
    memory: 32Mi
```

### mariadb_operator_security_context

Security context for operator container

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_security_context: {}
```

### mariadb_operator_tolerations

Tolerations for operator pod

**_Type:_** list<br />

#### Default value

```YAML
mariadb_operator_tolerations: []
```

### mariadb_operator_webhook_cert_manager_enabled

Use cert-manager to issue and rotate webhook certificates.
If false, mariadb-operator cert-controller will be used instead

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_webhook_cert_manager_enabled: false
```

### mariadb_operator_webhook_enabled

Enable the webhook server for CRD validation

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_webhook_enabled: true
```

### mariadb_operator_webhook_ha_enabled

Enable high availability for the webhook

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_operator_webhook_ha_enabled: false
```

### mariadb_operator_webhook_ha_replicas

Number of webhook replicas for HA mode

**_Type:_** int<br />

#### Default value

```YAML
mariadb_operator_webhook_ha_replicas: 3
```

### mariadb_operator_webhook_resources

Resources for webhook container

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_operator_webhook_resources: {}
```

#### Example usage

```YAML
mariadb_operator_webhook_resources:
  requests:
    cpu: 10m
    memory: 32Mi
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

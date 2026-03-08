# postgres_instance

Role to install PostgreSQL instances on kubernetes cluster.
It deploys PostgreSQL instances using the Zalando Postgres Operator CRDs via a helm chart.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [postgres_default_instance](#postgres_default_instance)
  - [postgres_instance_crd_helm_chart_ref](#postgres_instance_crd_helm_chart_ref)
  - [postgres_instance_crd_helm_repo_name](#postgres_instance_crd_helm_repo_name)
  - [postgres_instance_crd_helm_repo_url](#postgres_instance_crd_helm_repo_url)
  - [postgres_instance_crd_helm_version](#postgres_instance_crd_helm_version)
  - [postgres_instance_enabled](#postgres_instance_enabled)
  - [postgres_instance_name](#postgres_instance_name)
  - [postgres_instance_namespace](#postgres_instance_namespace)
  - [postgres_instance_number_of_instances](#postgres_instance_number_of_instances)
  - [postgres_instance_team_id](#postgres_instance_team_id)
  - [postgres_instance_values_override](#postgres_instance_values_override)
  - [postgres_instance_version](#postgres_instance_version)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### postgres_default_instance

Default values for helm chart deployment

**_Type:_** dict<br />

#### Default value

```YAML
postgres_default_instance:
  name: '{{ postgres_instance_name }}'
  namespace: '{{ postgres_instance_namespace }}'
  teamId: '{{ postgres_instance_team_id }}'
  numberOfInstances: '{{ postgres_instance_number_of_instances }}'
  version: '{{ postgres_instance_version }}'
  users:
    admin:
      - superuser
      - createdb
  databases:
    app: admin
  preparedDatabases: {}
  postgresql:
    parameters: {}
  volume:
    size: 1Gi
  additionalVolumes: []
  enableShmVolume: true
  resources:
    requests:
      cpu: 10m
      memory: 100Mi
    limits:
      cpu: 500m
      memory: 500Mi
  patroni:
    failsafe_mode: false
    initdb:
      encoding: UTF8
      locale: en_US.UTF-8
      data-checksums: 'true'
    ttl: 30
    loop_wait: 10
    retry_timeout: 10
    synchronous_mode: false
    synchronous_mode_strict: false
    synchronous_node_count: 1
    maximum_lag_on_failover: 33554432
  enableMasterLoadBalancer: false
  enableReplicaLoadBalancer: false
  enableConnectionPooler: false
  enableReplicaConnectionPooler: false
  enableMasterPoolerLoadBalancer: false
  enableReplicaPoolerLoadBalancer: false
  connectionPooler: {}
  allowedSourceRanges: []
  tls:
    secretName: ''
    certificateFile: tls.crt
    privateKeyFile: tls.key
    caFile: ''
    caSecretName: ''
  enableLogicalBackup: false
  logicalBackupSchedule: 30 00 * * *
  initContainers: []
  sidecars: []
  podAnnotations: {}
  serviceAnnotations: {}
  podPriorityClassName: ''
  tolerations: []
  nodeAffinity: {}
  env: []
  postgresTeams: []
```

### postgres_instance_crd_helm_chart_ref

#### Default value

```YAML
postgres_instance_crd_helm_chart_ref: '{{ postgres_instance_crd_helm_repo_name }}/postgresql-instance'
```

### postgres_instance_crd_helm_repo_name

#### Default value

```YAML
postgres_instance_crd_helm_repo_name: plopoyop
```

### postgres_instance_crd_helm_repo_url

#### Default value

```YAML
postgres_instance_crd_helm_repo_url: https://plopoyop.github.io/charts
```

### postgres_instance_crd_helm_version

PostgreSQL instance helm chart version

**_Type:_** string<br />

#### Default value

```YAML
postgres_instance_crd_helm_version: 0.1.0
```

### postgres_instance_enabled

Should PostgreSQL instance helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
postgres_instance_enabled: true
```

### postgres_instance_name

PostgreSQL instance name

**_Type:_** string<br />

#### Default value

```YAML
postgres_instance_name: postgres-database
```

### postgres_instance_namespace

K8s namespace to deploy PostgreSQL instance

**_Type:_** string<br />

#### Default value

```YAML
postgres_instance_namespace: postgres
```

### postgres_instance_number_of_instances

Number of PostgreSQL instances (replicas)

**_Type:_** integer<br />

#### Default value

```YAML
postgres_instance_number_of_instances: 2
```

### postgres_instance_team_id

Team ID for the PostgreSQL instance (used by Zalando operator)

**_Type:_** string<br />

#### Default value

```YAML
postgres_instance_team_id: acid
```

### postgres_instance_values_override

Overrides for default values

**_Type:_** dict<br />

#### Default value

```YAML
postgres_instance_values_override: {}
```

#### Example usage

```YAML
 postgres_instance_values_override:
   numberOfInstances: 3
   users:
     app_user:
       - createdb
   databases:
     mydb: app_user
   volume:
     size: 10Gi
     storageClass: fast-ssd
```

### postgres_instance_version

PostgreSQL version

**_Type:_** string<br />

#### Default value

```YAML
postgres_instance_version: '17'
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

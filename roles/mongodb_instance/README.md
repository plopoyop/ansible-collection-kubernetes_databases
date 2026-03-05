# mongodb_instance

Role to install mongodb on kubernetes cluster.
It install community operator via its helm chart and deploy mongodb replicatset.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [mongodb_default_instance](#mongodb_default_instance)
  - [mongodb_instance_crd_helm_chart_ref](#mongodb_instance_crd_helm_chart_ref)
  - [mongodb_instance_crd_helm_repo_name](#mongodb_instance_crd_helm_repo_name)
  - [mongodb_instance_crd_helm_repo_url](#mongodb_instance_crd_helm_repo_url)
  - [mongodb_instance_crd_helm_version](#mongodb_instance_crd_helm_version)
  - [mongodb_instance_enabled](#mongodb_instance_enabled)
  - [mongodb_instance_members](#mongodb_instance_members)
  - [mongodb_instance_name](#mongodb_instance_name)
  - [mongodb_instance_namespace](#mongodb_instance_namespace)
  - [mongodb_instance_values_override](#mongodb_instance_values_override)
  - [mongodb_instance_version](#mongodb_instance_version)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### mongodb_default_instance

Overrides for default values

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_default_instance:
  name: '{{ mongodb_instance_name }}'
  namespace: '{{ mongodb_instance_namespace }}'
  version: '{{ mongodb_instance_version }}'
  feature_compatibility_version: "{{ (mongodb_instance_version | ansible.builtin.split('.'))[0]
    }}.{{ (mongodb_instance_version | ansible.builtin.split('.'))[1] }}"
  members: '{{ mongodb_instance_members }}'
  persistent: true
  create_service_account: false
  admin_password: '{{ mongodb_instance_admin_password }}'
  additional_connection_string_config: {}
  additional_mongod_config: {}
  container_additional_config: {}
  backup_enabled: false
  backup_cronjob_schedule: '*/20 * * * *'
  backup_cronjob_timezone: Europe/Paris
  backup_cronjob_command: []
  backup_cronjob_container_env: []
  backup_cronjob_container_secret_env: []
  backup_cronjob_image: {}
  backup_cronjob_image_pull_secret: {}
  backup_additional_config: {}
  metrics_enabled: false
  metrics_username: prometheus
  metrics_password: ''
```

### mongodb_instance_crd_helm_chart_ref

#### Default value

```YAML
mongodb_instance_crd_helm_chart_ref: '{{ mongodb_instance_crd_helm_repo_name }}/mongodb-instance'
```

### mongodb_instance_crd_helm_repo_name

#### Default value

```YAML
mongodb_instance_crd_helm_repo_name: plopoyop
```

### mongodb_instance_crd_helm_repo_url

#### Default value

```YAML
mongodb_instance_crd_helm_repo_url: https://plopoyop.github.io/charts
```

### mongodb_instance_crd_helm_version

mongodb instance helm chart version

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_crd_helm_version: 0.2.3
```

### mongodb_instance_enabled

Should MongoDb Instance helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
mongodb_instance_enabled: true
```

### mongodb_instance_members

number of replicatset members

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_members: 3
```

### mongodb_instance_name

mongodb instance name

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_name: mongodb-database
```

### mongodb_instance_namespace

K8s namespace to install deploy mongodb instance

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_namespace: mongodb
```

### mongodb_instance_values_override

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_values_override: {}
```

#### Example usage

```YAML
 mongodb_instance_values_override:
   create_service_account: true
   additional_connection_string_config:
     authenticationMechanism: "scram-sha256"
     authSource: "admin"
   metrics_enabled: true
   metrics_username: "monitoring"
   metrics_password: "metricspassword"
```

### mongodb_instance_version

mongodb version

**_Type:_** dict<br />

#### Default value

```YAML
mongodb_instance_version: 8.0.6
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

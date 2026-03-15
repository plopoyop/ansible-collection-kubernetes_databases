# mariadb_instance

Role to deploy MariaDB instances on a kubernetes cluster.
It deploys MariaDB cluster instances via the mariadb-cluster helm chart using the MariaDB operator.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [mariadb_default_instance](#mariadb_default_instance)
  - [mariadb_instance_crd_helm_chart_ref](#mariadb_instance_crd_helm_chart_ref)
  - [mariadb_instance_crd_helm_repo_name](#mariadb_instance_crd_helm_repo_name)
  - [mariadb_instance_crd_helm_repo_url](#mariadb_instance_crd_helm_repo_url)
  - [mariadb_instance_crd_helm_version](#mariadb_instance_crd_helm_version)
  - [mariadb_instance_enabled](#mariadb_instance_enabled)
  - [mariadb_instance_name](#mariadb_instance_name)
  - [mariadb_instance_namespace](#mariadb_instance_namespace)
  - [mariadb_instance_values_override](#mariadb_instance_values_override)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### mariadb_default_instance

default values for helm chart deployment

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_default_instance:
  name: '{{ mariadb_instance_name }}'
  namespace: '{{ mariadb_instance_namespace }}'
  root_password_secret_name: ''
  root_password_secret_key: root
  root_password_generate: true
  storage_size: 1Gi
  replicas: 3
  galera_enabled: true
  databases: []
  users: []
  grants: []
  backups: []
  physical_backups: []
```

### mariadb_instance_crd_helm_chart_ref

#### Default value

```YAML
mariadb_instance_crd_helm_chart_ref: '{{ mariadb_instance_crd_helm_repo_name }}/mariadb-cluster'
```

### mariadb_instance_crd_helm_repo_name

#### Default value

```YAML
mariadb_instance_crd_helm_repo_name: mariadb-operator
```

### mariadb_instance_crd_helm_repo_url

#### Default value

```YAML
mariadb_instance_crd_helm_repo_url: https://helm.mariadb.com/mariadb-operator
```

### mariadb_instance_crd_helm_version

mariadb instance helm chart version

**_Type:_** string<br />

#### Default value

```YAML
mariadb_instance_crd_helm_version: 26.3.0
```

### mariadb_instance_enabled

Should MariaDB Instance helm chart be installed

**_Type:_** boolean<br />

#### Default value

```YAML
mariadb_instance_enabled: true
```

### mariadb_instance_name

mariadb instance helm release name

**_Type:_** string<br />

#### Default value

```YAML
mariadb_instance_name: mariadb-database
```

### mariadb_instance_namespace

K8s namespace to deploy mariadb instance

**_Type:_** string<br />

#### Default value

```YAML
mariadb_instance_namespace: mariadb
```

### mariadb_instance_values_override

Overrides for default values

**_Type:_** dict<br />

#### Default value

```YAML
mariadb_instance_values_override: {}
```

#### Example usage

```YAML
 mariadb_instance_values_override:
   replicas: 1
   galera_enabled: false
   databases:
     - name: mydb
       characterSet: utf8
       collate: utf8_general_ci
   users:
     - name: myuser
       passwordSecretKeyRef:
         name: myuser-password
         key: password
         generate: true
       maxUserConnections: 20
       host: "%"
   grants:
     - name: myuser-mydb-grant
       username: myuser
       database: mydb
       table: "*"
       privileges:
         - ALL
       grantOption: true
```

## Dependencies

None.

## License

MLP2

## Author

Clément Hubert

# Ansible Collection - plopoyop.kubernetes_databases

## Description

This Ansible collection provides a set of roles to install and configure various databases system on a Kubernetes cluster using their helm charts. The goal is to simplify and automate the deployment of these databases using Ansible.

## Contents

This collection includes multiple Ansible roles designed to install and configure databases for a Kubernetes cluster. Each role is designed to be as configurable as possible while providing default settings tailored to my specific usage.

## Disclaimer

The roles provided in this collection are developed based on my usage of the apps and my specific needs. While configuration options are available to adjust their behavior, not all possible options are necessarily supported.

Before using this collection in production, ensure that the default configurations meet your needs and adjust them if necessary.

## Prerequisites

- Ansible >= 2.9
- A running Kubernetes cluster
- Administrator access to cluster nodes (if required for certain installations)

## Installation

To install this collection, use the following command:

```sh
ansible-galaxy collection install plopoyop.kubernetes_databases
```

## Collection content
### List of Roles and Helm Chart Versions

| Role Name       | Helm Chart Version | Role Tag              | README Link                                 |
| ---------       | ------------------ | --------------------- | ------------------------------------        |
| MariaDB Instance  | v26.6.0           | `mariadb_instance`    | [View README](roles/mariadb_instance/README.md)  |
| MariaDB Operator  | v26.6.0           | `mariadb_operator`    | [View README](roles/mariadb_operator/README.md)  |
| MongoDb for Kubernetes | v1.8.1            | `mongodb_operator`    | [View README](roles/mongodb_operator/README.md) |
| MongoDb Instance | v0.2.4            | `mongodb_instance`    | [View README](roles/mongodb_instance/README.md) |
| OpenSearch Cluster  | v3.3.0          | `opensearch_cluster`  | [View README](roles/opensearch_cluster/README.md)  |
| OpenSearch Operator | v3.0.2          | `opensearch_operator` | [View README](roles/opensearch_operator/README.md) |
| Postgres Operator | v1.15.1            | `postgres_operator`   | [View README](roles/postgres_operator/README.md) |
| Postgres Instance | v0.1.0             | `postgres_instance`   | [View README](roles/postgres_instance/README.md) |
| Redis Standalone  | v0.16.9            | `redis_instance`      | [View README](roles/redis_instance/README.md)    |
| Redis Replication | v0.17.0            | `redis_instance`      | [View README](roles/redis_instance/README.md)    |
| Redis Cluster     | v0.17.4            | `redis_instance`      | [View README](roles/redis_instance/README.md)    |
| Redis Sentinel    | v0.16.12           | `redis_instance`      | [View README](roles/redis_instance/README.md)    |
| Redis Operator    | v0.24.0            | `redis_operator`      | [View README](roles/redis_operator/README.md)    |

### Tags

Every role in this collection ships tagged tasks so you can selectively run only what you need with `ansible-playbook --tags` or skip parts with `--skip-tags`.

Three kinds of tags are exposed:

- **Role tag** — named after the role itself (e.g. `mariadb_instance`, `mariadb_operator`, `mongodb_instance`, `mongodb_operator`, `opensearch_cluster`, `opensearch_operator`, `postgres_instance`, `postgres_operator`, `redis_instance`, `redis_operator`). Use it to scope a run to a single database component.
- **Action tag** — `install` or `uninstall`. The role's `*_enabled` variable controls which one runs:
  - When `<role>_enabled: true`, the setup tasks (tagged `install`) are executed.
  - When `<role>_enabled: false`, the cleanup tasks (tagged `uninstall`) are executed.
- **Task-type tag** — applied per task to scope a run to a specific phase (e.g. only create the namespace, only manage CRDs):

  | Tag               | Applied to                                                                                                  |
  | ----------------- | ----------------------------------------------------------------------------------------------------------- |
  | `namespace`       | Namespace creation/deletion                                                                                 |
  | `helm_repository` | Adding/removing helm repositories                                                                           |
  | `helm_chart`      | Helm chart install/upgrade/uninstall for application/operator charts                                        |
  | `crds`            | CRD-only helm charts (e.g. `mariadb_operator_crds`) and any direct CRD manifest application                 |
  | `manifest`        | Other Kubernetes resources (custom resources, additional manifests)                                         |

  Pure helper tasks (`set_fact`, etc.) carry only the role + action tags so they run alongside any phase that needs them.

> **Note:** the `mariadb_operator` role evaluates both `mariadb_operator_enabled` and `mariadb_operator_crds_enabled`. Cleanup runs only when both are `false`.

#### Examples

Install only the PostgreSQL operator:

```sh
ansible-playbook playbook.yml --tags "postgres_operator,install"
```

Run install actions for every role:

```sh
ansible-playbook playbook.yml --tags "install"
```

Uninstall only the Redis instance (requires `redis_instance_enabled: false`):

```sh
ansible-playbook playbook.yml --tags "redis_instance,uninstall"
```

Run everything except OpenSearch:

```sh
ansible-playbook playbook.yml --skip-tags "opensearch_cluster,opensearch_operator"
```

Prepare prerequisites only (create namespace + add helm repo) without installing the chart, e.g. for the MariaDB operator:

```sh
ansible-playbook playbook.yml --tags "mariadb_operator,namespace,helm_repository"
```

Install only the CRDs of the MariaDB operator (skip the operator chart itself):

```sh
ansible-playbook playbook.yml --tags "mariadb_operator,crds"
```

Uninstall a Postgres instance but keep its namespace:

```sh
ansible-playbook playbook.yml --tags "postgres_instance,uninstall" --skip-tags "namespace"
```

## Usage

You can call the roles from this collection in your Ansible playbooks as follows:

```yaml
- name: Install a tool on Kubernetes
  hosts: localhost
  roles:
    - role: plopoyop.kubernetes_databases.role_name
      vars:
        config_option: value
```

## Customization

Each role exposes variables to adjust the configuration of the installed tools. Refer to each role's documentation for available variables.

Contributions are welcome! Feel free to open issues or submit pull requests to improve the roles and add new features.

## Tools
[Devbox](https://www.jetify.com/docs/devbox) is used to make reproducible development environments

[Task](https://taskfile.dev/) as a task runner

[Renovate](https://github.com/renovatebot/renovate) to update dependencies

## License

This collection is distributed under the Mozilla Public License Version 2.0 license.

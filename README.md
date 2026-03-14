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

| Role Name       | Helm Chart Version | README Link                                 |
| ---------       | ------------------ | ------------------------------------        |
| MariaDB Instance  | v25.10.4           | [View README](roles/mariadb_instance/README.md)  |
| MariaDB Operator  | v26.3.0           | [View README](roles/mariadb_operator/README.md)  |
| MongoDb for Kubernetes | v1.7.0            | [View README](roles/mongodb_instance/README.md) |
| MongoDb Instance | v0.2.3            | [View README](roles/mongodb_instance/README.md) |
| Postgres Operator | v1.15.1            | [View README](roles/postgres_operator/README.md) |
| Postgres Instance | v0.1.0             | [View README](roles/postgres_instance/README.md) |


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

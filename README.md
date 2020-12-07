# [f5_ltm](#f5_ltm)

Configure an F5 LTMs nodes, pool, pool members and virtual servers.

|Travis|GitHub|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-f5_ltm.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-f5_ltm)|[![github](https://github.com/robertdebock/ansible-role-f5_ltm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-f5_ltm/actions)|[![quality](https://img.shields.io/ansible/quality/43521)](https://galaxy.ansible.com/robertdebock/f5_ltm)|[![downloads](https://img.shields.io/ansible/role/d/43521)](https://galaxy.ansible.com/robertdebock/f5_ltm)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-f5_ltm.svg)](https://github.com/robertdebock/ansible-role-f5_ltm/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.f5_ltm
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for f5_ltm

# Connection details for the F5 LTM.
# f5_ltm_provider:
#   server: 192.168.1.254
#   user: root
#   password: password
#   server_port: 8443
#   validate_certs: no

# General settings for the F5 LTM.
f5_ltm_partition: Common
f5_ltm_hostname: f5.example.com
f5_ltm_timezone: "Europe/Amsterdam"
f5_ltm_ntp_servers:
  - 1.1.1.1
  - 8.8.8.8

# The list of nodes.
# f5_ltm_nodes:
#   - name: node1.example.com
#     host: 192.168.1.1
#   - name: node2.example.com
#     host: 192.168.1.2

# The list of pools.
# f5_ltm_pools:
#   - name: pool1.example.com
#     lb_method: http_pool
#     monitors: /Common/http
#     monitor_type: and_list

# The list of pools and their members.
# f5_ltm_pool_members:
#   - name: pool1.example.com
#     members:
#       - name: node1.example.com
#         port: 80
#       - name: node2.example.com
#         port: 80

# The list of virtual_servers.
# f5_ltm_virtual_servers:
#   - name: virtual_server1.example.com
#     pool: pool1.example.com
#     destination: 192.168.1.254
#     port: 443
#     enable_vlans: all
#     all_profiles:
#       - http
#       - clientssl
#       - oneconnect
#     snat: Automap
```

## [Requirements](#requirements)

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

## [Status of requirements](#status-of-requirements)

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/f5_ltm.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|alpine|all|
|amazon|all|
|el|7, 8|
|debian|buster, bullseye|
|fedora|all|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.



## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-f5_ltm) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-f5_ltm/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).

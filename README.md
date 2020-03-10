# Cookiecutter template for an OSISM configuration repository

[![Build Status](https://travis-ci.org/osism/cfg-cookiecutter.svg?branch=master)](https://travis-ci.org/osism/cfg-cookiecutter)

## Installation

The `pwgen` tool must be installed.

### Virtualenv

```
$ virtualenv -p python3 .venv
$ source .venv/bin/activate
$ pip3 install -r requirements.txt
```

### Pipenv

```
$ pipenv install
$ pipenv shell
```

## Usage

* http://cookiecutter.readthedocs.io/en/latest/

```
$ cookiecutter ssh://git@github.com:osism/cfg-cookiecutter.git
ceph_fsid [Use a great UUID here]:
ceph_manager_version [latest]:
ceph_network_backend [192.168.80.0/24]:
[...]
```

Alternative:

```
$ git clone ssh://git@github.com:osism/cfg-cookiecutter.git
$ cd cookiecutter
$ cookiecutter .
ceph_fsid [Use a great UUID here]:
ceph_manager_version [latest]:
ceph_network_backend [192.168.80.0/24]:
[...]
```

### User config

* https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html

In ``cookiecutter.yml.sample`` you can find a sample user config.

```
---
default_context:
  ceph_fsid: bb678031-08a6-4e58-9231-b1b3a0a7d2ae
```

```
$ cookiecutter --config-file cookiecutter.yml ssh://git@github.com:osism/cfg-cookiecutter.git
ceph_fsid [bb678031-08a6-4e58-9231-b1b3a0a7d2ae]:
ceph_manager_version [latest]:
ceph_network_backend [192.168.80.0/24]:
[...]
```

## Post-processing

* The password for Ansible Vault encrypted files, ist stored at ``secrets/vaultpass``.
* The password of the generated Keepass file is ``password``. This should be changed.
* If a user config has been used, it can also be stored in the repository
* The contents in the generated ``cfg-customer`` directory is stored in the repository.
  Be careful not to forget dotfiles like ``.gitignore``. The directory itself is not
  stored in the repository.

## Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
    <th>Default</th>
  </tr>
  <tr>
    <td><code>ceph_fsid</code></td>
    <td>The UUID for the Ceph cluster, passed to ceph-ansible</td>
    <td></td>
  </tr>
  <tr>
    <td><code>docker_version</code></td>
    <td>The version of the Docker service. This <code>5:</code> must be prepended starting with version 18.09.</td>
    <td><code>5:19.03.5</code></td>
  </tr>
  <tr>
    <td><code>git_host</code></td>
    <td>The address of the used Git server on which this repository will be stored later</td>
    <td><code>github.com</code></td>
  </tr>
  <tr>
    <td><code>ceph_manager_version</code></td>
    <td>The version of the ceph-ansible container</td>
    <td><code>latest</code></td>
  </tr>
  <tr>
    <td><code>kolla_manager_version</code></td>
    <td>The version of the kolla-ansible container</td>
    <td><code>latest</code></td>
  </tr>
  <tr>
    <td><code>osism_manager_version</code></td>
    <td>The version of the osism-ansible container</td>
    <td><code>latest</code></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

## License

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0.

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author information

This cookiecutter was created by [Betacloud Solutions GmbH](https://www.betacloud-solutions.de).
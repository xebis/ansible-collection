# Ansible Collection

This Ansible collection provides a set of roles designed for configuring Kubuntu desktop and Ubuntu server environments.

## Features

### Roles

| Role                                                                 | Description                                                                                                                                | Dependencies                   |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------ |
| [xebis.ansible.apt](roles/apt/README.md)                             | Deb package updates and upgrades using the apt package manager. Can optionally clean up unused packages and reboot the system if required. | `xebis.ansible.system`         |
| [`xebis.ansible.coding_projects`](roles/coding_projects/README.md)   | Creates and clones coding projects to `~/Projects`                                                                                         | `xebis.ansible.apt`            |
| [xebis.ansible.grub](roles/grub/README.md)                           | GRUB menu configuration.                                                                                                                   |                                |
| `xebis.ansible.fail2ban`                                             | Fail2ban IPS                                                                                                                               | `xebis.ansible.apt`            |
| `xebis.ansible.google_chrome`                                        | Google Chrome (Stable)                                                                                                                     | `xebis.ansible.apt`            |
| [xebis.ansible.nftables_firewall](roles/nftables_firewall/README.md) | nftables firewall                                                                                                                          | `xebis.ansible.apt`            |
| `xebis.ansible.obsidian`                                             | Obsidian                                                                                                                                   | `xebis.ansible.snapd`          |
| `xebis.ansible.openssh_client`                                       | Installs OpenSSH client and generates SSH key pair.                                                                                        | `xebis.ansible.apt`            |
| `xebis.ansible.openssh_server`                                       | Installs OpenSSH server and provides `Restart ssh` handler.                                                                                | `xebis.ansible.apt`            |
| `xebis.ansible.snapd`                                                | Snap daemon                                                                                                                                | `xebis.ansible.apt`            |
| [xebis.ansible.system](roles/system/README.md)                       | System-related tasks such as reboot handler or reboot when required handler.                                                               |                                |
| [xebis.ansible.tmpfs](roles/tmpfs/README.md)                         | Sets to mount directories as tmpfs during startup.                                                                                         | `xebis.ansible.system`         |
| [`xebis.ansible.users`](roles/users/README.md)                       | Ansible role for managing system users.                                                                                                    | `xebis.ansible.openssh_server` |
| `xebis.ansible.visual_studio_code`                                   | Microsoft Visual Studio Code (Stable)                                                                                                      | `xebis.ansible.apt`            |

## Installation and Configuration

Add to `requirements.yaml`:

```yaml
---
collections:
  - name: git+https://github.com/xebis/ansible-collection.git,main
```

Install dependencies:

```shell
ansible-galaxy collection install -r requirements.yaml
```

## Usage

Create an Ansible playbook:

```yaml
---
- hosts: all
  roles:
    - role: xebis.ansible.apt
      vars:
        autoclean: true
        autoremove: true
        cache_valid_time: 3600
        purge: true
        upgrade: "full"
```

Refer to the example playbook [test.yaml](test.yaml) for additional inspiration.

Run the Ansible playbook:

```shell
ansible-playbook -i localhost, playbook.yaml
```

## Contributing

### Development

```shell
GALAXY_BUILD_OUTPUT=$(ansible-galaxy collection build --force)
ansible-galaxy collection install --force "${GALAXY_BUILD_OUTPUT##* }"

ansible-playbook test.yaml -i localhost, -kK
```

## Credits and Acknowledgments

- Martin Bružina - Author

## Copyright and Licensing

- MIT License  
  Copyright © 2025 Martin Bružina

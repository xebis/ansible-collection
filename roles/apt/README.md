# Xebis.Ansible.Apt

Deb package updates and upgrades using the apt package manager. Can optionally clean up unused packages and reboot the system if required.

## Tasks

- Updates the APT package cache.
- Upgrades installed packages based on the upgrade variable.
- Performs system cleanup if autoclean, autoremove, or purge are enabled.
- Reboots the system if it is required after upgrades.

Example play, equivalent to `apt update && apt full-upgrade -y && apt autoremove -y --purge && apt autoclean -y`:

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

## Variables

- `autoclean` [boolean]
  - Removes outdated packages from the local cache.
  - Default [ansible.builtin.apt module parameter autoclean](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html#parameter-autoclean)
- `autoremove` [boolean]
  - Removes unnecessary packages automatically.
  - Default [ansible.builtin.apt module parameter autoremove](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html#parameter-autoremove)
- `cache_valid_time` [seconds]
  - Defines how long (in seconds) the APT cache is considered valid.
  - Default [ansible.builtin.apt module parameter cache_valid_time](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html#parameter-cache_valid_time)
- `purge` [boolean]
  - Autoremove removes packages along with their configuration files.
  - Default [ansible.builtin.apt module parameter purge](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html#parameter-purge)
- `upgrade` [`yes`, `safe`, `no`, `full`, `dist`]
  - Defines the upgrade mode: "yes", "safe", "full", or "dist".
  - Default [ansible.builtin.apt module parameter upgrade](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html#parameter-upgrade)

## Handlers

- `Upgrade deb packages`
  - Upgrades installed packages when the upgrade variable is set to "yes", "safe", "full", or "dist".
- `Update deb packages`
  - Updates apt cache

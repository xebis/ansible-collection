# Xebis.Ansible.System

System-related tasks such as reboot handler or reboot when required handler.

## Variables

- `reboot_timeout` [seconds]
  - Timeout (in seconds) for the system to reboot and become accessible again.
  - Default [ansible.builtin.reboot module parameter reboot_timeout](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/reboot_module.html#parameter-reboot_timeout)

## Handlers

- `Reboot system when required`
  - Checks for the existence of `/var/run/reboot-required`.
  - If the file is found, the system is rebooted.
- `Reboot system`
  - Reboots a system when called.

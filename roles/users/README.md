# Xebis.Ansible.Users

Ansible role for managing system users.

## Tasks

- Create users and user groups
- Grant admin (sudo) access
- Manage SSH keys
- Fine tune SSH authentication settings

```yaml
---
- hosts: all
  roles:
    - role: xebis.ansible.users
      vars:
        passwordless_sudo: true
        ssh_password_login: false
        users:
          - user: example
            admin: true
            ssh_keys_urls:
              - https://github.com/example.keys
```

## Variables

- `ssh_password_login` [boolean]
  - Enables or disables password-based SSH authentication.
  - Default `true`
- `passwordless_sudo` [boolean]
  - Grants sudo privileges without a password when set to true.
  - Default `false`
- `users` [list]
  - List of users to be created. See structure below.
  - Default `[]`.
  - The structure:
    - `user` [string]
      - Username.
      - Required parameter.
    - `admin` [boolean]
      - Adds user to the `sudo` group.
      - Default `false`
    - `ssh_keys` [list]
      - List of SSH public keys for the user.
      - Default `[]`
    - `ssh_keys_urls` [list]
      - URLs pointing to SSH public keys (e.g., GitHub keys).
      - Default `[]`

## Handlers

- `Disable password SSH login`
  - When `ssh_password_login` is set to `false` disables password SSH login, only SSH keys are allowed.

# Xebis.Ansible.Visual_Studio_Code

Ansible role for managing Visual Studio Code.

## Tasks

- Install Visual StudioCode
- Install Visual Studio Code extensions

```yaml
---
- hosts: all
  roles:
    - role: xebis.ansible.visual_studio_code
      vars:
        extensions:
          - davidanson.vscode-markdownlint
```

## Variables

- `extensions` [list]
  - List of extensions installed.
  - Default `[]`

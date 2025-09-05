# Xebis.Ansible.Coding_Projects

Creates and clones coding projects to `~/Projects`.

## Tasks

- Installs `git`
- Sets git user and email
- Creates `~/Projects` directory and subdirectory for each _owner_
- Adds GitHub.com fingerprints to SSH known hosts
- Clones all repositories (only if not already cloned)

Example play:

```yaml
---
- hosts: all
  roles:
    - role: xebis.ansible.coding_projects
      vars:
        repositories:
          - owner: xebis
            name: ansible-collection
```

## Variables

- `repositories` \[[{owner, name}, ...]]
  - Repositories to clone. Owner and name have to be valid GitHub owner and repository and the repository has to be initialized.

# Ansible Collection

A collection of Ansible roles.

## Features

### Roles

| Role              | Description | Documentation      |
| ----------------- | ----------- | ------------------ |
| [apt](roles/apt/) | Apt         | Updates apt cache. |

## Contributing

### Development

```shell
GALAXY_BUILD_OUTPUT=$(ansible-galaxy collection build --force)
ansible-galaxy collection install --force "${GALAXY_BUILD_OUTPUT##* }"

ansible-playbook local.yaml -i localhost,
```

## Credits and Acknowledgments

- Martin Bružina - Author

## Copyright and Licensing

- MIT License  
  Copyright © 2025 Martin Bružina

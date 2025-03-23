# Ansible Collection

This Ansible collection provides a set of roles designed for configuring Kubuntu desktop and Ubuntu server environments.

## Features

### Roles

| Role                                           | Description                                                                                                                                | Dependencies           |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------- |
| [xebis.ansible.apt](roles/apt/README.md)       | Deb package updates and upgrades using the apt package manager. Can optionally clean up unused packages and reboot the system if required. | `xebis.ansible.system` |
| [xebis.ansible.system](roles/system/README.md) | System-related tasks such as reboot handler or reboot when required handler.                                                               |                        |

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

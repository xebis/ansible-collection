# Xebis.Ansible.Nftables_Firewall

`nftables` based extensible firewall chains and rules.

## Tasks

- Installs `nftables` package, creates `/etc/nftables` configuration directory.
- Copies default nftables chains and rules.
- Asynchronously starts and enables nftables service and waits until it is ready.

## Variables

- `nftables_firewall_log_rejected` [boolean]
  - Whether to log rejected packets to syslog.
  - Default `false`

## Handlers

- `Validate and reload nftables firewall`
  - Validates and reloads all `nftables` firewall rules.
- `Reload nftables firewall`
  - Reloads all `nftables` firewall rules. Shouldn't be used without prior nftables configuration check.

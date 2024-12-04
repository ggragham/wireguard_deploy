Base role
=========

Configure basic server setup with firewall rules, security hardening, and essential packages.

Requirements
------------

- [Debian](https://debian.org/) based server.

Role Variables
--------------

```yml
## Essential Environment Variables
DOMAIN_NAME: example.com  # Nginx server domain.
SSH_PORT: 22  # Port for SSH access.
NETWORK_INTERFACE: eth0  # Default network interface.

## Optional Environment Variables
FAIL2BAN_BANTIME: 5m  # Duration for which IPs are banned.
FAIL2BAN_FINDTIME: 3m  # Time window to consider failed login attempts.
FAIL2BAN_MAXRETRY: 5  # Number of allowed failed login attempts before banning IP.
```

Example Playbook
----------------

```yml
  - hosts: servers
    roles:
       - role: base
```

License
-------

GPL

Author Information
------------------

[Grell Gragham](https://github.com/ggragham)

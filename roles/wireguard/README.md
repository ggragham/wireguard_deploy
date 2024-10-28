WireGuard Role
=========

Install and config WireGuard VPN server.

Requirements
------------

- Docker is installed or a Docker Ansible role is applied (see [Docker Installation Guide](https://docs.docker.com/engine/install/)).
- NGINX is installed or an NGINX Ansible role is applied (see [NGINX Installation Guide](https://nginx.org/en/docs/install.html)).
- Authelia is installed or an Authelia Ansible role is applied (optional, for added security features; see [Authelia Installation Guide](https://authelia.com/integration/prologue/get-started/)).

Role Variables
--------------

```yml
DOCKER_SERVICES_NETWORK_NAME: wg-network  # Docker Network name for related services.
WG_DOCKER_IMAGE_VERSION: latest  # WireGuard Docker image version.

WG_PORT: 51820  # The public UDP port of VPN server.
WG_DEFAULT_ADDRESS: 10.8.0.x  # Clients IP address range.
WG_DEFAULT_DNS: 1.1.1.1, 1.0.0.1  # DNS server clients will use.

WG_LANG: en  # WebUI language.
WG_UI_PASSWORD: foobar123  # WebUI Password.
WG_UI_TRAFFIC_STATS: true  # Enable detailed RX / TX client stats in WebUI.
WG_UI_CHART_TYPE: 0 # Type of chart for displaying statistics; 0 Charts disabled, 1 # Line chart, 2 # Area chart, 3  # Bar chart.
```

Dependencies
------------

```yml
dependencies:
  - role: docker
  - role: nginx
  - role: authelia  # Optional.
```

Example Playbook
----------------

```yml
  - hosts: servers
    roles:
       - role: wireguard
```

License
-------

GPL

Author Information
------------------

[Grell Gragham](https://github.com/ggragham)

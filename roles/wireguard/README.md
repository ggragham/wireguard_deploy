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
## External Environment Variables
DOMAIN_NAME: example.com  # Domain name of your server.
DNS_SERVER_INSTALL: true  # Enable or disable DNS Server installation.

## Essential Environment Variables
WG_DOCKER_IMAGE_VERSION: latest  # WireGuard Docker image version.
WG_LANG: en  # WebUI language.
WG_UI_PASSWORD: foobar123  # WebUI Password.
WG_MTU: 1420  # MTU size.

## Optional Environment Variables
WG_PORT: 51820  # The public UDP port of VPN server.
WG_DEFAULT_ADDRESS: 10.8.0.x  # Clients IP address range.
WG_DEFAULT_DNS: 1.1.1.1, 1.0.0.1  # DNS servers for clients (used if DNS role is not installed).
WG_UI_TRAFFIC_STATS: true  # Enable detailed RX / TX client stats in WebUI.
WG_UI_CHART_TYPE: 0 # Type of chart for displaying statistics; 0 Charts disabled, 1 # Line chart, 2 # Area chart, 3  # Bar chart.

## Advanced Environment Variables
## Define extra ports to expose (optional).
## Use the format: - host_port:container_port
WG_ADDITIONAL_PORTS:
  - 1234:1234

## Custom firewall rules to apply before the WireGuard interface is brought up (opional).
## The following rules are provided as example.
WG_PRE_UP_FIREWALL_RULES: |
  iptables -P FORWARD DROP;
  iptables -A FORWARD -i wg0 -d 10.8.0.0/24 -j ACCEPT;
  iptables -t nat -A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE;
  iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 1234 -j DNAT --to-destination 10.8.0.2:1234;

## Add custom commands to run after the WireGuard is up (optional).
# WG_POST_UP:

## Custom firewall rules to apply before the WireGuard interface is brought down (optional).
## The following rules are provided as example.
WG_PRE_DOWN_FIREWALL_RULES: |
  iptables -D FORWARD -i wg0 -d 10.8.0.0/24 -j ACCEPT;
  iptables -t nat -D POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE;
  iptables -D PREROUTING -t nat -i eth0 -p tcp --dport 1234 -j DNAT --to-destination 10.8.0.2:1234;

## Add custom commands to run after the WireGuard is down (optional).
# WG_POST_DOWN:
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

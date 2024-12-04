DNS Role
=========

Install and configure Pi-hole as a DNS server and cloudflared as a DoH provider.

Requirements
------------

- Docker is installed or a Docker Ansible role is applied (see [Docker Installation Guide](https://docs.docker.com/engine/install/)).

Role Variables
--------------

```yml
DNS_SERVER_INSTALL: true  # Enable or disable DNS Server installation.
DNS_DOMAIN: dns.{{ DOMAIN_NAME }}  # URL of the DNS web control panel.
DOCKER_SERVICES_NETWORK_NAME: wg-network  # Docker Network name for related services.
PIHOLE_DOCKER_IMAGE_VERSION: latest  # Pi-hole Docker image version.

PIHOLE_ADMIN_PASSWORD: foobar123  # Password used to login in Pi-hole WebUI.
PIHOLE_TIMEZONE: Etc/UTC  # Timezone for the Pi-hole instance.
PIHOLE_DNSSEC: true  # Enable or disable DNSSEC support.
PIHOLE_QUERY_LOGGING: 'true'  # Toggle query logging.
PIHOLE_CACHE_SIZE: 10000  # DNS cache size.
PIHOLE_WEBUI_BOXED_LAYOUT: boxed  # Web interface layout.
PIHOLE_WEBUI_THEME: default-dark  # Web interface theme.

CLOUDFLARED_DOCKER_IMAGE_VERSION: latest  # Cloudflared Docker image version.
CLOUDFLARED_TIMEZONE: Etc/UTC  # Timezone for the Cloudflared service.
CLOUDFLARED_TUNNEL_DNS_UPSTREAM: https://1.1.1.1/dns-query,https://1.0.0.1/dns-query  # Upstream DoH servers for Cloudflared tunnel.

```

Dependencies
------------

```yml
dependencies:
  - role: docker
```

Example Playbook
----------------

```yml
  - hosts: servers
    roles:
       - role: dns
```

License
-------

GPL

Author Information
------------------

[Grell Gragham](https://github.com/ggragham)


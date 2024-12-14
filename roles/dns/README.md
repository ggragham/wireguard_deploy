DNS Role
=========

Install and configure Pi-hole as a DNS server and cloudflared as a DoH provider.

Requirements
------------

- Docker is installed or a Docker Ansible role is applied (see [Docker Installation Guide](https://docs.docker.com/engine/install/)).

Role Variables
--------------

```yml
## External Environment Variables
DOMAIN_NAME: example.com  # Domain name of your server.
SSL_GEN: auto  # Source of SSL Certificate.
SSL_EMAIL: test@example.com  # Email address used for SSL certificate registration or renewal notifications.

## Essential Environment Variables
PIHOLE_DOCKER_IMAGE_VERSION: latest  # Pi-hole Docker image version.
PIHOLE_TIMEZONE: Etc/UTC  # Timezone for the Pi-hole instance.
PIHOLE_ADMIN_PASSWORD: foobar123  # Password used to login in Pi-hole WebUI.

CLOUDFLARED_DOCKER_IMAGE_VERSION: latest  # Cloudflared Docker image version.
CLOUDFLARED_TIMEZONE: Etc/UTC  # Timezone for the Cloudflared service.
CLOUDFLARED_TUNNEL_DNS_UPSTREAM: https://1.1.1.1/dns-query,https://1.0.0.1/dns-query  # Upstream DoH servers for Cloudflared tunnel.

## Optional Environment Variables
DNS_SERVER_INSTALL: true  # Enable or disable DNS Server installation.
PIHOLE_DNSSEC: true  # Enable or disable DNSSEC support.
PIHOLE_QUERY_LOGGING: 'true'  # Toggle query logging.
PIHOLE_CACHE_SIZE: 10000  # DNS cache size.
PIHOLE_WEBUI_BOXED_LAYOUT: boxed  # Web interface layout.
PIHOLE_WEBUI_THEME: default-dark  # Web interface theme.
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


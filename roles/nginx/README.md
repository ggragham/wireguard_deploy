Nginx role
=========

Install and config webserver.

Requirements
------------

- Docker is installed or a Docker Ansible role is applied (see [Docker Installation Guide](https://docs.docker.com/engine/install/)).

Role Variables
--------------

```yml
## External Environment Variables
DOMAIN_NAME: example.com  # Nginx server domain.

## Essential Environment Variables
NGINX_DOCKER_IMAGE_VERSION: latest  # Nginx Docker image version.
SSL_CERT_NAME: cert.crt  # SSL certificate filename placed in the assets/ directory.
SSL_KEY_NAME: cert.key  # SSL Key filename placed in the assets/ directory.
DH_NAME: dhparam.pem  # DH key filename placed in the assets/ directory.

## Optional Environment Variables
DOCKER_SERVICES_NETWORK_NAME: wg-network  # Docker Network name for related services.
SSL_CERT_PATH: ./assets/{{ SSL_CERT_NAME }}  # SSL Cert path.
SSL_KEY_PATH: ./assets/{{ SSL_KEY_NAME }}  # SSL Key path.
DH_PATH: ./assets/{{ DH_NAME }}  # DH key path.
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
       - role: nginx
```

License
-------

GPL

Author Information
------------------

[Grell Gragham](https://github.com/ggragham)

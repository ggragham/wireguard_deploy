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
TIMEZONE: UTC  # Set your server's timezone.

## Essential Environment Variables
NGINX_DOCKER_IMAGE_VERSION: latest  # Nginx Docker image version.

## Optional Environment Variables
# Determines the source of the SSL certificate.
# Options: 'auto' or 'manual'
# 'auto' - Obtain the certificate automatically through Let's Encrypt.
# 'manual' - Manually provide your SSL certificate and place it in the assets directory.
# In this case, specify the certificate file names using the variables:
# SSL_CERT_NAME for the certificate,
# SSL_KEY_NAME for the private key,
SSL_GEN: auto
SSL_EMAIL: test@example.com  # Email address used for SSL certificate registration or renewal notifications.
SSL_DH_NAME: dhparam.pem  # DH key filename placed in the assets/ directory.
SSL_DH_KEY_SIZE: 2048  # Key size for the DH parameters.

# !! THIS CONFIGURATION IS USED WHEN 'SSL_GEN' SET TO 'manual' !!
SSL_CERT_NAME: cert.crt  # SSL certificate filename placed in the assets/ directory.
SSL_KEY_NAME: cert.key  # SSL Key filename placed in the assets/ directory.
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

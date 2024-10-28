Authelia Role
=========

Install and config Authelia authentication service.

Requirements
------------

- Docker is installed or a Docker Ansible role is applied (see [Docker Installation Guide](https://docs.docker.com/engine/install/)).
- NGINX is installed or an NGINX Ansible role is applied (see [NGINX Installation Guide](https://nginx.org/en/docs/install.html)).

Role Variables
--------------

```yml
DOMAIN_NAME: example.com  # Nginx server domain.
AUTHELIA_INSTALL: true  # Enable or disable Authelia installation.
AUTHELIA_DOCKER_IMAGE_VERSION: latest  # Authelia Docker image version.

AUTHELIA_THEME: dark  # light, dark, grey, auto.
AUTHELIA_LOG_FORMAT: text  # text, json.
AUTHELIA_TOTP_ISSUER: authelia.com  # Name displayed in the Authenticator application.
AUTHELIA_TOTP_ALGORITHM: sha1  # sha1, sha256, sha512.
AUTHELIA_TOTP_DIGITS: 6  # 6, 8.
AUTHELIA_TOTP_PERIOD: 30  # period in seconds a totp is valid for.
AUTHELIA_JWT_SECRET: example_of_jwt_secret  # secret key used to sign and verify the JWT.
AUTHELIA_NTP_PROVIDER: time.cloudflare.com  # address of the NTP server.
AUTHELIA_NTP_DISABLE_FAILURE: 'false'  # true, false.
AUTHELIA_SESSION_SECRET: example_of_session_secret  # secret to encrypt the session data.
AUTHELIA_SESSION_DOMAIN: '{{ DOMAIN_NAME }}'  # The domain to protect.
AUTHELIA_SESSION_URL: auth.{{ DOMAIN_NAME }}  # URI of the portal to redirect users.
AUTHELIA_STORAGE_ENCRYTPTION_KEY: example_of_storage_encryption_key  # ecryption key used to encrypt data in db.

AUTHELIA_DOMAIN_LIST:  # List of domains to protect by Authelia.
  - '{{ DOMAIN_NAME }}'

AUTHELIA_USERNAME: user  # Authelia auth username.
AUTHELIA_PASSWORD: password  # Authelia auth password.
```

Note
----
To generate JWT tokens or any keys and secrets, you can use the following command:

```bash
head /dev/random | tr -dc 'A-Za-z0-9_' | head -c 32
```

Dependencies
------------

```yml
dependencies:
  - role: docker
  - role: nginx
```

Example Playbook
----------------

```yml
  - hosts: servers
    roles:
       - role: authelia
```

License
-------

GPL

Author Information
------------------

[Grell Gragham](https://github.com/ggragham)

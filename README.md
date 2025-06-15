<h1 align="center">WireGuard VPN Server Deployment</h1>

<p>
  <img src="https://img.shields.io/github/last-commit/ggragham/wireguard_deploy" alt="last commit">
  <img src="https://img.shields.io/github/repo-size/ggragham/wireguard_deploy" alt="repo size">
  <a href="https://opensource.org/license/GPL-3.0"><img src="https://img.shields.io/github/license/ggragham/wireguard_deploy" alt="license"></a>
</p>

Deploy Your Own Secure WireGuard VPN Server the Easy Way.

## Table of contents
- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Important Note](#important-note)
- [Additional Resources](#additional-resources)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

## Overview
A deployment of a secure VPN service that provide access to your homelabs, smart homes, servers, and can also be used for safe web browsing (assuming trust in the server hosting the VPN). 
Deployment is automated using Ansible, with configurations managed via `vars.yml`. 
All components are deployed using Docker images.

## Features
- **Secure Access**: Safely connect to your home lab's infrastructure from remote locations, ensuring your data remains private.
- **Dockerized Components**: All services are run in isolated Docker containers for improved security and easier management.
- **Custom Domain Names**: Pi-hole provides DNS resolution within your network, allowing for friendly domain names instead of remembering IP addresses.
- **Ad Blocking**: Pi-hole also serves as an ad blocker, preventing intrusive advertisements from being served within your network.
- **Two-Factor Authentication (2FA)**: Integration with Authelia for enhanced security during user authentication.
- **Hardened System Configuration**: The deployment includes hardening configurations for the base system, adding an extra layer of security.
- **Secure Browsing**: The VPN server can be utilized for secure web surfing (provided you trust the server provider).
- **Simple Ansible Configuration**: Easily manageable configurations through `vars.yml` for a quick and easy setup.

## Prerequisites
- A clean installation of the latest version of **Debian** or **Fedora** Linux.
- **Ansible** installed on the control node.
- SSH access to the server with **sudo** privileges.

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/ggragham/wireguard_deploy.git
cd wireguard_deploy
```

### 2. Install Dependencies
Install the Ansible roles listed in the `requirements.yml` file:
```bash
ansible-galaxy role install --force --role-file requirements.yml
```
The `--force` option reinstalls roles even if they are already installed, preventing version conflicts.

### 3. Create Configuration File
Copy the template configuration file to create your own:
```bash
cp default.vars.yml vars.yml
```

### 4. Configuration
Modify the `vars.yml` file to set your desired configurations. Make sure to specify all essential parameters like domain name, network settings, user credentials, etc.

### 5. Deploy
Run the Ansible playbook:
```bash
ansible-playbook playbook.yml
```

## Important Note
**Before using the scripts and/or playbooks in this repository, ensure you have created a backup of your data and configurations. The author of this repository assumes no responsibility for any data loss or system issues that may arise from using these scripts or playbooks. Use them at your own risk.**

## Additional Resources
For further guidance and detailed information, refer to the following resources:
* [WireGuard Official Documentation](https://www.wireguard.com/)
* [wg-easy GitHub Repository](https://github.com/wg-easy/wg-easy)
* [Authelia Documentation](https://www.authelia.com/configuration/)
* [Pi-hole Documentation](https://docs.pi-hole.net/)
* [Nginx Official Documentation](https://nginx.org/en/docs/)
* [Docker Documentation](https://docs.docker.com/)
* [Ansible Documentation](https://docs.ansible.com/)

## Contributing
If you would like to contribute to this project, feel free to submit a pull request or open an issue for discussion. Contributions are welcome!

## Author
This project was created by [Grell Gragham](https://github.com/ggragham).

## License
This software is published under the [GPL-3.0 License](https://opensource.org/license/GPL-3.0).

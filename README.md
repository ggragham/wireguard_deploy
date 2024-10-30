#  WireGuard VPN Server Deployment

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
This project automates the deployment of a secure WireGuard VPN server using **wg-easy**. The Ansible playbook installs Docker, configures essential firewall rules, and integrates Nginx and Authelia for enhanced security, providing a streamlined setup for a reliable VPN environment.

## Features
- **WireGuard VPN**: Quick setup and configuration using the **wg-easy** Docker image.
- **User-Friendly Web Interface**: Manage **VPN** users and settings through an intuitive interface.
- **Nginx Reverse Proxy**: Secure access to the **WireGuard** web interface via **Nginx**.
- **Optional 2FA with Authelia**: Enable two-factor authentication for enhanced security.
- **Complete Automation with Ansible**: Install **Docker**, configure firewall rules, and set security parameters for reliable **VPN** operation.

## Prerequisites
* Debian Linux server.
* Ansible installed on the control node.
* SSH access to the server with sudo privileges.

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/ggragham/wg_deploy.git
cd wg_deploy
```

### 2. Create Configuration File
Copy the template configuration file to create your own:
```bash
cp default.vars.yml vars.yml
```

### 3. Configuration
Modify the `vars.yml` file to set your desired configurations. Make sure to specify all required parameters like domain names, user credentials, and network settings.

### 4. Deploy
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
* [Nginx Official Documentation](https://nginx.org/en/docs/)
* [Docker Documentation](https://docs.docker.com/)
* [Ansible Documentation](https://docs.ansible.com/)

## Contributing
If you would like to contribute to this project, feel free to submit a pull request or open an issue for discussion. Contributions are welcome!

## Author
This project was created by [Grell Gragham](https://github.com/ggragham).

## License
This software is published under the [GPL-3.0 License](https://opensource.org/license/GPL-3.0).

This section guides you through installing Carbonio on a supported Linux environment.  
We cover preparation, prerequisites, and a step-by-step installation procedure.

Before starting, ensure you understand the [Architecture & Components](../arch/arch.md) of Carbonio.

---

## System Requirements

!!! info "Minimum System Requirements"
    - **CPU:** 4 cores or more  
    - **RAM:** 8 GB minimum (16+ GB recommended)  
    - **Storage:** SSD recommended; minimum 100 GB free space  
    - **OS:** Ubuntu 20.04 LTS or 22.04 LTS (64-bit)  
    - **Network:** Static IP address and proper DNS resolution

!!! info "Recommended Production Setup"
    - **Multi-node deployment** for large organizations  
    - **Backup system** in place before going live  
    - **Secure DNS** and firewall configuration  
    - **TLS certificates** for HTTPS and mail services

---

## Pre-Installation Steps

!!! info "1. Update the System"
    Run:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```

!!! info "2. Configure Hostname and DNS"
    Ensure `/etc/hostname` and `/etc/hosts` match your FQDN:
    ```
    192.168.1.100 mail.example.com mail
    ```

!!! info "3. Set Static IP"
    Configure your network settings to use a static IP. Avoid DHCP for production systems.

!!! info "4. Open Required Ports"
    Allow ports like 80, 443, 25, 587, 993, 7071:
    ```bash
    sudo ufw allow 80,443,25,587,993,7071/tcp
    ```

---

## Installation Process

!!! info "1. Add Carbonio Repositories"
    Follow the official Zextras instructions to add the appropriate repository and GPG keys:
    ```bash
    wget -qO - https://repo.zextras.io/pgp-key.asc | sudo apt-key add -
    echo "deb https://repo.zextras.io/apt/ stable main" | sudo tee /etc/apt/sources.list.d/zextras.list
    sudo apt update
    ```

!!! info "2. Install Carbonio Packages"
    Install the core Carbonio components:
    ```bash
    sudo apt install carbonio-core carbonio-mail carbonio-webui carbonio-admin
    ```

!!! info "3. Run the Installer"
    After package installation, the system will prompt for the interactive setup:
    - Configure domain
    - Set admin password
    - Choose services to install

!!! info "4. Finish and Reboot"
    Reboot the server to finalize service configuration:
    ```bash
    sudo reboot
    ```

---

## Post-Installation Checklist

!!! info "✅ Verify Services"
    Ensure that key services are active:
    ```bash
    sudo systemctl status carbonio-*
    ```

!!! info "✅ Access Web Interface"
    Open your browser and go to:  
    `https://your-server:6071` (Admin Panel)  
    or  
    `https://your-server` (Webmail)

!!! info "✅ Set DNS and MX Records"
    Configure public DNS and MX records to allow incoming and outgoing mail.

!!! info "✅ Obtain TLS Certificates"
    Use **Let's Encrypt** or your internal CA:
    ```bash
    sudo certbot certonly --standalone -d mail.example.com
    ```

---

## Summary

You now have a working Carbonio installation.  
Next, move to [Post-Installation Configuration](../postinst/postinst.md) to fine-tune your system and begin adding users and domains.


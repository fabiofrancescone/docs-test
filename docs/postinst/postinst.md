After successfully installing Carbonio, it’s essential to perform some post-installation steps to ensure security, usability, and performance. This section walks through account setup, domain configuration, backups, and additional tuning.

---

## Admin Account & Access

!!! info "✅ Change Default Admin Password"
    For security, change the password of the `admin` account:
    ```bash
    carbonio prov setpassword admin@example.com NEW_PASSWORD
    ```

!!! info "✅ Set Up Additional Admins (Optional)"
    You can delegate admin rights to other users:
    ```bash
    carbonio admin create john@example.com
    ```

!!! info "✅ Secure Web Access"
    - Disable access to the admin console from the public internet if not required  
    - Use HTTPS with valid TLS certificates  

---

## Domain & User Configuration

!!! info "✅ Add Your Domain"
    Use the CLI or Admin UI to add domains:
    ```bash
    carbonio prov createDomain yourdomain.com
    ```

!!! info "✅ Create User Accounts"
    Create users for your domain:
    ```bash
    carbonio prov createAccount alice@yourdomain.com password123
    ```

!!! info "✅ Configure Mail Routing"
    - Set MX records to route mail to your Carbonio instance  
    - Add SPF, DKIM, and DMARC records for email authenticity

---

## System Hardening

!!! info "🔒 Enable Fail2Ban (Optional)"
    Protect against brute-force attacks:
    ```bash
    sudo apt install fail2ban
    ```

!!! info "🔒 Configure a Firewall"
    Ensure only required ports are open:
    ```bash
    sudo ufw allow ssh
    sudo ufw allow 80,443,25,587,993,7071/tcp
    sudo ufw enable
    ```

!!! info "🔒 Enable Secure Admin Panel Access"
    Restrict access by IP or use VPN to access admin interface (`:6071`).

---

## Backup Configuration

!!! info "📦 Enable Carbonio Backup"
    If you are using Carbonio CE, configure Zextras Backup:
    ```bash
    carbonio backup enable
    carbonio backup setProperty backupPath /opt/zextras/backup
    ```

!!! info "📅 Schedule Regular Backups"
    Use cron or systemd timers to run periodic backup exports.

---

## Monitoring & Maintenance

!!! info "🧭 Enable Logs & Alerts"
    - Check logs in `/opt/zextras/log`  
    - Set up email alerts for system failures or disk space issues

!!! info "🩺 Health Checks"
    Use:
    ```bash
    carbonio healthcheck
    ```

!!! info "📊 Add Monitoring Tools"
    - Integrate with Prometheus, Grafana, or Nagios  
    - Enable SNMP if required

---

## Summary

Your Carbonio instance is now secure, configured, and ready for production use.  
From here, you can explore:

- [User Management](../sysadm/users/users.md)
- [Backup & Restore](../sysadm/backup/backup.md)
- [Mail Services](../sysadm/mail/mail.md)
- [Mobile Sync & Collaboration Tools](../sysadm/collaboration/collaboration.md)

For advanced topics, continue to the [Advanced Configuration](../advanced/advanced.md) section.


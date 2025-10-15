
# Advanced Administration

This section covers advanced administrative tasks for Carbonio, as described in the [official documentation](https://docs.zextras.com/carbonio/html/admincli/advancedadmin.html).

## Managing Services

You can manage system services using the `carbonio` CLI.

### List Services
```bash
carbonio service list
```

### Start/Stop/Restart Services
```bash
carbonio service start <service>
carbonio service stop <service>
carbonio service restart <service>
```

## Logging Configuration

Modify logging levels for troubleshooting and diagnostics.

### View Current Log Level
```bash
carbonio log level get <module>
```

### Set Log Level
```bash
carbonio log level set <module> <level>
```

## Delegated Administration

Carbonio supports delegation of admin rights.

### Grant Admin Rights
```bash
carbonio prov grantRight <grantee> <right>
```

### List Admin Rights
```bash
carbonio prov getRights <grantee>
```

## Feature Toggles

Toggle features for testing or production environments.

### Enable Feature
```bash
carbonio config set feature.<feature_name> true
```

### Disable Feature
```bash
carbonio config set feature.<feature_name> false
```

## Troubleshooting Tools

Useful commands to debug and analyze issues.

### Check Mail Queues
```bash
carbonio mail queue list
```

### Force Log Rotation
```bash
logrotate -f /etc/logrotate.d/carbonio
```

---

For full details, refer to the [Advanced Administration section](https://docs.zextras.com/carbonio/html/admincli/advancedadmin.html) in the official documentation.
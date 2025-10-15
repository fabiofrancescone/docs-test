# Migration

This section provides guidance on migrating to Carbonio, including preparation, steps, and tools used during the process.

## Overview

Carbonio provides a structured and reliable path for migrating from various platforms to ensure business continuity and data integrity.

## Prerequisites

Before initiating a migration to Carbonio, ensure the following:
- A working Carbonio installation.
- Administrative access to both the source and target systems.
- Adequate storage and system resources.
- Full backup of the source environment.

## Migration Tools

Carbonio provides a set of command-line tools for managing migration:
- `carbonio-migrate` — Primary tool to initiate and manage migrations.
- Log and configuration files stored in `/opt/zextras/carbonio/log` and `/opt/zextras/conf`.

## Supported Migration Types

Carbonio supports migration from:
- Zimbra Open Source and Network Edition
- IMAP servers (generic)
- Exchange/Office365 (via external tools)

## Migration Steps

### 1. Install and Configure

Ensure Carbonio is correctly installed and updated. Configure necessary domains, accounts, and services.

### 2. Prepare Source System

Gather the following from the source:
- User data and mailbox formats
- Domain and account structures
- Authentication methods

### 3. Data Import

Use `carbonio-migrate` with appropriate flags:
```bash
carbonio-migrate --source <source_type> --host <source_host> --user <username> ...
```

Refer to the tool's documentation for complete options.

### 4. Validation and Testing

Once data is migrated:
- Validate mailbox data and permissions
- Test email delivery and functionality
- Confirm calendar and contact syncing

## Troubleshooting

Logs are located at:
- `/opt/zextras/log/carbonio-migrate.log`
- `/var/log/zextras/`

Common issues include:
- Authentication failures
- Incomplete data transfer
- Format compatibility problems

Check logs and re-run the migration for affected accounts if necessary.

## Additional Resources

- [Carbonio Administration Guide](https://docs.zextras.com/carbonio/html/admincli/)
- [Support Portal](https://community.zextras.com)

# System Administration via CLI

This guide provides an overview of essential system administration tasks in Carbonio using the Command Line Interface (CLI).

## Accessing the Carbonio CLI

To execute Carbonio commands, switch to the `zextras` user:

```bash
su - zextras
```

You can run commands directly:

```bash
carbonio backup doSmartScan start
```

Or enter the interactive Carbonio Shell:

```bash
carbonio
```

Within the shell, the prompt changes to `carbonio>`, allowing command execution with features like auto-completion and command history.

## Command Structure

A typical Carbonio command follows this structure:

```bash
carbonio [options] <module> <command> [parameters]
```

- **Options**: Modifiers like `--progress`, `--json`, or `--host` to control command behavior.
- **Module**: The component of Carbonio you're interacting with (e.g., `admin`, `backup`).
- **Command**: The specific action to perform within the module.
- **Parameters**: Additional data required by the command.

For example, to set an account limit for a domain:

```bash
carbonio admin setDomainSettings example.com account_limit 1000
```

## Managing Features

You can enable or disable specific features at the Class of Service (COS) or account level.

To check if the Files component is enabled for the default COS:

```bash
carbonio prov getCos default carbonioFeatureFilesEnabled
```

To disable the Mails App for a specific account:

```bash
carbonio prov modifyAccount johnsmith@acme.example carbonioFeatureMailsAppEnabled FALSE
```

## Certificate Management

Renewing a Let's Encrypt certificate can be done manually or automatically.

To renew manually:

```bash
carbonio certbot renew
```

Ensure that the domain's DNS records are correctly configured and that the server is accessible over the internet.

## Domain Disclaimers

To configure a domain disclaimer:

```bash
carbonio prov modifyDomain example.com zimbraDomainDisclaimerText "Your disclaimer text here."
```

To enable the disclaimer:

```bash
carbonio prov modifyDomain example.com zimbraDomainDisclaimerEnabled TRUE
```

## Analytics Management

Enable or disable analytics at the COS or account level.

To disable analytics for a COS:

```bash
carbonio prov modifyCos default carbonioFeatureAnalyticsEnabled FALSE
```

## Network Configuration

To change the private IP address of a Carbonio server:

1. Update the server's network configuration files.
2. Modify the `/etc/hosts` file to reflect the new IP.
3. Restart network services:

    ```bash
    systemctl restart network
    ```

4. Update Carbonio's configuration:

    ```bash
    carbonio prov modifyServer server.example.com zimbraIPMode ipv4
    carbonio prov modifyServer server.example.com zimbraServiceEnabled ldap
    ```

## Hostname Changes

To change the hostname of a Carbonio server:

1. Update the system's hostname:

    ```bash
    hostnamectl set-hostname newhostname.example.com
    ```

2. Modify the `/etc/hosts` file accordingly.
3. Update Carbonio's configuration:

    ```bash
    carbonio prov modifyServer oldhostname.example.com zimbraServerHostname newhostname.example.com
    ```

## Node Removal

To remove a node from the Carbonio infrastructure:

1. Decommission services on the node.
2. Remove the server from Carbonio's configuration:

    ```bash
    carbonio prov deleteServer server.example.com
    ```

3. Clean up any remaining data or configurations related to the node.

## System Locale

To set the system locale:

```bash
localectl set-locale LANG=en_US.UTF-8
```

Replace `en_US.UTF-8` with your desired locale.

---

For a comprehensive list of commands and detailed explanations, refer to the [Carbonio Admin CLI documentation](https://docs.zextras.com/carbonio/html/admincli/administration.html).
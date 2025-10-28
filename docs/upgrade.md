# Upgrade

This section describes the procedures to upgrade **Carbonio** to the latest release.

Carbonio does not have a standalone installer. When new versions are released, the Zextras repositories are updated, and the packages are available for installation alongside regular system updates. Therefore, upgrading Carbonio is performed as part of the system upgrade process.

The upgrade can be performed **manually** or using **Ansible**. The Ansible procedure works even if Carbonio was installed manually, provided that the inventory file is properly configured.

> **Important:** Before starting any upgrade procedure, it is strongly recommended to take a snapshot of all nodes and back up your data.


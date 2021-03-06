---
title: Upgrade NetQ CLI
author: Cumulus Networks
weight: 147
aliases:
 - /display/NETQ/Upgrade+NetQ
 - /pages/viewpage.action?pageId=12320951
product: Cumulus NetQ
version: 2.4
imgData: cumulus-netq
siteSlug: cumulus-netq
toc: 4
---
While it is not required to upgrade the NetQ CLI on your monitored switches and hosts when you upgrade to NetQ 2.4.1, doing so gives you access to new features and important bug fixes. Refer to the {{<exlink url="https://support.cumulusnetworks.com/hc/en-us/articles/360041040413" text="release notes">}} for details.

To upgrade the NetQ CLI:

1. Log in to your switch or host.

2. Update and install the new NetQ debian package.

    <details><summary>For Switches and Hosts Running Cumulus Linux or Ubuntu</summary>

    ```
    sudo apt-get update
    sudo apt-get install -y netq-apps
    ```

    </details>
    <details><summary>For Hosts Running RHEL or CentOS</summary>

    ```
    sudo yum update
    sudo yum install netq-apps
    ```

    </details>

3. Restart the CLI.

```
netq config restart cli
```

To complete the upgrade, refer to the relevant configuration topic:

- [Configure the NetQ CLI on a Cumulus Linux Switch](../../Install-NetQ/Install-NetQ-CLI/Install-NetQ-CLI-on-CL/#configure-the-netq-cli-on-a-cumulus-linux-switch)
- [Configure the NetQ CLI on an Ubuntu Server](../../Install-NetQ/Install-NetQ-CLI/Install-NetQ-CLI-on-Ubuntu/#configure-the-netq-cli-on-an-ubuntu-server)
- [Configure the NetQ CLI on a RHEL or CentOS Server](../../Install-NetQ/Install-NetQ-CLI/Install-NetQ-CLI-on-RHEL/#configure-the-netq-cli-on-a-rhel-or-centos-server)

<!-- - {{<link title="Configure the NetQ CLI on a Cumulus Linux Switch">}}
- {{<link title="Configure the NetQ CLI on an Ubuntu Server">}}
- {{<link title="Configure the NetQ CLI on a RHEL or CentOS Server">}} -->

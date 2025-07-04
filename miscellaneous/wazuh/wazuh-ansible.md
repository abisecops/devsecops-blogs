---
hidden: true
---

# wazuh-ansible

I found there is proper official repo for wazuh with ansible playbook. Let us configure with official documentation.

Prerequisites

To demonstrate how we can provision and configure multiple Wazuh endpoints with Ansible, we use the following infrastructure.

* A Red Hat 9.5.0 endpoint with the Wazuh central components (Wazuh server, Wazuh indexer, and Wazuh dashboard) installed. Follow the [Quickstart guide](https://documentation.wazuh.com/current/quickstart.html) to install Wazuh 4.7.0.
* A Red Hat 9.5.0 endpoint to install Ansible.
* An Ubuntu 23.04 endpoint to deploy and configure the [Wazuh Linux agent 4.7.0](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html).&#x20;
* A Windows 11 endpoint to deploy and configure the [Wazuh Windows agent 4.7.0](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html).

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

The following table shows the parameters we used to demonstrate our deployment.

| **Endpoints** | **Purpose**  | **IP address** | **Software** |
| ------------- | ------------ | -------------- | ------------ |
| Red Hat 9.5.0 | Control node | 172.16.1.11    | Ansible      |
| Ubuntu 23.04  | Managed node | 172.16.1.13    | SSH          |
| Windows 11    | Managed node | 172.16.1.12    | WinRM        |

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

_Let's create and use the non-root user account to manage all the endpoints._

_username :**ansible**, and password: **`pass123`**_



#### Setting up Ansible for configuration management

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

\
Set up Ansible for configuration management.

Installing ansible&#x20;

1. Update and install the CentOS 7 EPEL repository:

```bash
sudo yum update -y
sudo yum install epel-release -y
```

2. Install the latest version of Ansible:

```bash
sudo yum install ansible -y
```

3. Ansible version

```bash
ansible --version
```

\



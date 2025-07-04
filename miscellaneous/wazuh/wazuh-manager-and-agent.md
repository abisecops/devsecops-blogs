# Wazuh manager and agent



## Ansible Project

This repository contains Ansible playbooks, inventory, and scripts designed to automate the installation and configuration of Wazuh (Manager and Agent). This project simplifies setting up and managing these components in your environment.

Get the repo:&#x20;

{% @github-files/github-code-block %}

```
git clone https://github.com/whoami-anoint/wazu/
cd ansible/
```

### Directory Structure

```
ansible/
├── inventory
│   └── hosts                # Inventory file listing target systems
├── main.yml                 # Main Ansible playbook
├── scripts
│   ├── wazuh-agent-setup.sh # Script for setting up Wazuh Agent
│   └── wazuh-server-setup.sh # Script for setting up Wazuh Manager
├── tasks
│   ├── wazuh-agent.yml         # Task file for Wazuh Agent configuration
│   └── wazuh-setup.yml         # Task file for Wazuh Manager setup
```

### Prerequisites

1. **Ansible Installed**: Ensure Ansible is installed on your control node.
2. **SSH Access**: Passwordless SSH access should be configured between the control node and target systems.
3. **Dependencies**:
   * Target systems should have internet access to download necessary packages.
   * Ensure sudo privileges on target systems.

### Usage

#### Step 1: Update the Inventory

Update the `inventory/hosts` file to define the target systems for the Wazuh Manager and Agent installation. Below is an example:

```bash
[wazuh_manager]
manager ansible_host=192.168.1.100 ansible_user=ubuntu
[wazuh_agent]
agent ansible_host=192.168.1.101 ansible_user=ubuntu
```

#### Use to ping the commands now:

```bash
ansible all -i inventory/hosts -m ping
```

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

#### Step 2: Customize Variables

If needed, customize the variables in the playbooks or scripts to match your environment.

#### Step 3: Run the Playbook

Execute the main playbook to set up Docker, Wazuh Manager, and Wazuh Agent:

```bash
ansible-playbook -i inventory/hosts main.yml
```

```
ansible-playbook -i inventory/hosts azuh-setup.yml
ansible-playbook -i inventory/hosts wazuh-agent.yml
```

#### Step 4: Verify Installation

* For Wazuh Manager:
  * Ensure the Wazuh Manager service is running on the designated host.
* For Wazuh Agent:
  * Verify the Wazuh Agent is connected to the Wazuh Manager.

### Scripts Overview

* **`wazuh-agent-setup.sh`**: Sets up the Wazuh Agent on the target system.
* **`wazuh-server-setup.sh`**: Configures and starts the Wazuh Manager.

### Task Files

* **`wazuh-agent.yml`**: Configures Wazuh Agent on the target host.
* **`wazuh-setup.yml`**: Configures Wazuh Manager.



**On manager**

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

**On Wazuh agent**

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

#### Pending tasks:&#x20;

* Need to be manually setup kibana which I will mention on page:

{% content-ref url="kibana.md" %}
[kibana.md](kibana.md)
{% endcontent-ref %}


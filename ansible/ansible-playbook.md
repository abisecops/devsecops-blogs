# Ansible Playbook

Today we are going to make a playbook and inventory file:

**inventory**

**->** Inventory cover all the details and configurations of the servers.

Your requirements:

* pemfiles
* ip address
* username
* group \[optional]

```bash
[deployment]
13.127.148.152 ansible_user=ubuntu ansible_ssh_private_key_file=~/Documents/pemfiles/deploy/deploy.pem

[portal]
dashboardapi.hicare.in ansible_user=ubuntu ansible_ssh_private_key_file=~/Documents/pemfiles/portal/portal.pem

[rnd]
192.168.2.88 ansible_user=researcher

[mobiledev]
13.200.98.24 ansible_user=ubuntu ansible_ssh_private_key_file=~/Documents/pemfiles/mobiledev/mobiledev.pem

[prod]
3.112.136.195 ansible_user=ubuntu ansible_ssh_private_key_file=~/Documents/pemfiles/prod/prod.pem

[qa]
3.6.10.62 ansible_user=ubuntu ansible_ssh_private_key_file=~/Documents/pemfiles/qa/qa.pem
```

&#x20;\
**usrin.yml**

**->** With this usrin.yml, you can easily manage all servers from one command. Command will be user input format.&#x20;

```bash
---
- name: Get list info from hosts
  hosts: all
  gather_facts: no

  vars_prompt:
    - name: user_command
      prompt: "Enter the command to execute:"
      private: no

  tasks:
    - name: Run user-specified command
      ansible.builtin.shell:
        cmd: "{{ user_command }}"
      register: command_output

    - name: Format output
      set_fact:
        command_info:
          hostname: "{{ inventory_hostname }}"
          command_output: "{{ command_output.stdout_lines }}"

    - name: Debug output
      ansible.builtin.debug:
        var: command_info
```

Now, let's make a simple command:&#x20;

```bash
sudo ansible-playbook -i inventory usrin.yml
```

Try basic command: **uname ;** you can get uname from all servers now

```bash
Enter the command to execute:: uname 
```

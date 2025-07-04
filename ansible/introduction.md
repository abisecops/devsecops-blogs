# Introduction

Ansible is a powerful open-source automation tool used for configuration management, application deployment, and orchestration in DevOps workflows. Benefits of Ansible are Free, Very simple to set up and use, Powerful, Flexible, Agentless, and Efficient.

### Installation:&#x20;

```
sudo apt-add-repository ppa:ansible/ansible
sudo apt install ansible -y
```

Try command `ansible`:

```bash
ansible
```

In my case, I got an error here:&#x20;

```vim
devops@1337:~$ ansible
 ERROR: Ansible requires the locale encoding to be UTF-8; Detected ISO8859-1.
```

I fixed this issue with the given commands:&#x20;

```bash
locale
export LC_ALL="en_US.UTF-8"
export LANG="en_US.UTF-8"
```

Then,&#x20;

```
ansible
```

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption><p>Ansible installation demo</p></figcaption></figure>


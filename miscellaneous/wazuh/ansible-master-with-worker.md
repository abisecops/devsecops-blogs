# Ansible (master with worker)

#### Wazuh Manager server ec2

<pre class="language-bash"><code class="lang-bash"><strong>sudo apt update -y
</strong>sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y
</code></pre>

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Create ssh-keygen with&#x20;

```bash
ssh-keygen -t rsa -b 2048
```

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

Copy this key and we'll add to agent server later.

```
cat ~/.ssh/id_rsa.pub
```

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Paste the given keys to authorized\_keys of wazuh agent server.

```
nano ~/.ssh/authorized_keys
```

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

```
ansible all -i inventory/hosts -m ping

```


# Set Up Git Repository on Storage Server

### Tasks

1. Utilize `yum` to install the `git` package on the `Storage Server`.
2. Create a bare repository named `/opt/apps.git` (ensure exact name usage).

### Steps

{% stepper %}
{% step %}
SSH into `Storage Server`

```bash
ssh natasha@172.16.238.15
```

<figure><img src="../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Update the Package Manager's Cache

```bash
sudo yum update -y
```
{% endstep %}

{% step %}
Install Git

```bash
sudo yum install git -y
```
{% endstep %}

{% step %}
Verify Git Installation

```bash
git --version
```

<figure><img src="../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Change the current directory to the `/opt` directory

```bash
cd /opt
```
{% endstep %}

{% step %}
Create the bare repository using the `git init` command with the `--bare` flag

```bash
git init --bare apps.git 
```

<figure><img src="../.gitbook/assets/image (210).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

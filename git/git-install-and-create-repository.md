# Git Install and Create Repository

### Tasks

1. Install `git` package using `yum` on `Storage server`.
2. After that, create/init a git repository named `/opt/ecommerce.git` (use the exact name as asked and make sure not to create a bare repository).

### Steps

{% stepper %}
{% step %}
### ssh to storage server

```bash
ssh natasha@ststor01
```
{% endstep %}

{% step %}
### Get sudo access

```
sudo su -
```
{% endstep %}

{% step %}
### Install git

```
yum install -y git
```
{% endstep %}

{% step %}
### Get the directory

```
cd /opt
```
{% endstep %}

{% step %}
### Init the file

```
git init /opt/ecommerce.git
```

<figure><img src="../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

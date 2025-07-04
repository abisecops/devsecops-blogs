# Git Create Branches

### Tasks

1. On `Storage server` in Stratos DC create a new branch `xfusioncorp_ecommerce` from `master` branch in `/usr/src/kodekloudrepos/ecommerce` git repo.
2. Please do not try to make any changes in the code.

### Steps

{% stepper %}
{% step %}
### ssh to storage server

```
ssh natasha@ststor01
```
{% endstep %}

{% step %}
### Get sudo access&#x20;

```
sudo su -
```
{% endstep %}

{% step %}
### Navigate to ecommerce directory

```
cd /usr/src/kodekloudrepos/ecommerce
```
{% endstep %}

{% step %}
### Checkout master branch

```
git checkout master
```
{% endstep %}

{% step %}
### Create new branch&#x20;

```
git checkout -b xfusioncorp_ecommerce
```

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Get git status

```
git status
```
{% endstep %}

{% step %}
### Get all branches

```
git branch -a
```

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

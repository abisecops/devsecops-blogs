# Delete Git Branch

### Tasks

* Delete the `xfusioncorp_beta` branch from the Git repo at `/usr/src/kodekloudrepos/beta` on the Storage Server.

### Steps

{% stepper %}
{% step %}
SSH into the Storage server:

```bash
ssh natasha@ststor01
```
{% endstep %}

{% step %}
### Get the repo

```
cd /usr/src/kodekloudrepos/beta
sudo git config --global --add safe.directory /usr/src/kodekloudrepos/beta
```
{% endstep %}

{% step %}
Check if this branch is exist there or now

```
sudo git branch --list xfusioncorp_beta
```
{% endstep %}

{% step %}
Check the branches

<pre><code><strong>sudo git branch
</strong></code></pre>
{% endstep %}

{% step %}
Change to the master

```
sudo git checkout master
```

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Change the permissions

```bash
sudo chown -R natasha /usr/src/kodekloudrepos/beta
sudo chmod -R u+rwx /usr/src/kodekloudrepos/beta
```
{% endstep %}

{% step %}
Delete the branch

```bash
git branch -D xfusioncorp_beta
```

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Verify now

```
git branch
```

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

# Git Revert Some Changes

### Tasks

1. Access the git repository at `/usr/src/kodekloudrepos/beta` on the `Storage server` in `Stratos DC`.
2. Identify the current HEAD commit to be reverted.
3. Revert the HEAD commit to the previous commit with the message "initial commit".
4. Use `git revert HEAD` to create a new commit with the message "revert beta".



#### Steps

{% stepper %}
{% step %}
SSH to the Storage server

```
ssh natasha@ststor01
```
{% endstep %}

{% step %}
Get root/sudo access

```
sudo su -
```
{% endstep %}

{% step %}
Navigate to the beta repo

```
cd /usr/src/kodekloudrepos/beta
```
{% endstep %}

{% step %}
Check recent commits

```
git log --oneline -2
```

<figure><img src="../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Revert the latest commit

```
git revert HEAD --no-edit
```

<figure><img src="../.gitbook/assets/image (222).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Change the commit message to exactly "revert beta"

```
git commit --amend -m "revert beta"
```

<figure><img src="../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Verify the commit history

```
git log --oneline -2
```

<figure><img src="../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

# Git Stash

### Tasks

1. Go to the Git repository located at `/usr/src/kodekloudrepos/blog` on the Storage server.
2. Identify available stashes.
3. Apply the stashed changes with the identifier `stash@{1}`.
4. Commit the restored changes with an appropriate message.
5. Push the changes to the `origin` remote.

### Steps

{% stepper %}
{% step %}
**SSH to storage server and switch to root if needed**

```bash
ssh natasha@ststor01
sudo su -
```
{% endstep %}

{% step %}
### Navigate to blog directory

```bash
cd /usr/src/kodekloudrepos/blog
```
{% endstep %}

{% step %}
Confirm `stash@{1}` exists

```bash
git stash list
```

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Restore the stashed changes

```bash
git stash apply stash@{1}
```

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Confirm restored files are ready for commit

```bash
git status
```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Git add and commit

```bash
git add .
git commit -m "Restore changes from stash@{1}"
```
{% endstep %}

{% step %}
Push to remote

```
git push origin master
```

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

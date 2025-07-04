# Git Clean

### Tasks&#x20;

1. Navigate to the Git repository located at `/usr/src/kodekloudrepos/cluster` on the Storage server.
2. Remove any untracked files and directories (files that are not committed to Git).
3. Do not add or push any new files.
4. Ensure that `git status` shows a clean working tree (no changes, no untracked files).

### Steps

{% stepper %}
{% step %}
SSH to storage server and switch to root if needed

```bash
ssh natasha@ststor01
sudo su -
```
{% endstep %}

{% step %}
### Navigate to cluster directory

```bash
cd /usr/src/kodekloudrepos/cluster
```
{% endstep %}

{% step %}
Check for untracked files

```bash
git status
```

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Remove all untracked files and directories

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

```bash
git clean -fd
```
{% endstep %}

{% step %}
Verify it says: "nothing to commit, working tree clean"

```bash
git status
```

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

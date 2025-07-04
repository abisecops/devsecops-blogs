# Git Cherry Pick

#### Git Cherry-Pick

* **Definition:** `git cherry-pick` applies changes from a specific commit to your current branch.
* **Summary:** Copies a single commit to another branch without merging the whole branch.
* **Use Case:** Pick select bug fixes or features from another branch without full merge.

### Tasks

1. Ensure you have access to the `storage server` where the repository is cloned at `/usr/src/kodekloudrepos`.
2. Navigate to the `/usr/src/kodekloudrepos` directory which contains the repository.
3. Identify the commit on the `feature` branch with the message `Update info.txt`.
4. Merge the identified commit from the `feature` branch into the `master` branch.
5. Push the updated `master` branch to the remote repository located at `/opt/official.git`.

### Steps

{% stepper %}
{% step %}
SSH into the storage server and get root

```bash
ssh natasha@ststor01
sudo su -
```
{% endstep %}

{% step %}
Navigate to the repo

```bash
cd /usr/src/kodekloudrepos/official
```
{% endstep %}

{% step %}
Fetch all branches to be sure you’re updated

```bash
git fetch --all
```
{% endstep %}

{% step %}
Check out the master branch&#x20;

```bash
git checkout master
```
{% endstep %}

{% step %}
Find the commit hash from feature branch with message "Update info.txt"

```bash
git log feature --grep="Update info.txt" --oneline
```

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### git cherry-ping commit ha, 0e3895a

```bash
git cherry-pick 0e3895a
```

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Push the updated master branch to remote

```bash
git push origin master
```

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}


# Git Merge Branches

### Tasks

1. Navigate to the `/usr/src/kodekloudrepos/demo` repository.
2. Create a new branch named `nautilus` from `master`.
3. Copy the `/tmp/index.html` file into the repository.
4. Add and commit the copied file to the `nautilus` branch.
5. Merge the `nautilus` branch into the `master` branch.
6. Push changes for both `nautilus` and `master` branches to the origin.

### Steps

{% stepper %}
{% step %}
### ssh storage server

```
ssh natasha@ststor01
```
{% endstep %}

{% step %}
### su access

```
sudo su -

```
{% endstep %}

{% step %}
### Navigate the given demo repo

```
cd /usr/src/kodekloudrepos/demo
```

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Git status

```
git status
```
{% endstep %}

{% step %}
### Create new branch

```
git checkout -b nautilus
```

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Again git status

```
git status
```
{% endstep %}

{% step %}
### Then, git branch

```
git branch
```
{% endstep %}

{% step %}
### Copy file

```bash
cp /tmp/index.html /usr/src/kodekloudrepos/demo/
```

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Commit and checkout to master

```bash
git commit -m "add index.html"
git checkout master
```

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption><p>y</p></figcaption></figure>
{% endstep %}

{% step %}
### git merge

```
git merge nautilus
```

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Push the local nautilus branch to the remote `origin` with upstream tracking using:

```
git push -u origin nautilus

```

This sends commits to the remote repository, available for collaborators.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Push to master now then git status

```
git push -u origin master
git status
```
{% endstep %}
{% endstepper %}

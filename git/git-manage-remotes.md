# Git Manage Remotes

### Tasks

* Navigate to the `/usr/src/kodekloudrepos/media` directory.
* Add a new remote named `dev_media`pointing to `/opt/media.git` using Git.
* Copy the file `/tmp/index.html` into the repository.
* Add the copied file to the staging area and commit it to the master branch.
* Push the master branch to the new remote `dev_media`.



### Steps

{% stepper %}
{% step %}
ssh to storage server

```
ssh natasha@ststor01
```
{% endstep %}

{% step %}
### get su access

```
sudo su -
```
{% endstep %}

{% step %}
Navigate to the `/usr/src/kodekloudrepos/media` directory.

```
cd /usr/src/kodekloudrepos/media
```
{% endstep %}

{% step %}
Add a new remote named `dev_media` pointing to `/opt/xfusioncorp_media.git` using Git.

```
git remote add dev_media /opt/xfusioncorp_media.git
```
{% endstep %}

{% step %}
### Copy index.html to current path

```
cp /tmp/index.html .
```

<figure><img src="../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Add, Commit and Push index.html to master

```
git add index.html
git commit -m "add index.html"

```

<figure><img src="../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Push master branch to dev\_media

```
git push dev_media master
```

<figure><img src="../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}


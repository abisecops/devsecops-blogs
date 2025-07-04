# Git hard reset

### Tasks

1. Navigate to `/usr/src/kodekloudrepos/demo` git repository on the Storage server.
2. Reset the repository so that only two commits remain:
   * `initial commit`
   * `add data.txt file`
3. Make sure the working directory and HEAD are aligned to `add data.txt file`.
4. Push the updated state to the remote, replacing existing history.

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
### Navigate to demo directory

```
cd /usr/src/kodekloudrepos/demo
```
{% endstep %}

{% step %}
Find the commit hash for "add data.txt file"

```
git log --oneline
```

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Reset to "add data.txt file"

```
git rebase -i --root
```

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Keep only:

* `initial commit`
* `add data.txt file`

(Delete or drop other commits in the interactive editor)

```
git rebase -i --root
```
{% endstep %}

{% step %}
Force push cleaned-up history

```
git push origin master --force
```
{% endstep %}

{% step %}
Verify only two commits remain

```
git log --oneline
```

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

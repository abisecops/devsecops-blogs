# Manage Git Pull Requests

### Tasks

1. SSH into the storage server as user `max` using the given credentials.
2. Locate the already cloned Git repository in Max's home directory.
3. Confirm the repository contains Sarah’s story and commit history using `git log`.
4. Verify Max's story is pushed to the `story/fox-and-grapes` branch.
5. Open the Gitea UI from the top bar of the lab environment.
6. Log in to Gitea as user `max`.
7. Create a Pull Request:
   * Title: `Added fox-and-grapes story`
   * Source branch: `story/fox-and-grapes`
   * Destination branch: `master`
8. Assign `tom` as a reviewer to the PR through the Gitea UI.
9. Log out of Gitea.
10. Log in to Gitea as user `tom`.
11. Review and approve the Pull Request.
12. Merge the PR into the `master` branch.
13. Take screenshots (or a screen recording) as evidence of each key action.



### Steps

{% stepper %}
{% step %}
SSH max Login with password `Max_pass123`

```
ssh max@ststor01
```
{% endstep %}

{% step %}
Navigate to the cloned repo

```
cd story-blog
```
{% endstep %}

{% step %}
Confirm Sarah's and Max’s commits exist

```
git log
```

<figure><img src="../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Verify `story/fox-and-grapes` exists

```
git branch -a
```

<figure><img src="../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Open **Gitea UI and**  Login as `max` / `Max_pass123`

<figure><img src="../.gitbook/assets/image (227).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Create PR in **`story-blog`** repo:

* Title: `Added fox-and-grapes story`
* From branch: `story/fox-and-grapes`
* To branch: `master`

<figure><img src="../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
In PR page → Click **Reviewers** → Add `tom`

<figure><img src="../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Logout from Max's Gitea account. Login as `tom` / `Tom_pass123`

<figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Open the PR → Review → Approve → Merge

<figure><img src="../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
The pull request has been merged as [`6764b4acf8`](http://git.stratos.xfusioncorp.com/sarah/story-blog/commit/6764b4acf839c03b51983c778467ab4c436d24b4).

<figure><img src="../.gitbook/assets/image (232).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (233).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

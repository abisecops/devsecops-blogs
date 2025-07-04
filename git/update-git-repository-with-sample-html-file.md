# Update Git Repository with Sample HTML File

### Tasks

* A repository named `/opt/games.git` has been created.
* It has been cloned to `/usr/src/kodekloudrepos/games` on the **storage server**.
* A sample `index.html` file is located on the **jump host** at `/tmp/index.html`.
* Copy the file to `/usr/src/kodekloudrepos/games` on the storage server.
* Add and commit the file to the repository.
* Push the changes to the `master` branch.

### Steps

{% stepper %}
{% step %}
Check the file location

```bash
cd /tmp
ls
```

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Copy file

```
sudo scp /tmp/index.html natasha@ststor01:/tmp
```

passwd : Bl@kW

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
SSH into the Storage server (natasha's server :joy:)

```
ssh natasha@ststor01
```
{% endstep %}

{% step %}
Copy index.html to the path

```
cp index.html /usr/src/kodekloudrepos/games
```
{% endstep %}

{% step %}
### Navigate to games directory

```
cd /usr/src/kodekloudrepos/games
```

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Git status

```bash
sudo git status
```

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Add, Commit and Push

```bash
sudo git add index.html
sudo git commit -m "add index.html"
sudo git push origin master 
```

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}


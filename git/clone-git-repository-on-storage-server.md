# Clone Git Repository on Storage Server

### Tasks&#x20;

1. The repository to be cloned is located at `/opt/cluster.git`
2. Clone this Git repository to the `/usr/src/kodekloudrepos` directory. Ensure no modifications are made to the repository during the cloning process.

### Steps

{% stepper %}
{% step %}
**SSH into the Storage Server**

```
ssh natasha@172.16.238.15
```
{% endstep %}

{% step %}
Navigate to the working directory

```
cd /usr/src/kodekloudrepos
```
{% endstep %}

{% step %}
Clone the local repository

```
git clone /opt/cluster.git
```

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Verify now

```
ls -l
```

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

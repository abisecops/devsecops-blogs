---
description: Deployment services and make run in ubuntu
---

# Service deployment and monitoring

Today we did service deployment for dot net with ubuntu server.

**Steps:**&#x20;

```
1) Download the rar file from mail
2) Extract the file
3) Change the directory inside the folder including .dll files
4) Move the folder to /srv directory
```

```
mv foldername /srv/
```

<figure><img src="../.gitbook/assets/image (149).png" alt=""><figcaption><p>srv files</p></figcaption></figure>

Now go to the services directory:&#x20;

```
cd /etc/systemd/system
ls
#you can see services files here
```



<figure><img src="../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure>

```
#enable the service
sudo systemctl enable *-servicename.service
#start the service
sudo systemctl start *-servicename.service
#get status of the service
sudo systemctl status *-servicename.service
```

Now, check the services running in name of "hicare" using the command:

```
systemctl | grep "hicare"
```



<figure><img src="../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

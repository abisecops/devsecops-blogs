---
description: SSH Problem
cover: >-
  https://forum.nomachine.com/wp-content/uploads/2014/01/Screen-Shot-2014-01-07-at-1.15.39-PM.png
coverY: 0
---

# Connection reset by peer

How can I fix "kex\_exchange\_identification: read: Connection reset by peer"?

**The error is:**

```
kex_exchange_identification: read: Connection reset by peer
Connection reset by x.x.x.x port 22
Connection closed by x.x.x.x port 34976
```

<figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

It could be the process on the server side listening to the SSH _port_ is dead, and even a restart / stop service do not work. So to find the process, and killing it may solve the problem.

Let's debug more with netstat:&#x20;

```
sudo netstat -ntlp
```

<figure><img src="../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

Time to kill pid:

```
sudo kill 619
sudo netstat -ntlp
```

<figure><img src="../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>



Now, the issue is fixed:&#x20;

```bash
sudo systemctl restart ssh
sudo systemctl status ssh
```

<figure><img src="../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

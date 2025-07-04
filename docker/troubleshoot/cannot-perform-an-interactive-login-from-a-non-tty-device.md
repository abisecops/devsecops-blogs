---
description: Unable to use AWS CLI in Jenkins due to "Unable to locate credentials" error
cover: ../../.gitbook/assets/image (172).png
coverY: 0
---

# Cannot perform an interactive login from a non TTY device

<figure><img src="../../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>

Method (1)

Update your aws credentials within the the bash of the jenkins server. With the following commands:

```
sudo -su jenkins
aws configure
```



Method (2)

Another method

1. Make directory in `/var/lib/jenkins` that called .aws (or copy .aws folder from home directory if you already configured your aws credentials via "aws configure" command)
2. Then go down to `/var/lib/jenkins/.aws` and write `sudo shown -R jenkins ./` to change owner for files in .aws directory.



You can check again with the given command:&#x20;

```
aws configure list
```

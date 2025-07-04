---
description: codedeploy-agent on ec2 instance
cover: ../../.gitbook/assets/image (176).png
coverY: 0
---

# Install the CodeDeploy agent for Ubuntu Server

#### Steps:&#x20;

<pre class="language-bash"><code class="lang-bash">sudo apt update
sudo apt install ruby-full
sudo apt install wget
cd /home/ubuntu
<strong>wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
</strong>chmod +x ./install
sudo ./install auto
</code></pre>

* Writing the output to a temporary log file is a workaround that should be used while we address a known bug with the `install` script on Ubuntu Server 20.04.

```bash
sudo ./install auto > /tmp/logfile
```

```bash
systemctl status codedeploy-agent
systemctl start codedeploy-agent # if services are stopped
```

<figure><img src="../../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>

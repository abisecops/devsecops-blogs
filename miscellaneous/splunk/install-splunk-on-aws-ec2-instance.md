---
icon: sign-posts-wrench
---

# Install Splunk on AWS EC2 Instance

Let's install Splunk on AWS EC2 Instance.&#x20;

1. First visit the Splunk link:&#x20;

{% embed url="https://www.splunk.com/" %}

* Register for free trial. (Usually I use temp mails for such kinda account, even you can also use that)&#x20;

2. Verify and login now.
3. Let's download

{% embed url="https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html" %}

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

Download via [Command Line (wget)](https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html)

```bash
wget -O splunk-9.3.2-d8bb32809498-linux-2.6-amd64.deb "https://download.splunk.com/products/splunk/releases/9.3.2/linux/splunk-9.3.2-d8bb32809498-linux-2.6-amd64.deb"
```

Launch the instance for Splunk

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

Connect now with pem files for the instance

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

Use the given commands

```bash
sudo apt update -y
wget -O splunk-9.3.2-d8bb32809498-linux-2.6-amd64.deb "https://download.splunk.com/products/splunk/releases/9.3.2/linux/splunk-9.3.2-d8bb32809498-linux-2.6-amd64.deb"

```

<figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

```bash
sudo dpkg -i splunk-9.3.2-d8bb32809498-linux-2.6-amd64.deb
```

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

First, switch to the Splunk directory:

```bash
cd /opt/splunk
```

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

Then, start Splunk:

```bash
sudo ./bin/splunk start

```

Then just press enter till the  \_

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

Give desire credentials

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

The Splunk web interface is at [http://ip-172-31-21-144:8000](http://ip-172-31-21-144:8000)

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

Lets access the Splunk Web Interface.&#x20;

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

Now signin with your credentials.

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

<pre class="language-bash"><code class="lang-bash"># Some Useful Commands
cd /opt/splunk #directory
<strong>sudo ./bin/splunk start #start splunk
</strong>sudo ./bin/splunk stop #stop splunk
sudo ./bin/splunk restart #restart splunk
sudo ./bin/splunk status #status splunk
</code></pre>


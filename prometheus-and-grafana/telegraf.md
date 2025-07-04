---
description: >-
  Telegraf is a plugin-driven server agent written in Go for collecting metrics
  & data on the system.
---

# Telegraf

Now you need to configure **telegraf plugin to influxdb**.&#x20;

**Best features on influx is you can write and query data using the programming language of your choice.**

**Download steps of telegraf:**&#x20;

```bash
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c && cat influxdata-archive_compat.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg > /dev/null
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' | sudo tee /etc/apt/sources.list.d/influxdata.list
sudo apt-get install telegraf
```

<figure><img src="../.gitbook/assets/image (139).png" alt=""><figcaption><p>File upload</p></figcaption></figure>

You can use these programming language to configure:

<figure><img src="../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>

We can use different plugin as per our requirements:&#x20;

<figure><img src="../.gitbook/assets/image (141).png" alt=""><figcaption><p>Plugins sample of telegraf agent in influxdb</p></figcaption></figure>

Prometheus config on telegraf:&#x20;

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

Error found:&#x20;

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

Let's fix the issue. Status = 401 means auth error.

Again come to the config file of prometheus. Token were not configured there.

Regenerate the token and follow this step again:&#x20;

```bash
export INFLUX_TOKEN=ckURyEPM-Z0ZOVrEZ4F13xE8AKl757USDGuHCRdTtyj9rVFF-WGsa0V5GJgKbNFTNbjSMGd7leKluuywKRpksQ==
telegraf --config http://hostip:8086/api/v2/telegrafs/0c6897d0d83b5000

```

Now, the error is fixed:&#x20;

<figure><img src="../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

Let's monitor on influxdb:\
![](<../.gitbook/assets/image (144).png>)

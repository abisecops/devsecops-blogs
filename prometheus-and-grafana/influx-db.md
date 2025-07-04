---
description: >-
  InfluxDB is an open-source time series database developed by the company
  InfluxData.
---

# Influx DB

`TSDB: Time Series Database`

It is used for storage and retrieval of time series data in fields such as operations monitoring, application metrics, Internet of Things sensor data, and real-time analytics.

Download steps:&#x20;

```bash
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c && cat influxdata-archive_compat.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg > /dev/null
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' | sudo tee /etc/apt/sources.list.d/influxdata.list

sudo apt-get install influxdb2
```

If you mistakenly install influxdb instead of influxdb2. You might get the issue of unmasked service in the command:&#x20;

```bash
systemctl status influxdb
```

Influxdb doesn't support GUI nowadays. You have to install influxdb2 -> upgraded version

Then, use remove the previous one with autoremove and this command to unmask the service:

```bash
systemctl unmasked influxdb
systemctl restart influxdb
systemctl status influxdb
```

Now you can access from the link: http://hostIP:8086

Create your credentials: user: passwd

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

You company, Your bucket -> You can change these later.

We have two features:

1\) Influx CLI

2\) Server Agent (Telegraf)

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

To setup influxdb on cli:&#x20;

```
pip3 install influxdb-client
```

```bash
influx -host hostIP -port 8086 -username user -password passwda
```

Next step on Telegraf

{% content-ref url="telegraf.md" %}
[telegraf.md](telegraf.md)
{% endcontent-ref %}


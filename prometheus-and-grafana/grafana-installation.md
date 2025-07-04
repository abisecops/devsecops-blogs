---
cover: https://grafana.com/meta-generator/Install%20Grafana.jpg
coverY: 0
---

# Grafana Installation



Standalone Linux Binaries:&#x20;

```
wget https://dl.grafana.com/enterprise/release/grafana-enterprise-10.2.3.linux-amd64.tar.gz
tar -zxvf grafana-enterprise-10.2.3.linux-amd64.tar.gz
```

Config file of grafana: \``/etc/grafana/grafana.ini`

```bash
sudo /bin/systemctl enable grafana-server
Synchronizing state of grafana-server.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable grafana-server
Created symlink /etc/systemd/system/multi-user.target.wants/grafana-server.service → /lib/systemd/system/grafana-server.service.
 sudo /bin/systemctl start grafana-server
 sudo /bin/systemctl status grafana-server
```

Default password: admin:admin

Current passwd: admin:admin@2024A

Dashboard ID: 3662&#x20;

Adding Prometheus host\_IP on Grafana during configuration

Steps: to add  prometheus

* [Home](http://192.168.2.101:3000/) > [Connections](http://192.168.2.101:3000/connections) > [Data sources](http://192.168.2.101:3000/connections/datasources)
* Select prometheus

<figure><img src="../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>



{% embed url="http://192.168.2.101:3000/d/acaa1774-d9bb-4bbe-b4a7-677fb87df44c/prometheus-2-0-overview?orgId=1&refresh=30s&from=1704455670724&to=1704457470725" %}
Dashboard Link of grafana \
Source: Official Documentation of grafana
{% endembed %}

`Notification Alert System:`&#x20;

`Methods:`

`1) email -> smtp not set out -> (pending)`

<figure><img src="../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

`2) discord-webhook url : Sucessfully tested`

<figure><img src="../.gitbook/assets/image (130).png" alt=""><figcaption><p>Discord webhook configuration</p></figcaption></figure>

Now, send test notification:&#x20;

<figure><img src="../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

`You can access through the given invitation link:`&#x20;

[`https://discord.gg/ShqdMvgt`](https://discord.gg/ShqdMvgt)

`We can also configure admin option.`

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://medium.com/yavar/install-and-setup-grafana-on-ubuntu-20-04-22-04-8798824df026" %}

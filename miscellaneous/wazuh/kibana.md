# Kibana

Enable and start Kibana:

```
sudo systemctl enable kibana
sudo systemctl start kibana
```

```
# Start the Wazuh Dashboard:

sudo systemctl enable wazuh-dashboard
sudo systemctl start wazuh-dashboard

```

```
sudo systemctl restart wazuh-manager
```

**wazuh agent**

```
sudo systemctl restart wazuh-agent
sudo systemctl enable wazuh-agent
```

**Kibana**

Change localhost to **0.0.0.0 from kibana.yml**

```
sudo nano /etc/kibana/kibana.yml

```

```
server.host: "localhost"

```

```
server.host: "0.0.0.0"
```

```linker-script
http://<your-server-ip>:5601
```

```
sudo systemctl restart kibana
```



Elastic search

```
sudo /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token --scope kibana
```

<figure><img src="../../.gitbook/assets/image (202).png" alt=""><figcaption></figcaption></figure>

```bash
bin/elasticsearch-create-enrollment-token --scope kibana
```

<figure><img src="../../.gitbook/assets/image (201).png" alt=""><figcaption></figcaption></figure>

Now let's login the portal.&#x20;

<figure><img src="../../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>

I don't know password, now time to set.

```bash
sudo ./elasticsearch-reset-password -u elastic
```

<figure><img src="../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>

username: elastic

password: \*\*\*\*\*\*



<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

```
```

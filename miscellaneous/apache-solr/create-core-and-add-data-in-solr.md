# Create Core & Add Data in Solr

Install solr first [introduction.md](introduction.md "mention")

1. Now config solr setup:

```bash
sudo chmod -R u+w /var/solr/data
```

2. Create core data:&#x20;

```bash
sudo su - solr -c "/opt/solr/bin/solr create -c coder -n data_driven_schema_configs" 
```

3. To delete core data:&#x20;

```bash
/opt/solr/bin/solr delete -c coder
```

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

Then,  create the solr core again:&#x20;

<figure><img src="../../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

In case, you got any error check on the logs: \


```bash
cd /var/solr
```

Try to give 755 permission if you stuck for permission there.

For restart:&#x20;

```bash
sudo service solr restart
```

## POST request to the Solr server running on `127.0.0.1:8983` with the content type set to JSON

* Solr core name: coder

```bash
curl -X POST \
  -H 'Content-Type: application/json' \
  'http://127.0.0.1:8983/solr/coder/update/json/docs' \
  --data-binary '{
    "id": "02",
    "first_name": "Abishek",
    "last_name": "Kafle",
    "title": "DevOps and Security",
    "cybername": "anoint"
  }'

```

```bash
sudo service solr restart
```

<figure><img src="../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

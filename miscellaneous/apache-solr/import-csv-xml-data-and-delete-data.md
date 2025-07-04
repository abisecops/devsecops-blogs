# Import csv, xml data & Delete data

**Today we are going to post data with different file**&#x20;

## Import data

### For json:&#x20;

```bash
sudo nano main.json
```

```json
{
  "id": "02",
  "first_name": ["Abishek"],
  "last_name": ["Kafle"],
  "title": ["DevOps and Security"],
  "cybername": ["anoint"]
}

```

Now post this **main**.json file using curl:

```bash
curl -X POST \
  -H 'Content-Type: application/json' \
  'http://127.0.0.1:8983/solr/coder/update/json/docs' \
  --data @main.json

```

* You can also update json file as per your requirements.
* After POST the json also restart the solr too:&#x20;

```bash
sudo service solr restart
```

### For xml:

```bash
sudo nano main.xml
```

```xml
<add>
  <doc>
    <field name="id">02</field>
    <field name="first_name">Abishek</field>
    <field name="last_name">Kafle</field>
    <field name="title">DevOps and Security</field>
    <field name="cybername">anoint</field>
  </doc>
</add>

```

**Post XML Data to Solr using curl**:

```bash
curl -X POST \
  -H 'Content-Type: application/xml' \
  'http://127.0.0.1:8983/solr/coder/update' \
  --data-binary @main.xml
```

**Restart Solr**:

```bash
sudo service solr restart
```

## Delete Data

### For json:&#x20;

1\) Delete the specific data from json:&#x20;

```bash
curl -X POST \
  'http://127.0.0.1:8983/solr/coder/update/json/docs' \
  -H 'Content-Type: application/json' \
  --data-binary '{
    "delete": {
      "query": "id:02"
    }
  }'

```

2\) Delete all data from json:&#x20;

```bash
curl -X POST \
  'http://127.0.0.1:8983/solr/coder/update/json/docs' \
  -H 'Content-Type: application/json' \
  --data-binary '{
    "delete": {
      "query": "*:*"
    }
  }'

```



### For xml:&#x20;

1\) Delete the specific data from xml:&#x20;

```bash
curl -X POST \
  'http://127.0.0.1:8983/solr/coder/update' \
  -H 'Content-Type: application/xml' \
  --data-binary '<delete><query>id:02</query></delete>'
```

2\) Delete all the data from xml:&#x20;

```bash
curl -X POST \
  'http://127.0.0.1:8983/solr/coder/update' \
  -H 'Content-Type: application/xml' \
  --data-binary '<delete><query>*:*</query></delete>'

```

* After deleting documents, you should commit the changes to make them visible in Solr:

```bash
curl -X POST \
  'http://127.0.0.1:8983/solr/coder/update' \
  -H 'Content-Type: application/xml' \
  --data-binary '<commit />'
```

```bash
sudo service solr restart
```

* You can also use UI too but cli is preferred:&#x20;

{% embed url="https://f5c4-52-157-4-131.ngrok-free.app/solr/#/coder/documents" %}

<div align="left"><figure><img src="../../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure></div>

## File Upload

You can also upload your file:&#x20;

<figure><img src="../../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

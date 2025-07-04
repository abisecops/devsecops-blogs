---
description: >-
  Configure Solr to use the Data Import Handler (DIH) for importing data from an
  SQL database
---

# Data Import Handler (DIH)

1. Navigate to the directory:&#x20;

```bash
cd /opt/solr/server/solr/mycore/conf
```

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

* If you don't have this directory:&#x20;

```bash
sudo cp -r /opt/solr/server/solr/configsets/_default /opt/solr/server/solr/mycore
cd /opt/solr/server/solr/mycore/conf
```

#### 2. Modify the  **solrconfig.xml** file:&#x20;

```bash
sudo nano solrconfig.xml
```

```xml
<config>
<lib dir="/opt/solr/dist/" regex="solr-dataimporthandler-.*\.jar" />
<requestHandler name="/dataimport" class="org.apache.solr.handler.dataimport.DataImportHandler">
  <lst name="defaults">
    <str name="config">data-config.xml</str>
  </lst>
</requestHandler>
</config>
```

3. Now, `data-config.xml` for MySQL:

```bash
sudo nano data-config.xml
```

```xml
<dataConfig>
  <dataSource type="JdbcDataSource" 
              driver="com.mysql.jdbc.Driver" 
              url="jdbc:mysql://localhost:3306/xyz_database" 
              user="your_username" 
              password="your_password" />
  <document>
    <entity name="table_name" query="SELECT * FROM your_table">
      <field column="column1" name="column1"/>
      <field column="column2" name="column2"/>
      <!-- Add more fields as needed -->
    </entity>
  </document>
</dataConfig>
```

4. Run the dataimport:&#x20;

* After configuring DIH on solr, we can initiate the data import process by sending an HTTP request to Solr using the given command/ query:&#x20;

```bash
curl 'http://localhost:8983/solr/core_name/dataimport?command=full-import'
```

5. **Check Import Status:**

* We can check the import status by visiting Solr's Admin UI or querying the status using `curl`:

```bash
curl 'http://localhost:8983/solr/core_name/dataimport?command=status'
```

<mark style="color:red;">Points to be remember:</mark>

* Remember to ensure that your Solr server and SQL database are accessible.
* Handle sensitive information e.g database credentials securely.

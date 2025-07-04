---
description: >-
  Solr powers some of the most heavily-trafficked websites and applications in
  the world.
---

# Introduction

Solr is highly reliable, scalable and fault tolerant, providing distributed indexing, replication and load-balanced querying, automated failover and recovery, centralized configuration and more. Solr powers the search and navigation features of many of the world's largest internet sites.

Today, we are going to install solr in our ubuntu server.&#x20;

1. The following command will install the solr in our system:&#x20;

```bash
sudo apt update -y 
cd /opt
sudo wget https://archive.apache.org/dist/lucene/solr/8.2.0/solr-8.2.0.tgz
sudo tar xzf solr-8.2.0.tgz solr-8.2.0/bin/install_solr_service.sh --strip-components=2
 sudo ./install_solr_service.sh solr-8.2.0.tgz
 
```

2. Now, Solr should be up and running, verify with&#x20;

```bash
sudo service solr status
```

If not, try this:&#x20;

```bash
sudo service solr stop
sudo service solr start
sudo service solr status
```

3. By default the port of Solr is 8983. Try : [http://localhost:8983/](https://localhost:8983/)

If we are using localhost and wanna try to port mapping to public try ngrok. Let's do it.&#x20;

**Ngrok setup for solr :**&#x20;

1. Login with solr : [ngrok.com](https://ngrok.com/).&#x20;

```bash
curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
  | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null && echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
  | sudo tee /etc/apt/sources.list.d/ngrok.list && sudo apt update && sudo apt install ngrok
```

Now config your authtoken:&#x20;

```bash
ngrok config add-authtoken 232LoK9HE67GqM6veskRqb3GuR0_6so5RVAzM1KyYtk6zp3MC
```

Try:&#x20;

```
ngrok http http://localhost:8983
```

Or:&#x20;

```
ngrok http 8983
```

Now you will get your public url: \
[https://8276-20-172-46-65.ngrok-free.app](https://8276-20-172-46-65.ngrok-free.app)\
\


<figure><img src="../../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

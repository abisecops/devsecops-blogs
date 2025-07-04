---
description: Hiding version of nginx server on the website
---

# Hide Nginx Server Info

While deploying APIs on nginx server, we should be aware about future possible vulnerable cases. So better to prevent such possible vulnerability and threats on time.

There are several cves published regularly. In case, attacker know our server info, he/she can test or exploit to our server. So, better to hide them to prevent such cases.

**Steps:**

1. **Create the custom server name:**&#x20;

```bash
sudo apt-get install nginx-extras
```

```bash
cd /etc/nginx/sites-available
```

```bash
more_set_headers 'Server: hicare'; # To Set a custom string as "Server" 
```

2. Now time to update nginx.conf too:&#x20;

```bash
       #add this on http section
       server_tokens off;
        more_clear_headers Server; 
```

As the below format

```
http {

        ##
        # Basic Settings
        ##

        sendfile on;
        tcp_nopush on;
        types_hash_max_size 2048;
        server_tokens off;
        more_clear_headers Server;      

        # server_names_hash_bucket_size 64;
        # server_name_in_redirect off;

        include /etc/nginx/mime.types;
        default_type application/octet-stream;

}
```

Now, test and reload nginx server:&#x20;

```
sudo nginx -t
sudo nginx -s reload
sudo systemctl restart nginx
```

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption><p>Hicare server</p></figcaption></figure>

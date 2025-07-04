---
description: 'SSL certificate  on : dashboardapi.hicare.in'
---

# Issuing SSL Certificate

#### Steps:&#x20;

1. Use the given command on linux server:&#x20;

```bash
openssl req -new -newkey rsa:2048 -nodes -keyout dashboardapi_hicare_in.pem -out dashboardapi_hicare_in.csr -subj /CN=dashboardapi.hicare.in; cat dashboardapi_hicare_in.csr
```

2. Download the zip file.
3. Copy file **local host to server**.

```bash
sudo scp -i 'Dashboard Server Key.pem' 'dashboardapi.hicare.in_cert.zip' ubuntu@15.207.50.230:/home/ubuntu/
```

4. Now unzip the file:

```bash
unzip 'dashboardapi.hicare.in_cert.zip' -d ./dashboardapi.hicare.in_cert
```

5. Copy all files of the folder to **/etc/ssl/ :**

```bash
cd dashboardapi.hicare.in_cert
sudo cp -r * /etc/ssl/
```

6. Now go to the path: **/etc/ssl/ :**&#x20;

```bash
cd /etc/ssl/
cat dashboardapi.hicare.in.crt dashboardapi.hicare.in.ca-bundle >> ssl-bundle.crt
```

7. Now, go to the config nginx default file.

```bash
cd /etc/nginx/sites-available/
mv default default2
sudo nano default
```

```bash
server {
    listen 80;
    listen        443 ssl; #better to use this
    server_name   dashboardapi.hicare.in;

#ssl on; #ssl on is deprecated now.

ssl_certificate /etc/ssl/ssl-bundle.crt;
ssl_certificate_key /etc/ssl/dashboardapi_hicare_in.pem;

#global http handler

if ($scheme = http){
return 301 https://dashboardapi.hicare.in$request_uri;
}

ssl_stapling on;
ssl_stapling_verify on;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    location /omdashboard/ {
        proxy_pass         http://127.0.0.1:5000/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }

    location /rmdashboard/ {
        proxy_pass         http://127.0.0.1:5001/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }

    location /portalapi/ {
        proxy_pass         http://127.0.0.1:5002/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }
}

```

8. Changes here in configuration:&#x20;

```bash
    listen        443 ssl;
    server_name   dashboardapi.hicare.in;
    
    

if ($scheme = http){
return 301 https://dashboardapi.hicare.in$request_uri;
}

ssl_stapling on;
ssl_stapling_verify on;
```

```bash
sudo nginx -t
sudo nginx -s reload
sudo systemctl restart nginx
```

<figure><img src="../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

#### :tada: Congrats, your website is hosted on [dashboardapi.hicare.in](https://dashboardapi.hicare.in/) and auto redirected (HTTP to HTTPS) with SSL Certificate.

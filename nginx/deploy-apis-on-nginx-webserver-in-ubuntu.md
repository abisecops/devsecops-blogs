---
description: 'Deploy OM_Dashboard and RM_Dashboard APIs on nginx (ec2: Ubuntu Server)'
---

# Deploy APIs on Nginx webserver in Ubuntu

Steps:&#x20;

1. Update and upgrade the system:&#x20;

```bash
sudo apt update && sudo apt upgrade -y
```

2. Then install dot-net (required version). In my case, I am using **8.0**.

```bash
wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install -y dotnet-host
sudo apt-get install -y dotnet-sdk-8.0
sudo apt install -y aspnetcore-runtime-8.0
sudo apt install -y dotnet-runtime-8.0
sudo apt update 
```

In case you're getting conflict, you can also use:&#x20;

```bash
sudo apt-get install apt-transport-https
sudo apt-get update 
sudo apt-get install -f -y dotnet-host 
sudo apt-get install -f -y dotnet-sdk-8.0
sudo apt install -f -y aspnetcore-runtime-8.0
sudo apt install -f -y dotnet-runtime-8.0
sudo apt update
sudo apt upgrade -y 
```

3. Check the **dot-net** version and info:

```bash
dotnet --version
dotnet --info
```

4. Get the file:&#x20;

&#x20;    Method: **git, wget, scp**&#x20;

5. Now config and give the path to the OM\_Dashboard zip file:&#x20;

```bash
unzip OM_Dashboard.zip -d RM_Dashboard
sudo rm -rf OM_Dashboard.zip
sudo cp -r OM_Dashboard /var/www
cd /var/www/OM_Dashboard/OM_Dashboard
```

6. Now config and give the path to the OM\_Dashboard zip file:&#x20;

```bash
unzip RM_Dashboard.zip -d RM_Dashboard
sudo rm -rf RM_Dashboard.zip
sudo cp -r RM_Dashboard /var/www
cd /var/www/RM_Dashboard/RM_Dashboard
```

7. Both should have exe and dll. (Choose the dll with name of exe)&#x20;
8. Let's create the service to deploy  OM\_Dashboard api first.

```bash
cd /etc/systemd/system
sudo nano omdashboard.service
```

```bash
[Unit]
Description=ASP.NET Core Web App running on Ubuntu

[Service]
WorkingDirectory= /var/www/OM_Dashboard/OM_Dashboard
ExecStart=/usr/bin/dotnet /var/www/OM_Dashboard/OM_Dashboard/OM.Dashboards.API.dll
Restart=always
# Restart service after 10 seconds if the dotnet service crashes:
RestartSec=10
KillSignal=SIGINT
SyslogIdentifier=dotnet-web-app
# This user should exist on the server and have ownership of the deployment directory
User=www-data
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target
```

Now turn for RM\_Dashboard

```bash
sudo nano rmdashboard.service
```

```bash
[Unit]
Description=ASP.NET Core Web App running on Ubuntu

[Service]
WorkingDirectory= /var/www/RM_Dashboard/RM_Dashboard
ExecStart=/usr/bin/dotnet /var/www/RM_Dashboard/RM_Dashboard/RM.Dashboards.API.dll --urls=http://0.0.0.0:5001
Restart=always
# Restart service after 10 seconds if the dotnet service crashes:
RestartSec=10
KillSignal=SIGINT
SyslogIdentifier=dotnet-web-app
# This user should exist on the server and have ownership of the deployment directory
User=www-data
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target
```

9. Check enable, start and check status of both services

```bash
sudo systemctl enable omdashboard.service
sudo systemctl enable rmdashboard.service
sudo systemctl start omdashboard.service
sudo systemctl start rmdashboard.service
sudo systemctl status omdashboard.service
sudo systemctl status rmdashboard.service
```

10. Time to install  **nginx** too:&#x20;

```bash
sudo apt install nginx -y 
```

11. Enable and check status of nginx service

```bash
sudo systemctl enable nginx # It might be enabled by default (Optional)
sudo systemctl start nginx # (Optional)
sudo systemctl status nginx # Checks the status of the service
```

12. Let's config the nginx server:&#x20;

```bash
cd /etc/nginx/sites-available
ls
sudo mv default default2 # (Backup purpose)
sudo nano default # new default config file
```

For new **default** file:&#x20;

```bash
server {
    listen        80;
    server_name   localhost;

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

}
```

13. Now check the nginx file syntax/ status and reload nginx server:&#x20;

```bash
sudo nginx -t 
sudo nginx -s reload
sudo systemctl restart nginx
```

14. Now, your APIs are deployed successfully. :clap:\
    :link: [http://65.2.39.232/omdashboard](http://65.2.39.232/omdashboard)\
    :link:[http://65.2.39.232/rmdashboard](http://65.2.39.232/rmdashboard)

Note: These sites aren't accessible now but you can try your hosted URL as per your given location.&#x20;

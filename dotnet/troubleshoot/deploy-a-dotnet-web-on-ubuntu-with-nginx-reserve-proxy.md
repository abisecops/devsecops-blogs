---
description: Hosting dotnet webapp on nginx (ubuntu server)
---

# Deploy a Dotnet Web on Ubuntu with Nginx Reserve Proxy

{% embed url="https://lunawen.com/devops/20220409-luna-tech-deploy-dotnet-webapi-ubuntu/" %}

```
// Some code
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ cat default
server {
    listen        80;
    location / {
        proxy_pass         http://127.0.0.1:5000/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }

    location /cc/ {
        proxy_pass         http://127.0.0.1:5000/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }

    location /portal/ {
        proxy_pass         http://127.0.0.1:5000/;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }


}
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ 
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ sudo nginx -t 
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ sudo nginx -s reload
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ sudo systemctl restart nginx

sudo netstat -tulpn 
```

{% embed url="https://code-maze.com/deploy-aspnetcore-linux-nginx/" %}

```
// Some code
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ sudo lsof -i:5000
COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dotnet  6923 www-data  268u  IPv4  59354      0t0  TCP localhost:5000 (LISTEN)
dotnet  6923 www-data  269u  IPv6  59358      0t0  TCP ip6-localhost:5000 (LISTEN)
ubuntu@ip-172-31-15-149:/etc/nginx/sites-available$ 


```

{% embed url="https://www.cyberciti.biz/faq/unix-linux-check-if-port-is-in-use-command/" %}

```
// Some code
hicareadmin@hicareH61S:~$ dotnet --info
You must install or update .NET to run this application.

App: /usr/lib/dotnet/sdk/7.0.115/dotnet.dll
Architecture: x64
Framework: 'Microsoft.NETCore.App', version '7.0.15' (x64)
.NET location: /usr/lib/dotnet/

The following frameworks were found:
  7.0.2 at [/usr/lib/dotnet/shared/Microsoft.NETCore.App]

Learn about framework resolution:
https://aka.ms/dotnet/app-launch-failed

To install missing framework, download:
https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=7.0.15&arch=x64&rid=ubuntu.22.04-x64

Host:
  Version:      7.0.15
  Architecture: x64
  Commit:       8f4568cdaa

.NET SDKs installed:
  7.0.115 [/usr/lib/dotnet/sdk]

.NET runtimes installed:
  Microsoft.NETCore.App 7.0.2 [/usr/lib/dotnet/shared/Microsoft.NETCore.App]

Other architectures found:
  None

Environment variables:
  DOTNET_ROOT       [/snap/dotnet-sdk/current]

global.json file:
  /home/hicareadmin/global.json

Learn more:
  https://aka.ms/dotnet/info

Download .NET:
  https://aka.ms/dotnet/download
hicareadmin@hicareH61S:~$ 


```

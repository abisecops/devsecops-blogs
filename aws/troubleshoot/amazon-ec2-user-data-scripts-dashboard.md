# Amazon EC2 User Data Scripts Dashboard

Links:&#x20;

* [https://medium.com/@jeetanshu/unlocking-the-power-of-user-data-in-ec2-instances-on-aws-part-2-1a399f577ae6](https://medium.com/@jeetanshu/unlocking-the-power-of-user-data-in-ec2-instances-on-aws-part-2-1a399f577ae6)
* [https://www.cloud-plusplus.com/post/amazon-ec2-user-data-scripts-configuration](https://www.cloud-plusplus.com/post/amazon-ec2-user-data-scripts-configuration)



<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

```bash
sudo nano userdata.sh
```

```bash
#!/bin/bash

set -x

# Install dependencies
sudo apt update
sudo apt install -y apt-transport-https cargo jq wget curl build-essential libssl-dev pkg-config

# Update and upgrade packages
sudo apt upgrade -y > /dev/null 2>&1

# Purge existing NGINX installation and remove /etc/nginx/
sudo apt purge nginx nginx-common nginx-core -y > /dev/null 2>&1
sudo rm -rf /etc/nginx/ > /dev/null 2>&1
sudo apt autoremove --purge -y > /dev/null 2>&1

# Add Microsoft package repository for .NET SDK with a timeout of 30 seconds
wget --timeout=30 https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb

sudo dpkg -i packages-microsoft-prod.deb > /dev/null 2>&1
rm packages-microsoft-prod.deb

# Update package lists
sudo apt update > /dev/null 2>&1

# Install .NET SDK and dependencies
sudo apt install -y dotnet-host dotnet-sdk-8.0 aspnetcore-runtime-8.0 dotnet-runtime-8.0 > /dev/null 2>&1

# Install Nginx
sudo apt install -y nginx nginx-extras nginx-common > /dev/null 2>&1

# Allow TCP traffic for NGINX and specified ports
sudo ufw allow 'Nginx Full' > /dev/null 2>&1
sudo ufw allow 5000/tcp > /dev/null 2>&1
sudo ufw allow 5001/tcp > /dev/null 2>&1
sudo ufw allow 5002/tcp > /dev/null 2>&1
sudo ufw allow 3200/tcp > /dev/null 2>&1

# Create NGINX configuration file
sudo tee /etc/nginx/sites-available/default > /dev/null <<'EOT'
server {
    listen 80;
    more_set_headers 'Server: hicare';

    root /var/www/html;

    location / {
        try_files $uri $uri/ =404;
    }

    location /omdashboard/ {
        proxy_pass http://127.0.0.1:5000/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /rmdashboard/ {
        proxy_pass http://127.0.0.1:5001/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /portalapi/ {
        proxy_pass http://127.0.0.1:5002/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /sysinfo/ {
        proxy_pass http://127.0.0.1:3200/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
EOT

# Create a symbolic link to enable the site
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/ > /dev/null 2>&1

# Reload NGINX to apply changes
sudo systemctl reload nginx > /dev/null 2>&1

# Grant read and execute permissions to the NGINX user for the /var/www/html directory and its contents
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html

# Build and install sysinfo-web
cargo install --git https://github.com/onur/sysinfo-web > /dev/null 2>&1

# Create sysinfo-web service file
sudo tee /etc/systemd/system/sysinfo-web.service > /dev/null <<'EOT'
[Unit]
Description=Sysinfo Web Service
After=network.target

[Service]
Type=simple
ExecStart=/home/ubuntu/.cargo/bin/sysinfo-web 0.0.0.0:3200
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOT

# Reload systemd
sudo systemctl daemon-reload > /dev/null 2>&1

# Start and enable sysinfo-web service
sudo systemctl enable sysinfo-web > /dev/null 2>&1
sudo systemctl start sysinfo-web > /dev/null 2>&1

```



```bash
chmod 777 userdata.sh
```


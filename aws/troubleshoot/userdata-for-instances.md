# userdata for instances



```bash
#!/bin/bash

set -x

# Install dependencies
sudo apt update
sudo apt install -y apt-transport-https cargo jq wget curl build-essential libssl-dev pkg-config
sudo timedatectl set-timezone Asia/Kolkata

# Add Microsoft package repository for .NET SDK with a timeout of 30 seconds
wget --timeout=30 https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb

sudo add-apt-repository universe
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-8.0

# Install NGINX
sudo apt install -y nginx > /dev/null 2>&1

# Allow TCP traffic for NGINX and specified ports
sudo ufw allow 'Nginx Full' > /dev/null 2>&1
sudo ufw allow 5000/tcp > /dev/null 2>&1
sudo ufw allow 5001/tcp > /dev/null 2>&1
sudo ufw allow 5002/tcp > /dev/null 2>&1
sudo ufw allow 3200/tcp > /dev/null 2>&1
sudo ufw allow 80/tcp > /dev/null 2>&1

# Grant read and execute permissions to the NGINX user for the /var/www/html directory and its contents
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html

# Build and install sysinfo-web
cargo install sysinfo-web > /dev/null 2>&1

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

# Update NGINX configuration to include sysinfo web application
sudo tee /etc/nginx/sites-available/default > /dev/null <<'EOT'
server {
    listen 80;
    #listen [::]:80 default_server;

    root /var/www/html;

    index index.html index.htm index.nginx-debian.html;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
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

# Reload NGINX to apply changes
sudo nginx -t > /dev/null 2>&1
sudo nginx -s reload > /dev/null 2>&1
sudo systemctl restart nginx > /dev/null 2>&1
```



You can also do such a way:&#x20;

```bash
sudo nano userdata.sh
```

&#x20;**copy and paste**

then, provide permission

```bash
sudo chmod 777 userdata.sh
```

Checkout the port:&#x20;

```bash
netstat -tulpen
```

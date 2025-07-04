# Apache Tomcat

Today we're going to install and config tomcat.&#x20;

```bash
#!/bin/bash

# Step 1: Install Java
sudo apt-get update
sudo apt-get install -y default-jdk

# Step 2: Create Tomcat User and Group
sudo groupadd tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat

# Step 3: Download Tomcat 10
cd /opt
sudo wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.19/bin/apache-tomcat-10.1.19.tar.gz
sudo tar xzvf apache-tomcat-10*tar.gz
sudo mv apache-tomcat-10.1.19 tomcat

# Step 4: Update Permissions
sudo chgrp -R tomcat /opt/tomcat
sudo chmod -R g+rwx /opt/tomcat/conf
sudo chmod g+x /opt/tomcat/conf
sudo chown -R tomcat /opt/tomcat/webapps/ /opt/tomcat/work/ /opt/tomcat/temp/ /opt/tomcat/logs/

# Step 5: Create a systemd Service File
sudo tee /etc/systemd/system/tomcat.service <<EOF
[Unit]
Description=Apache Tomcat 10 Web Application Container
After=network.target

[Service]
Type=forking

Environment=JAVA_HOME=/usr/lib/jvm/default-java
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
EOF

# Step 6: Reload systemd
sudo systemctl daemon-reload

# Step 7: Start and enable Tomcat service
sudo systemctl start tomcat
sudo systemctl enable tomcat

# Step 8: Allow port 8080 in firewall
sudo ufw allow 8080

# Step 9: Deploy WAR file
sudo cp ~/Documents/war/sample.war /opt/tomcat/webapps/

# Step 10: Restart Tomcat
sudo systemctl restart tomcat

# Step 11: Verify Tomcat status
sudo systemctl status tomcat

```

<figure><img src="../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

sample.war makes sample folder ultimately when we move the .war file.&#x20;

* You can try any of your war file and browse the path as the given.

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

Some resource I used :&#x20;

{% embed url="https://www.ubuntumint.com/install-apache-tomcat-ubuntu/" %}

{% embed url="https://anamul-haque.medium.com/how-to-install-tomcat-on-ubuntu-and-deploy-war-file-in-tomcat-24039e8c3278" %}

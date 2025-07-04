---
description: 'Installing Docker and Docker Compose on an Ubuntu server:'
---

# Installing Docker and Docker Compose on an Ubuntu server:

### Installing Docker on Ubuntu:

1.  **Update Package Index**:&#x20;

    ```bash
    sudo apt update
    ```
2.  **Install Dependencies**: Install the packages necessary to allow apt to use a repository over HTTPS:

    ```bash
    sudo apt install apt-transport-https ca-certificates curl software-properties-common
    ```
3.  **Add Docker's Official GPG Key**: Add Docker’s official GPG key to your system:

    ```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    ```
4.  **Set Up the Stable Repository**: Add the Docker repository to APT sources:

    ```bash
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    ```
5.  **Update the Package Database**: Update the package database with Docker packages from the newly added repo:

    ```bash
    sudo apt update
    ```
6.  **Install Docker CE**: Install Docker Community Edition (CE):

    ```bash
    sudo apt install docker-ce
    ```
7.  **Verify Docker Installation**: Check that Docker is installed correctly by running the `hello-world` image:

    ```bash
    sudo docker run hello-world
    ```

#### Installing Docker Compose:

1.  **Download Docker Compose Binary**:

    * Check the latest release of Docker Compose from the [official GitHub repository](https://github.com/docker/compose/releases).
    * Replace `VERSION` with the latest release version:

    ```bash
    sudo curl -L "https://github.com/docker/compose/releases/download/VERSION/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    ```
2.  **Apply Executable Permissions**:

    ```bash
    sudo chmod +x /usr/local/bin/docker-compose
    ```
3.  **Create Symbolic Link**:

    ```bash
    sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
    ```
4.  **Verify Docker Compose Installation**:

    ```bash
    docker-compose --version
    ```

#### Post-Installation Steps:

1.  **Manage Docker as a Non-root User (Optional)**:

    * If you want to run Docker commands without `sudo`, add your user to the `docker` group:

    ```bash
    sudo usermod -aG docker $USER
    ```

    * Log out and log back in to apply the group membership changes.
2.  **Restart Docker Service**:

    ```bash
    sudo systemctl restart docker
    ```
3.  **Test Docker Compose**:

    * Create a `docker-compose.yml` file in your project directory.
    * Define services and configurations in the `docker-compose.yml`.
    * Run `docker-compose up` to start the services defined in the YAML file.



### Automation Script:&#x20;

```bash
#!/bin/bash

# Install Docker
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker.io

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Add current user to the docker group
sudo usermod -aG docker $USER

# Prompt user to log out and log back in to apply group membership changes
echo "Please log out and log back in to apply group membership changes."
```

Save the script to a file, for example, `install_docker.sh`, then make it executable:

```bash
chmod +x install_docker.sh
```

To execute the script, run:

```bash
./install_docker.sh
```

####

#### Conclusion:

You have now successfully installed Docker and Docker Compose on your Ubuntu server. This setup enables you to manage and deploy containerized applications efficiently.&#x20;

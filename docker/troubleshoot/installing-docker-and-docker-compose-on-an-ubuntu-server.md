---
description: 'Installing Docker and Docker Compose on an Ubuntu server:'
---

# Installing Docker and Docker Compose on an Ubuntu server:

### Installing Docker on Ubuntu:

1.  **Update Package Index**:

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
3. **Test Docker Compose**:
   * Create a `docker-compose.yml` file in your project directory.
   * Define services and configurations in the `docker-compose.yml`.
   * Run `docker-compose up` to start the services defined in the YAML file.

### Automation Script:

```bash
#!/bin/bash

set -euo pipefail

# ============================================================
# Docker Engine + Docker Compose Installation Script
# Supports Ubuntu / Debian
# ============================================================

echo "=============================================="
echo " Docker Engine & Docker Compose Installation"
echo "=============================================="

# ------------------------------------------------------------
# 1. Check root privileges
# ------------------------------------------------------------

if [[ $EUID -eq 0 ]]; then
    SUDO=""
else
    if ! command -v sudo >/dev/null 2>&1; then
        echo "ERROR: sudo is not installed."
        exit 1
    fi
    SUDO="sudo"
fi

# ------------------------------------------------------------
# 2. Detect OS
# ------------------------------------------------------------

if [[ ! -f /etc/os-release ]]; then
    echo "ERROR: Cannot detect operating system."
    exit 1
fi

source /etc/os-release

case "$ID" in
    ubuntu|debian)
        ;;
    *)
        echo "ERROR: This script supports Ubuntu and Debian only."
        echo "Detected OS: $ID"
        exit 1
        ;;
esac

echo "Detected OS: $PRETTY_NAME"

# ------------------------------------------------------------
# 3. Install required packages
# ------------------------------------------------------------

echo
echo "[1/8] Installing prerequisites..."

$SUDO apt-get update

$SUDO apt-get install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# ------------------------------------------------------------
# 4. Add Docker GPG key
# ------------------------------------------------------------

echo
echo "[2/8] Configuring Docker repository..."

$SUDO install -m 0755 -d /etc/apt/keyrings

if [[ "$ID" == "ubuntu" ]]; then
    DOCKER_KEYRING="/etc/apt/keyrings/docker.asc"
    DOCKER_REPO="https://download.docker.com/linux/ubuntu"
else
    DOCKER_KEYRING="/etc/apt/keyrings/docker.asc"
    DOCKER_REPO="https://download.docker.com/linux/debian"
fi

if [[ ! -f "$DOCKER_KEYRING" ]]; then
    $SUDO curl -fsSL \
        "$DOCKER_REPO/gpg" \
        -o "$DOCKER_KEYRING"
fi

$SUDO chmod a+r "$DOCKER_KEYRING"

# ------------------------------------------------------------
# 5. Add official Docker repository
# ------------------------------------------------------------

ARCH="$(dpkg --print-architecture)"
CODENAME="${VERSION_CODENAME:-$(lsb_release -cs)}"

echo "Architecture : $ARCH"
echo "Codename     : $CODENAME"

$SUDO tee /etc/apt/sources.list.d/docker.list >/dev/null <<EOF
deb [arch=$ARCH signed-by=$DOCKER_KEYRING] $DOCKER_REPO $CODENAME stable
EOF

$SUDO apt-get update

# ------------------------------------------------------------
# 6. Install Docker Engine
# ------------------------------------------------------------

echo
echo "[3/8] Installing Docker Engine..."

$SUDO apt-get install -y \
    docker-ce \
    docker-ce-cli \
    containerd.io \
    docker-buildx-plugin \
    docker-compose-plugin

# ------------------------------------------------------------
# 7. Enable and start Docker
# ------------------------------------------------------------

echo
echo "[4/8] Starting Docker service..."

$SUDO systemctl enable docker
$SUDO systemctl start docker

# ------------------------------------------------------------
# 8. Add current user to Docker group
# ------------------------------------------------------------

CURRENT_USER="${SUDO_USER:-$USER}"

echo
echo "[5/8] Configuring Docker group..."

if ! getent group docker >/dev/null 2>&1; then
    $SUDO groupadd docker
fi

if id "$CURRENT_USER" >/dev/null 2>&1; then
    $SUDO usermod -aG docker "$CURRENT_USER"
    echo "Added $CURRENT_USER to the docker group."
else
    echo "WARNING: Could not determine current user."
fi

# ------------------------------------------------------------
# 9. Verify Docker
# ------------------------------------------------------------

echo
echo "[6/8] Verifying Docker installation..."

DOCKER_VERSION=$($SUDO docker --version)
COMPOSE_VERSION=$($SUDO docker compose version)

echo
echo "Docker  : $DOCKER_VERSION"
echo "Compose : $COMPOSE_VERSION"

# ------------------------------------------------------------
# 10. Test Docker Engine
# ------------------------------------------------------------

echo
echo "[7/8] Testing Docker..."

$SUDO docker run --rm hello-world

# ------------------------------------------------------------
# 11. Installation summary
# ------------------------------------------------------------

echo
echo "[8/8] Installation completed successfully!"
echo
echo "=============================================="
echo " Installation Summary"
echo "=============================================="
echo "Docker:"
$SUDO docker --version

echo
echo "Docker Compose:"
$SUDO docker compose version

echo
echo "Docker Service:"
$SUDO systemctl is-active docker

echo
echo "=============================================="
echo " IMPORTANT"
echo "=============================================="
echo
echo "Your user was added to the docker group."
echo
echo "Log out and log back in, or run:"
echo
echo "    newgrp docker"
echo
echo "Then test without sudo:"
echo
echo "    docker run hello-world"
echo
echo "Check Docker:"
echo "    docker ps"
echo
echo "Check Compose:"
echo "    docker compose version"
echo
echo "=============================================="
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

You have now successfully installed Docker and Docker Compose on your Ubuntu server. This setup enables you to manage and deploy containerized applications efficiently.

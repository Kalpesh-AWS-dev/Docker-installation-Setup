# Docker Installation Tutorial

This tutorial provides step-by-step instructions for installing Docker on **Linux**, **Windows**, and **macOS** systems.

---

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation Steps](#installation-steps)
   - [Linux (Ubuntu Example)](#on-linux-ubuntu-example)
   - [Windows](#on-windows)
   - [macOS](#on-macos)
3. [Post-Installation Steps](#post-installation-steps)
4. [Common Commands](#common-commands)
5. [Uninstallation](#uninstallation)
6. [Troubleshooting](#troubleshooting)

---

## Prerequisites
### System Requirements
- **Linux**: Ubuntu 18.04 or later
- **Windows**: Windows 10 or later (Pro, Enterprise, or Education editions)
- **macOS**: macOS 10.14 or later

---

## Installation Steps

### On Linux (Ubuntu Example)
1. **Update the System:**
   ```bash
   sudo apt-get update
   sudo apt-get upgrade
   ```

2. **Install Required Packages:**
   ```bash
   sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add Docker’s Official GPG Key:**
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

4. **Set up the Stable Repository:**
   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

5. **Install Docker Engine:**
   ```bash
   sudo apt-get update
   sudo apt-get install -y docker-ce docker-ce-cli containerd.io
   ```

6. **Verify Installation:**
   ```bash
   docker --version
   ```

7. **Run Docker Without Root Privileges:**
   ```bash
   sudo groupadd docker
   sudo usermod -aG docker $USER
   newgrp docker
   ```

8. **Test Docker Installation:**
   ```bash
   docker run hello-world
   ```

---

### On Windows
1. **Download Docker Desktop:**
   - Go to the [Docker Desktop official website](https://www.docker.com/products/docker-desktop/) and download the installer.

2. **Install Docker Desktop:**
   - Run the installer and follow the on-screen instructions.
   - Restart your system if prompted.

3. **Enable WSL 2 (Optional):**
   - Install and configure [Windows Subsystem for Linux 2 (WSL 2)](https://docs.microsoft.com/en-us/windows/wsl/install) for improved performance.

4. **Verify Installation:**
   ```bash
   docker --version
   ```

5. **Test Docker Installation:**
   ```bash
   docker run hello-world
   ```

---

### On macOS
1. **Download Docker Desktop:**
   - Visit the [Docker Desktop official website](https://www.docker.com/products/docker-desktop/) and download the macOS installer.

2. **Install Docker Desktop:**
   - Open the `.dmg` file and drag Docker to the Applications folder.
   - Launch Docker and follow the setup instructions.

3. **Verify Installation:**
   ```bash
   docker --version
   ```

4. **Test Docker Installation:**
   ```bash
   docker run hello-world
   ```

---

## Post-Installation Steps
### Enable Auto-Start (Linux Only)
```bash
sudo systemctl enable docker
```

### Configure Docker for Non-Root Users
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

---

## Common Commands
| Command                         | Description                                   |
|---------------------------------|-----------------------------------------------|
| `docker ps`                     | List running containers                      |
| `docker images`                 | List downloaded images                       |
| `docker run <image>`            | Run a container from an image                |
| `docker stop <container_id>`    | Stop a running container                     |
| `docker rm <container_id>`      | Remove a container                           |
| `docker rmi <image_id>`         | Remove an image                              |
| `docker logs <container_id>`    | View container logs                          |
| `docker exec -it <container_id>`| Run commands inside a running container       |

---

## Uninstallation
### On Linux
```bash
sudo apt-get purge -y docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker
```

### On Windows and macOS
- Use the standard uninstallation process through the system settings.

---

## Troubleshooting
### Common Issues and Solutions
- **Permissions Error:**  
  Ensure your user is added to the `docker` group:
  ```bash
  sudo usermod -aG docker $USER
  ```

- **Check Docker Logs (Linux):**  
  ```bash
  sudo journalctl -u docker.service
  ```

- **Container Fails to Start:**  
  Check container logs:
  ```bash
  docker logs <container_id>
  ```

---

For more detailed information, visit the official [Docker Documentation](https://docs.docker.com/).


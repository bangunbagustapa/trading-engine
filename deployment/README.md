# Deployment Guide

## Prerequisites
- Ubuntu 20.04+ or Debian 10+
- User with sudo privileges

## 1. Update System
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl ca-certificates gnupg ufw
```

## 2. Configure Firewall
```bash
sudo ufw allow 22/tcp
sudo ufw allow 5678/tcp
sudo ufw --force enable
sudo ufw status
```

## 3. Install Docker

### 3.1 Add Docker's Official GPG Key
```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### 3.2 Add Docker Repository
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 3.3 Install Docker Packages
```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 3.4 Start and Enable Docker
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### 3.5 Verify Installation
```bash
sudo docker --version
sudo docker compose version
```

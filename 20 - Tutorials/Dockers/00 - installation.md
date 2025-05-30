# Installation Guide
## Official Docker Installation
```bash

# update package index
sudo apt update

# install requirement package
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release

# add docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# add docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# update package index (again)
sudo apt update

# install docker enginee
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# verify installation
sudo docker run hello-world
```

## Post-Installation Configuration
```bash
# add your user to the docker group
sudo usermod -aG docker $USER

# Log out and log back in, or run:
newgrp docker

# test without sudo
docker run hello-world

# enable docker to start on boot
sudo systemctl enable docker.service
sudo systemctl enable containerd.service

# check docker service status
sudo systemctl status docker
```

## Verify Installation
```bash
# check docker version
docker --version
docker version

# check docker info
docker info

# run a test container
## Run an Ubuntu container interactively
docker run -it ubuntu bash

## Inside the container, you can run:
cat /etc/os-release
exit
```

# Uninstall Docker Guide
```bash
sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```
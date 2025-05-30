## Permission Denied
```bash
# Error: Got permission denied while trying to connect to Docker daemon
# Solution: Make sure you're in the docker group
groups $USER
# If docker is not listed, run:
sudo usermod -aG docker $USER
newgrp docker
```

## Docker Service Not Running
```bash
# Check status
sudo systemctl status docker

# Start Docker service
sudo systemctl start docker

# Enable auto-start
sudo systemctl enable docker
```

## Old Docker Installation Conflicts
```bash
# Remove old installations
sudo apt remove docker docker-engine docker.io containerd runc

# Then follow the official installation steps
```
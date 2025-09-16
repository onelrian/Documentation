---
layout: page
title: Multipass Commands & VM Management
---

# Multipass Commands & VM Management

## Installation and Setup

### Installing Multipass
```bash
# Ubuntu/Debian
sudo snap install multipass

# macOS
brew install --cask multipass

# Windows
# Download from https://multipass.run/ or use Chocolatey:
choco install multipass
```

### Initial Configuration
```bash
# Check version
multipass version

# Get help
multipass help
multipass help <command>

# Set default driver (Linux/macOS)
multipass set local.driver=qemu
multipass set local.driver=virtualbox

# Set bridged interface
multipass set local.bridged-interface=eth0
```

## Instance Management

### Creating Instances
```bash
# Basic launch
multipass launch                    # Launch with random name
multipass launch --name myvm        # Launch with specific name
multipass launch 22.04              # Launch specific Ubuntu version
multipass launch jammy              # Launch by codename

# Advanced launch options
multipass launch --name dev-vm --cpus 2 --memory 4G --disk 20G
multipass launch --name web-server --cloud-init cloud-config.yaml
multipass launch --name bridge-vm --bridged
multipass launch --name mounted-vm --mount ./project:/home/ubuntu/project
```

### Instance Control
```bash
# Start instances
multipass start myvm                # Start specific instance
multipass start vm1 vm2 vm3         # Start multiple instances
multipass start --all               # Start all instances

# Stop instances
multipass stop myvm                 # Stop specific instance
multipass stop --all                # Stop all instances
multipass stop --force myvm         # Force stop

# Restart instances
multipass restart myvm              # Restart specific instance
multipass restart --all             # Restart all instances

# Suspend instances
multipass suspend myvm              # Suspend to disk
multipass suspend --all             # Suspend all instances
```

### Instance Information
```bash
# List instances
multipass list                      # Basic listing
multipass ls                        # Short alias
multipass list --format table       # Table format
multipass list --format csv         # CSV format
multipass list --format json        # JSON format

# Instance details
multipass info myvm                 # Detailed info for one instance
multipass info                      # Info for all instances
multipass info --format yaml myvm   # YAML format
```

### Deleting Instances
```bash
# Delete instances
multipass delete myvm               # Mark for deletion
multipass delete vm1 vm2 vm3        # Delete multiple instances
multipass delete --all              # Delete all instances

# Purge deleted instances
multipass purge                     # Permanently remove deleted instances

# Immediate deletion
multipass delete --purge myvm       # Delete and purge immediately

# Recover deleted instances
multipass recover myvm              # Recover before purge
multipass recover --all             # Recover all deleted instances
```

## Access and Interaction

### Shell Access
```bash
# Access instance shell
multipass shell myvm                # Shell into specific instance
multipass shell                     # Shell into primary instance

# Execute commands
multipass exec myvm -- ls -la       # Execute single command
multipass exec myvm -- "cd /home && pwd"  # Execute with shell
multipass exec myvm -- sudo apt update    # Execute with sudo
```

### File Transfer
```bash
# Transfer files
multipass transfer file.txt myvm:/home/ubuntu/
multipass transfer myvm:/home/ubuntu/result.txt ./
multipass transfer -r ./directory myvm:/home/ubuntu/

# Transfer with different options
multipass transfer --parents file.txt myvm:/path/to/dest/
```

## File System Operations

### Mount Operations
```bash
# Mount directories
multipass mount . myvm:/mnt/host     # Mount current directory
multipass mount /host/path myvm:/vm/path  # Mount specific path
multipass mount --uid-map 1000:1000 --gid-map 1000:1000 ./project myvm:/home/ubuntu/project

# List mounts
multipass info myvm                 # Shows mount information

# Unmount directories
multipass umount myvm:/mnt/host     # Unmount specific path
multipass umount myvm               # Unmount all mounts for instance
```

## Image Management

### Available Images
```bash
# Find available images
multipass find                      # List all available images
multipass find 22.04                # Find specific version
multipass find --format table       # Table format
multipass find --format json        # JSON format

# Common Ubuntu releases
multipass find | grep -E "(20.04|22.04|24.04)"
```

### Custom Images
```bash
# Launch from URL
multipass launch file:///path/to/image.img --name custom-vm
multipass launch https://cloud-images.ubuntu.com/releases/22.04/release/ubuntu-22.04-server-cloudimg-amd64.img
```

## Cloud-Init Configuration

### Basic Cloud-Init
```yaml
# cloud-config.yaml
#cloud-config
users:
  - name: developer
    sudo: ALL=(ALL) NOPASSWD:ALL
    shell: /bin/bash
    ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2E...

packages:
  - git
  - curl
  - vim
  - htop

runcmd:
  - apt update
  - apt upgrade -y
  - echo "Setup complete" > /home/developer/setup.log
```

### Advanced Cloud-Init Examples
```yaml
# Development environment setup
#cloud-config
packages:
  - git
  - nodejs
  - npm
  - python3
  - python3-pip
  - docker.io

runcmd:
  - usermod -aG docker ubuntu
  - systemctl enable docker
  - systemctl start docker
  - npm install -g yarn
  - pip3 install virtualenv

write_files:
  - path: /home/ubuntu/.bashrc
    append: true
    content: |
      alias ll='ls -la'
      alias la='ls -A'
      export PATH=$PATH:/usr/local/bin
```

### Using Cloud-Init
```bash
# Launch with cloud-init file
multipass launch --name dev-env --cloud-init cloud-config.yaml

# Launch with inline cloud-init
multipass launch --name test-vm --cloud-init - <<EOF
#cloud-config
packages:
  - nginx
runcmd:
  - systemctl enable nginx
  - systemctl start nginx
EOF
```

## Networking

### Network Configuration
```bash
# List available networks
multipass networks                  # Show available networks

# Launch with bridged networking
multipass launch --name bridge-vm --bridged
multipass launch --name net-vm --network bridged
multipass launch --name custom-net --network name=virbr0

# Set default bridged interface
multipass set local.bridged-interface=eth0
multipass set local.bridged-interface=wlan0
```

### Network Information
```bash
# Get instance IP
multipass info myvm | grep IPv4
multipass list                      # Shows IP addresses

# Network troubleshooting
multipass exec myvm -- ip addr show
multipass exec myvm -- ping google.com
multipass exec myvm -- netstat -tlnp
```

## Configuration Management

### Multipass Settings
```bash
# View all settings
multipass get

# View specific setting
multipass get local.driver
multipass get local.cpus
multipass get local.memory
multipass get local.disk

# Set configuration values
multipass set local.cpus=2
multipass set local.memory=2G
multipass set local.disk=10G
multipass set local.driver=qemu
multipass set local.bridged-interface=eth0
```

### Resource Defaults
```bash
# Set default resources for new instances
multipass set local.cpus=2
multipass set local.memory=4G
multipass set local.disk=20G

# Set timeout for operations
multipass set client.timeout=300
```

## Blueprints and Presets

### Using Blueprints
```bash
# Docker blueprint
multipass launch docker --name docker-vm

# Microk8s blueprint
multipass launch microk8s --name k8s-vm

# Minikube blueprint
multipass launch minikube --name minikube-vm

# List available blueprints
multipass find | grep -v "Image"
```

## Troubleshooting

### Common Issues
```bash
# Check multipass daemon status
multipass version                   # Check if daemon is running
sudo systemctl status multipass    # Linux systemd status

# View logs
multipass get local.log-level       # Check log level
multipass set local.log-level=debug # Enable debug logging

# Network troubleshooting
multipass exec myvm -- ping 8.8.8.8
multipass exec myvm -- nslookup google.com
multipass exec myvm -- ip route show

# Storage troubleshooting
multipass info myvm                 # Check disk usage
multipass exec myvm -- df -h       # Check disk space in VM
```

### Recovery Operations
```bash
# Restart multipass daemon
sudo systemctl restart multipass    # Linux
# On macOS/Windows, restart from system tray

# Reset instance
multipass stop myvm
multipass start myvm

# Clean up resources
multipass delete --all
multipass purge
```

## Automation and Scripting

### Batch Operations
```bash
# Start multiple instances
for vm in web db cache; do
    multipass launch --name $vm-server --cpus 2 --memory 2G
done

# Execute command on all instances
multipass list --format csv | tail -n +2 | cut -d, -f1 | while read vm; do
    multipass exec $vm -- sudo apt update
done

# Stop all running instances
multipass stop --all
```

### Useful Aliases
```bash
# Add to ~/.bashrc or ~/.zshrc
alias mp='multipass'
alias mpl='multipass launch'
alias mps='multipass shell'
alias mpls='multipass list'
alias mpi='multipass info'
alias mpstart='multipass start'
alias mpstop='multipass stop'
alias mpdel='multipass delete'

# Functions
mpnew() {
    multipass launch --name "$1" --cpus 2 --memory 2G --disk 10G
}

mpcp() {
    multipass transfer "$1" "$2"
}

mpexec() {
    multipass exec "$1" -- "${@:2}"
}
```

### Integration Scripts
```bash
#!/bin/bash
# setup-dev-env.sh - Create development environment

VM_NAME="dev-env"
CLOUD_CONFIG="dev-cloud-config.yaml"

# Create cloud-config
cat > $CLOUD_CONFIG << EOF
#cloud-config
packages:
  - git
  - vim
  - curl
  - build-essential
  - nodejs
  - npm

runcmd:
  - npm install -g yarn
  - echo "Development environment ready" > /home/ubuntu/setup-complete.txt
EOF

# Launch instance
multipass launch --name $VM_NAME --cpus 2 --memory 4G --disk 20G --cloud-init $CLOUD_CONFIG

# Wait for setup to complete
echo "Waiting for setup to complete..."
while ! multipass exec $VM_NAME -- test -f /home/ubuntu/setup-complete.txt; do
    sleep 5
done

echo "Development environment ready!"
multipass shell $VM_NAME
```

## Performance Optimization

### Resource Management
```bash
# Monitor resource usage
multipass info myvm                 # Check allocated resources
multipass exec myvm -- htop        # Monitor VM performance
multipass exec myvm -- free -h     # Check memory usage
multipass exec myvm -- df -h       # Check disk usage

# Optimize performance
multipass set local.cpus=4          # Increase default CPU
multipass set local.memory=8G       # Increase default memory
multipass launch --name fast-vm --cpus 4 --memory 8G --disk 50G
```

This comprehensive Multipass reference covers all essential commands for VM management and development workflows.

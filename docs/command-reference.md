# Multipass Command Reference

## Core Commands

### Instance Management

#### `multipass launch`
Create and start a new instance.

```bash
# Basic launch
multipass launch

# Launch with specific image
multipass launch 22.04

# Launch with custom name
multipass launch --name my-server

# Launch with custom resources
multipass launch --name dev-vm --cpus 2 --memory 4G --disk 20G

# Launch with cloud-init
multipass launch --name web-server --cloud-init cloud-config.yaml

# Launch with network bridging
multipass launch --name bridge-vm --bridged
```

**Options:**
- `--name <name>` - Set instance name
- `--cpus <number>` - Number of CPU cores (default: 1)
- `--memory <size>` - Memory size (default: 1G)
- `--disk <size>` - Disk size (default: 5G)
- `--cloud-init <file>` - Cloud-init configuration file
- `--network <spec>` - Network interface specification
- `--bridged` - Use bridged networking
- `--mount <source>:<target>` - Mount host directory
- `--timeout <seconds>` - Boot timeout (default: 300)

#### `multipass list`
List all instances and their status.

```bash
# List all instances
multipass list

# List with additional info
multipass list --format table
multipass list --format csv
multipass list --format json
```

#### `multipass info`
Show detailed information about instances.

```bash
# Info for all instances
multipass info

# Info for specific instance
multipass info my-vm

# Show only specific fields
multipass info --format yaml my-vm
```

#### `multipass start`
Start stopped instances.

```bash
# Start specific instance
multipass start my-vm

# Start multiple instances
multipass start vm1 vm2 vm3

# Start all instances
multipass start --all
```

#### `multipass stop`
Stop running instances.

```bash
# Stop specific instance
multipass stop my-vm

# Stop multiple instances
multipass stop vm1 vm2 vm3

# Stop all instances
multipass stop --all

# Force stop (immediate)
multipass stop --force my-vm
```

#### `multipass restart`
Restart instances.

```bash
# Restart specific instance
multipass restart my-vm

# Restart multiple instances
multipass restart vm1 vm2 vm3
```

#### `multipass suspend`
Suspend instances (save state to disk).

```bash
# Suspend specific instance
multipass suspend my-vm

# Suspend all instances
multipass suspend --all
```

#### `multipass delete`
Mark instances for deletion.

```bash
# Delete specific instance
multipass delete my-vm

# Delete multiple instances
multipass delete vm1 vm2 vm3

# Delete and purge immediately
multipass delete --purge my-vm
```

#### `multipass purge`
Permanently remove deleted instances.

```bash
# Purge all deleted instances
multipass purge
```

#### `multipass recover`
Recover deleted instances (before purge).

```bash
# Recover specific instance
multipass recover my-vm

# Recover all deleted instances
multipass recover --all
```

### Access and Interaction

#### `multipass shell`
Open shell in instance.

```bash
# Shell into primary instance
multipass shell

# Shell into specific instance
multipass shell my-vm

# Shell with specific user
multipass shell my-vm --user root
```

#### `multipass exec`
Execute commands in instance.

```bash
# Execute single command
multipass exec my-vm -- ls -la

# Execute with sudo
multipass exec my-vm -- sudo apt update

# Execute interactive command
multipass exec my-vm -- bash -c "cd /home && pwd"
```

#### `multipass transfer`
Transfer files between host and instance.

```bash
# Copy file to instance
multipass transfer myfile.txt my-vm:/home/ubuntu/

# Copy file from instance
multipass transfer my-vm:/home/ubuntu/result.txt ./

# Copy directory recursively
multipass transfer -r ./mydir my-vm:/home/ubuntu/

# Copy with different permissions
multipass transfer --parents myfile.txt my-vm:/path/to/dest/
```

### File System Operations

#### `multipass mount`
Mount host directories in instance.

```bash
# Mount current directory
multipass mount . my-vm:/mnt/host

# Mount with specific options
multipass mount --uid-map 1000:1000 --gid-map 1000:1000 ./project my-vm:/home/ubuntu/project

# Mount read-only
multipass mount --type classic ./data my-vm:/mnt/data
```

#### `multipass umount`
Unmount directories.

```bash
# Unmount specific path
multipass umount my-vm:/mnt/host

# Unmount all mounts for instance
multipass umount my-vm
```

### Image Management

#### `multipass find`
List available images.

```bash
# List all available images
multipass find

# Find specific image
multipass find 22.04

# Show detailed image info
multipass find --format table
```

#### `multipass get`
Get configuration values.

```bash
# Get all settings
multipass get

# Get specific setting
multipass get local.driver
```

#### `multipass set`
Set configuration values.

```bash
# Set driver
multipass set local.driver=virtualbox

# Set bridged interface
multipass set local.bridged-interface=en0

# Set CPU limit
multipass set local.cpus=4
```

### Network Commands

#### `multipass networks`
List available networks.

```bash
# List all networks
multipass networks

# List with details
multipass networks --format table
```

### Utility Commands

#### `multipass version`
Show version information.

```bash
multipass version
```

#### `multipass help`
Show help information.

```bash
# General help
multipass help

# Command-specific help
multipass help launch
multipass help mount
```

## Quick Reference Shortcuts

### Aliases for Common Operations
Add these to your shell configuration (`.bashrc`, `.zshrc`):

```bash
# Quick aliases
alias mp='multipass'
alias mpl='multipass launch'
alias mps='multipass shell'
alias mpls='multipass list'
alias mpi='multipass info'
alias mpstart='multipass start'
alias mpstop='multipass stop'
alias mpdel='multipass delete'

# Function for quick VM creation
mpnew() {
    multipass launch --name "$1" --cpus 2 --memory 2G --disk 10G
}

# Function for quick file transfer
mpcp() {
    multipass transfer "$1" "$2"
}
```

### Keyboard Shortcuts in Shell
- `Ctrl+D` - Exit shell session
- `Ctrl+C` - Interrupt current command
- `Ctrl+Z` - Suspend current process
- `Ctrl+L` - Clear screen

## Environment Variables

```bash
# Set default instance name
export MULTIPASS_DEFAULT_INSTANCE=my-vm

# Set custom socket path (Linux/macOS)
export MULTIPASS_SERVER_ADDRESS=/custom/path/multipassd.socket
```

## Configuration Locations

### Linux
- Config: `~/.config/multipass/`
- Images: `/var/snap/multipass/common/cache/`
- Instances: `/var/snap/multipass/common/data/multipassd/vault/instances/`

### macOS
- Config: `~/Library/Application Support/multipass/`
- Images: `~/Library/Caches/multipass/`
- Instances: `/var/root/Library/Application Support/multipassd/`

### Windows
- Config: `%APPDATA%\multipass\`
- Images: `%LOCALAPPDATA%\multipass\cache\`
- Instances: `C:\ProgramData\Multipass\data\`

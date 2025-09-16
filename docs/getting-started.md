# Getting Started with Multipass

## What is Multipass?

Multipass is a lightweight VM manager for Linux, Windows and macOS. It's designed for developers who want a fresh Ubuntu environment with a single command. It uses KVM on Linux, Hyper-V on Windows and HyperKit on macOS to run the VM with minimal overhead.

## Key Features

- **Fast**: Launch Ubuntu VMs in seconds
- **Lightweight**: Minimal resource overhead
- **Cross-platform**: Works on Linux, Windows, and macOS
- **Cloud-init support**: Customize instances on first boot
- **Network bridging**: Connect VMs to your local network
- **File sharing**: Mount host directories in VMs

## Installation

### Ubuntu/Debian
```bash
sudo snap install multipass
```

### macOS
```bash
brew install --cask multipass
```

### Windows
Download from the [official website](https://multipass.run/) or use Chocolatey:
```powershell
choco install multipass
```

## Quick Start

1. **Launch your first instance:**
   ```bash
   multipass launch --name my-vm
   ```

2. **Access the instance:**
   ```bash
   multipass shell my-vm
   ```

3. **List all instances:**
   ```bash
   multipass list
   ```

4. **Stop an instance:**
   ```bash
   multipass stop my-vm
   ```

5. **Delete an instance:**
   ```bash
   multipass delete my-vm
   multipass purge
   ```

## Next Steps

- [Command Reference](command-reference.md) - Complete list of all commands
- [Advanced Usage](advanced-usage.md) - Cloud-init, networking, and more
- [Troubleshooting](troubleshooting.md) - Common issues and solutions
- [Examples](examples/) - Real-world use cases and configurations

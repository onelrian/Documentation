# Package Managers & System Administration

## APT (Debian/Ubuntu/Mint)

### Basic Package Operations
```bash
# Update package database
sudo apt update                     # Update package lists
sudo apt upgrade                    # Upgrade installed packages
sudo apt full-upgrade               # Upgrade with dependency resolution
sudo apt dist-upgrade               # Distribution upgrade

# Package installation/removal
sudo apt install package            # Install package
sudo apt install package1 package2 # Install multiple packages
sudo apt install package=version    # Install specific version
sudo apt remove package             # Remove package (keep config)
sudo apt purge package              # Remove package and config files
sudo apt autoremove                 # Remove unused dependencies
sudo apt autoclean                  # Clean package cache

# Package information
apt search keyword                  # Search for packages
apt show package                    # Show package information
apt list --installed               # List installed packages
apt list --upgradable              # List upgradable packages
apt depends package                 # Show package dependencies
apt rdepends package               # Show reverse dependencies
```

### Advanced APT Usage
```bash
# Hold/unhold packages
sudo apt-mark hold package          # Prevent package updates
sudo apt-mark unhold package        # Allow package updates
apt-mark showhold                   # Show held packages

# Repository management
sudo add-apt-repository ppa:user/repo  # Add PPA repository
sudo add-apt-repository --remove ppa:user/repo  # Remove PPA
sudo apt edit-sources               # Edit sources list

# Package files and cache
apt-cache policy package            # Show package policy
apt-file search filename            # Find package containing file
dpkg -L package                     # List files in package
dpkg -S filename                    # Find package owning file
```

### Useful APT Aliases
```bash
# Add to ~/.bashrc or ~/.zshrc
alias agi='sudo apt install'
alias agr='sudo apt remove'
alias agp='sudo apt purge'
alias agu='sudo apt update'
alias agg='sudo apt upgrade'
alias agf='sudo apt full-upgrade'
alias ags='apt search'
alias agsh='apt show'
alias agl='apt list --installed'
alias aglu='apt list --upgradable'
alias agac='sudo apt autoclean'
alias agar='sudo apt autoremove'
alias agah='sudo apt-mark hold'
alias aguh='sudo apt-mark unhold'

# Combined operations
alias update='sudo apt update && sudo apt upgrade'
alias install='sudo apt install'
alias search='apt search'
```

## YUM/DNF (Red Hat/CentOS/Fedora)

### YUM Commands (CentOS 7 and older)
```bash
# Package management
sudo yum update                     # Update all packages
sudo yum install package            # Install package
sudo yum remove package             # Remove package
sudo yum autoremove                 # Remove unused dependencies

# Package information
yum search keyword                  # Search packages
yum info package                    # Package information
yum list installed                  # List installed packages
yum list available                  # List available packages
yum provides filename               # Find package providing file
yum history                         # Show transaction history

# Repository management
yum repolist                        # List repositories
sudo yum-config-manager --enable repo  # Enable repository
sudo yum-config-manager --disable repo # Disable repository
```

### DNF Commands (Fedora/CentOS 8+)
```bash
# Package management
sudo dnf update                     # Update all packages
sudo dnf upgrade                    # Same as update
sudo dnf install package            # Install package
sudo dnf remove package             # Remove package
sudo dnf autoremove                 # Remove unused dependencies

# Package information
dnf search keyword                  # Search packages
dnf info package                    # Package information
dnf list installed                  # List installed packages
dnf list available                  # List available packages
dnf provides filename               # Find package providing file
dnf history                         # Show transaction history

# Group operations
dnf group list                      # List package groups
sudo dnf group install "Group Name" # Install package group
sudo dnf group remove "Group Name"  # Remove package group
```

### YUM/DNF Aliases
```bash
# YUM aliases
alias yi='sudo yum install'
alias yr='sudo yum remove'
alias yu='sudo yum update'
alias ys='yum search'
alias ysh='yum info'
alias yl='yum list installed'

# DNF aliases
alias di='sudo dnf install'
alias dr='sudo dnf remove'
alias du='sudo dnf update'
alias ds='dnf search'
alias dsh='dnf info'
alias dl='dnf list installed'
```

## Pacman (Arch Linux/Manjaro)

### Basic Pacman Operations
```bash
# System update
sudo pacman -Syu                    # Update system (sync, refresh, upgrade)
sudo pacman -Syyu                   # Force refresh and update

# Package installation/removal
sudo pacman -S package              # Install package
sudo pacman -S package1 package2   # Install multiple packages
sudo pacman -R package              # Remove package
sudo pacman -Rs package             # Remove package and dependencies
sudo pacman -Rns package            # Remove package, deps, and config files
sudo pacman -Rdd package            # Force remove (skip dependency checks)

# Package information
pacman -Ss keyword                  # Search packages
pacman -Si package                  # Show package information
pacman -Q                           # List installed packages
pacman -Qs keyword                  # Search installed packages
pacman -Qi package                  # Show installed package info
pacman -Ql package                  # List files in package
pacman -Qo filename                 # Find package owning file
pacman -Qu                          # List upgradable packages
```

### Advanced Pacman Usage
```bash
# Database operations
sudo pacman -Sc                     # Clean package cache
sudo pacman -Scc                    # Clean all cache
sudo pacman -Sw package             # Download package only
pacman -Qdt                         # List orphaned packages
sudo pacman -Rs $(pacman -Qtdq)     # Remove orphaned packages

# File operations
pacman -Fl package                  # List files in package (from repos)
pacman -Fx filename                 # Find package containing file
sudo pacman -U package.pkg.tar.xz   # Install local package

# Hooks and logs
sudo pacman -Qkk                    # Check package integrity
tail -f /var/log/pacman.log         # Monitor pacman log
```

### Pacman Aliases
```bash
# Basic operations
alias paci='sudo pacman -S'         # Install
alias pacr='sudo pacman -R'         # Remove
alias pacrs='sudo pacman -Rs'       # Remove with dependencies
alias pacu='sudo pacman -Syu'       # Update system
alias pacs='pacman -Ss'             # Search
alias pacq='pacman -Q'              # Query installed
alias pacqi='pacman -Qi'            # Package info
alias pacql='pacman -Ql'            # List files
alias pacqo='pacman -Qo'            # Which package owns file
alias pacqu='pacman -Qu'            # List upgradable
alias pacsc='sudo pacman -Sc'       # Clean cache
alias pacscc='sudo pacman -Scc'     # Clean all cache

# Advanced operations
alias pacorphans='pacman -Qdt'
alias pacrmorphans='sudo pacman -Rs $(pacman -Qtdq)'
alias paclog='tail -f /var/log/pacman.log'
```

## Snap Packages

### Basic Snap Operations
```bash
# Package management
sudo snap install package           # Install snap package
sudo snap install --classic package # Install with classic confinement
sudo snap remove package            # Remove snap package
sudo snap refresh                   # Update all snaps
sudo snap refresh package           # Update specific snap

# Package information
snap find keyword                   # Search for snaps
snap info package                   # Show snap information
snap list                           # List installed snaps
snap list --all                     # Include disabled snaps
snap connections package            # Show snap connections

# Snap management
sudo snap disable package           # Disable snap
sudo snap enable package            # Enable snap
sudo snap revert package            # Revert to previous version
snap changes                        # Show recent changes
```

### Snap Aliases
```bash
alias sni='sudo snap install'
alias snr='sudo snap remove'
alias snu='sudo snap refresh'
alias sns='snap find'
alias snl='snap list'
alias sni='snap info'
```

## Flatpak

### Basic Flatpak Operations
```bash
# Package management
flatpak install package             # Install flatpak
flatpak install flathub package     # Install from specific remote
flatpak uninstall package           # Remove flatpak
flatpak update                      # Update all flatpaks
flatpak update package              # Update specific flatpak

# Package information
flatpak search keyword              # Search flatpaks
flatpak info package                # Show flatpak information
flatpak list                        # List installed flatpaks
flatpak list --app                  # List only applications

# Repository management
flatpak remotes                     # List remotes
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-delete remote        # Remove remote

# Application management
flatpak run package                 # Run flatpak application
flatpak kill package                # Kill running flatpak
```

## AppImage Management

### AppImage Operations
```bash
# Make executable and run
chmod +x application.AppImage
./application.AppImage

# Extract AppImage
./application.AppImage --appimage-extract

# Integration with system
# Install AppImageLauncher for automatic integration
sudo apt install appimagelauncher   # Ubuntu/Debian
```

## System Service Management

### Systemd Service Control
```bash
# Service status and control
sudo systemctl start service        # Start service
sudo systemctl stop service         # Stop service
sudo systemctl restart service      # Restart service
sudo systemctl reload service       # Reload service config
sudo systemctl status service       # Show service status
sudo systemctl enable service       # Enable service at boot
sudo systemctl disable service      # Disable service at boot
sudo systemctl mask service         # Mask service (prevent start)
sudo systemctl unmask service       # Unmask service

# System control
sudo systemctl reboot              # Reboot system
sudo systemctl poweroff            # Power off system
sudo systemctl suspend             # Suspend system
sudo systemctl hibernate           # Hibernate system

# Service information
systemctl list-units               # List all units
systemctl list-units --failed      # List failed units
systemctl list-unit-files          # List unit files
systemctl is-active service        # Check if service is active
systemctl is-enabled service       # Check if service is enabled
```

### Service Management Aliases
```bash
alias sctl='systemctl'
alias sctle='sudo systemctl enable'
alias sctld='sudo systemctl disable'
alias sctls='sudo systemctl start'
alias sctlr='sudo systemctl restart'
alias sctlst='systemctl status'
alias sctlstop='sudo systemctl stop'
alias sctlrel='sudo systemctl reload'

# Journal logs
alias jctl='journalctl'
alias jctlf='journalctl -f'         # Follow logs
alias jctlu='journalctl -u'         # Unit logs
alias jctlb='journalctl -b'         # Boot logs
alias jctlk='journalctl -k'         # Kernel logs
```

## Process Management

### Process Control Commands
```bash
# Process viewing
ps aux                              # All processes
ps -ef                              # All processes (different format)
pstree                              # Process tree
top                                 # Real-time process viewer
htop                                # Enhanced process viewer
jobs                                # Active jobs in shell

# Process control
kill PID                            # Terminate process
kill -9 PID                         # Force kill process
killall process_name                # Kill all processes by name
pkill pattern                       # Kill processes matching pattern
pgrep pattern                       # Find processes matching pattern
nohup command &                     # Run command immune to hangups

# Job control
bg                                  # Put job in background
fg                                  # Bring job to foreground
disown                              # Remove job from shell's job table
```

### Process Monitoring Aliases
```bash
alias psa='ps aux'
alias psg='ps aux | grep'
alias psr='ps aux | grep -v grep | grep'
alias cpu='ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head'
alias mem='ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head'
alias listening='ss -tuln'
alias ports='netstat -tulanp'
```

## File System Management

### Disk Usage and Management
```bash
# Disk space
df -h                               # Disk space usage
du -h directory                     # Directory size
du -sh *                            # Size of all items in current dir
ncdu                                # Interactive disk usage analyzer
lsblk                               # List block devices
fdisk -l                            # List disk partitions

# File system operations
sudo mount /dev/sdb1 /mnt           # Mount filesystem
sudo umount /mnt                    # Unmount filesystem
sudo fsck /dev/sdb1                 # Check filesystem
sudo mkfs.ext4 /dev/sdb1            # Create ext4 filesystem
```

### File System Aliases
```bash
alias df='df -h'
alias du='du -h'
alias dus='du -sh'
alias dush='du -sh * | sort -hr'
alias mount='mount | column -t'
alias lsblk='lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL'
```

## Network Package Managers

### NPM (Node.js)
```bash
# Package management
npm install package                 # Install locally
npm install -g package              # Install globally
npm uninstall package               # Remove package
npm update                          # Update packages
npm outdated                        # Show outdated packages

# Package information
npm search keyword                  # Search packages
npm info package                    # Package information
npm list                            # List installed packages
npm list -g                         # List global packages
```

### Pip (Python)
```bash
# Package management
pip install package                 # Install package
pip install --user package          # Install for user only
pip uninstall package               # Remove package
pip install --upgrade package       # Upgrade package
pip freeze                          # List installed packages
pip freeze > requirements.txt       # Export requirements

# Package information
pip search keyword                  # Search packages (deprecated)
pip show package                    # Package information
pip list                            # List installed packages
pip list --outdated                 # Show outdated packages
```

This comprehensive package management reference covers all major Linux package managers and system administration tools.

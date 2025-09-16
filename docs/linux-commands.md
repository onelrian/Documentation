# Linux System Commands & Shortcuts

## File System Navigation

### Basic Navigation
```bash
# Change directory
cd /path/to/directory
cd ~                    # Home directory
cd -                    # Previous directory
cd ..                   # Parent directory
cd ../..                # Two levels up

# List files and directories
ls                      # Basic listing
ls -la                  # Detailed listing with hidden files
ls -lh                  # Human readable sizes
ls -lt                  # Sort by modification time
ls -lS                  # Sort by size
ls -R                   # Recursive listing

# Print working directory
pwd

# Find files and directories
find /path -name "*.txt"
find . -type f -name "pattern"
find . -type d -name "dirname"
locate filename         # Fast file search (requires updatedb)
which command           # Find command location
whereis command         # Find command, source, manual
```

### File Operations
```bash
# Create files and directories
touch filename          # Create empty file
mkdir dirname           # Create directory
mkdir -p path/to/dir    # Create nested directories

# Copy files and directories
cp source dest          # Copy file
cp -r source dest       # Copy directory recursively
cp -i source dest       # Interactive copy (prompt before overwrite)
cp -u source dest       # Copy only if source is newer

# Move and rename
mv source dest          # Move/rename file or directory
mv file1 file2 dir/     # Move multiple files to directory

# Remove files and directories
rm filename             # Remove file
rm -i filename          # Interactive removal
rm -r dirname           # Remove directory recursively
rm -rf dirname          # Force remove directory (dangerous!)
rmdir dirname           # Remove empty directory

# Create links
ln target linkname      # Hard link
ln -s target linkname   # Symbolic link
```

## File Content Operations

### Viewing Files
```bash
# Display file contents
cat filename            # Display entire file
less filename           # Page through file
more filename           # Page through file (basic)
head filename           # First 10 lines
head -n 20 filename     # First 20 lines
tail filename           # Last 10 lines
tail -n 20 filename     # Last 20 lines
tail -f filename        # Follow file changes (live)

# Search in files
grep pattern filename   # Search for pattern
grep -r pattern dir/    # Recursive search
grep -i pattern file    # Case insensitive
grep -n pattern file    # Show line numbers
grep -v pattern file    # Invert match (exclude pattern)
```

### File Editing
```bash
# Text editors
nano filename           # Simple editor
vim filename            # Vi/Vim editor
emacs filename          # Emacs editor
gedit filename          # GUI text editor (GNOME)
kate filename           # GUI text editor (KDE)

# Stream editing
sed 's/old/new/g' file  # Replace text
awk '{print $1}' file   # Print first column
sort filename           # Sort lines
uniq filename           # Remove duplicate lines
wc filename             # Word, line, character count
wc -l filename          # Line count only
```

## System Information

### System Status
```bash
# System information
uname -a                # System information
hostnamectl             # System hostname info
uptime                  # System uptime and load
whoami                  # Current username
id                      # User and group IDs
w                       # Who is logged in
who                     # Currently logged users
last                    # Login history

# Hardware information
lscpu                   # CPU information
lsmem                   # Memory information
lsblk                   # Block devices
lsusb                   # USB devices
lspci                   # PCI devices
dmidecode               # Hardware details (requires root)
```

### Disk Usage
```bash
# Disk space
df -h                   # Disk space usage (human readable)
du -h directory         # Directory size
du -sh directory        # Summary of directory size
du -h --max-depth=1     # Size of subdirectories
ncdu                    # Interactive disk usage analyzer

# Disk operations
fdisk -l                # List disk partitions
mount                   # Show mounted filesystems
mount /dev/sdb1 /mnt    # Mount filesystem
umount /mnt             # Unmount filesystem
```

## Process Management

### Process Control
```bash
# View processes
ps aux                  # All running processes
ps -ef                  # All processes with full format
pstree                  # Process tree
top                     # Real-time process viewer
htop                    # Enhanced process viewer
jobs                    # Active jobs in current shell

# Process control
kill PID                # Terminate process by PID
kill -9 PID             # Force kill process
killall processname     # Kill all processes by name
pkill pattern           # Kill processes matching pattern
nohup command &         # Run command immune to hangups
bg                      # Put job in background
fg                      # Bring job to foreground
```

### System Control
```bash
# System services (systemd)
systemctl status service    # Check service status
systemctl start service     # Start service
systemctl stop service      # Stop service
systemctl restart service   # Restart service
systemctl enable service    # Enable service at boot
systemctl disable service   # Disable service at boot
systemctl list-units       # List all units

# System control
sudo reboot             # Restart system
sudo shutdown -h now    # Shutdown immediately
sudo shutdown -h +10    # Shutdown in 10 minutes
sudo shutdown -r now    # Restart immediately
```

## Network Commands

### Network Information
```bash
# Network interfaces
ip addr show            # Show IP addresses
ip route show           # Show routing table
ifconfig                # Network interface configuration (deprecated)
iwconfig                # Wireless interface configuration

# Network connectivity
ping hostname           # Test connectivity
ping -c 4 hostname      # Ping 4 times only
traceroute hostname     # Trace route to host
nslookup hostname       # DNS lookup
dig hostname            # DNS lookup (detailed)
host hostname           # DNS lookup (simple)

# Network monitoring
netstat -tuln           # Show listening ports
ss -tuln                # Show listening ports (modern)
lsof -i                 # Show network connections
iftop                   # Network usage by connection
nethogs                 # Network usage by process
```

### File Transfer
```bash
# Download files
wget URL                # Download file
wget -c URL             # Continue partial download
curl URL                # Transfer data from server
curl -O URL             # Download and save file

# Secure copy
scp file user@host:path # Copy file to remote host
scp user@host:file .    # Copy file from remote host
rsync -av source dest   # Synchronize directories
```

## Archive and Compression

### Archive Operations
```bash
# tar archives
tar -cvf archive.tar files      # Create tar archive
tar -xvf archive.tar            # Extract tar archive
tar -tvf archive.tar            # List tar contents
tar -czvf archive.tar.gz files  # Create compressed archive
tar -xzvf archive.tar.gz        # Extract compressed archive

# zip archives
zip archive.zip files           # Create zip archive
zip -r archive.zip directory    # Create zip with directory
unzip archive.zip               # Extract zip archive
unzip -l archive.zip            # List zip contents

# Other compression
gzip filename                   # Compress file
gunzip filename.gz              # Decompress file
```

## Keyboard Shortcuts (Terminal)

### Command Line Editing
- `Ctrl + A` - Move to beginning of line
- `Ctrl + E` - Move to end of line
- `Ctrl + U` - Delete from cursor to beginning
- `Ctrl + K` - Delete from cursor to end
- `Ctrl + W` - Delete word before cursor
- `Alt + D` - Delete word after cursor
- `Ctrl + Y` - Paste deleted text
- `Ctrl + L` - Clear screen
- `Ctrl + R` - Search command history
- `Ctrl + C` - Cancel current command
- `Ctrl + Z` - Suspend current command
- `Ctrl + D` - Exit shell or EOF

### History Navigation
- `↑` / `↓` - Navigate command history
- `!!` - Repeat last command
- `!n` - Repeat command number n
- `!string` - Repeat last command starting with string
- `^old^new` - Replace old with new in last command

### Tab Completion
- `Tab` - Auto-complete commands and filenames
- `Tab Tab` - Show all possible completions

## Environment Variables

### Common Variables
```bash
# View environment
env                     # Show all environment variables
echo $HOME              # Home directory
echo $PATH              # Executable search path
echo $USER              # Current username
echo $SHELL             # Current shell

# Set variables
export VAR=value        # Set environment variable
unset VAR               # Remove variable
```

### Shell Configuration
```bash
# Configuration files
~/.bashrc               # Bash configuration
~/.zshrc                # Zsh configuration
~/.profile              # Shell-independent profile
/etc/environment        # System-wide environment
```

## Permissions and Ownership

### File Permissions
```bash
# Change permissions
chmod 755 filename      # rwxr-xr-x
chmod +x filename       # Add execute permission
chmod -w filename       # Remove write permission
chmod u+r filename      # Add read for user
chmod g-w filename      # Remove write for group
chmod o=r filename      # Set read-only for others

# Change ownership
chown user filename     # Change owner
chown user:group file   # Change owner and group
chgrp group filename    # Change group only
```

### Permission Values
- `r` (read) = 4
- `w` (write) = 2  
- `x` (execute) = 1

Common combinations:
- `755` = rwxr-xr-x (executable files)
- `644` = rw-r--r-- (regular files)
- `600` = rw------- (private files)
- `777` = rwxrwxrwx (all permissions - avoid!)

## Text Processing

### Advanced Text Operations
```bash
# Cut and paste columns
cut -d: -f1 /etc/passwd     # Extract first field
cut -c1-10 filename         # Extract characters 1-10

# Text transformation
tr 'a-z' 'A-Z' < file       # Convert to uppercase
tr -d ' ' < file            # Delete spaces
rev filename                # Reverse lines

# Comparison
diff file1 file2            # Compare files
comm file1 file2            # Compare sorted files
cmp file1 file2             # Binary comparison
```

This reference covers the essential Linux commands and shortcuts for daily system administration and development work.

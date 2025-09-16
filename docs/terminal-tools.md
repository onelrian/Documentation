# Terminal Tools & Utilities

## File Management Tools

### Advanced File Operations
```bash
# fd - Modern find replacement
fd pattern                          # Find files/directories
fd -t f pattern                     # Files only
fd -t d pattern                     # Directories only
fd -e txt                           # Find by extension
fd -H pattern                       # Include hidden files
fd -I pattern                       # Don't respect .gitignore

# exa/eza - Modern ls replacement
exa -la                             # Detailed listing
exa --tree                          # Tree view
exa --git                           # Show git status
exa -T -L 2                         # Tree with depth limit

# bat - Better cat with syntax highlighting
bat filename                        # View file with highlighting
bat -n filename                     # Show line numbers
bat --style=plain filename          # Plain output
bat -A filename                     # Show all characters

# ripgrep (rg) - Fast grep replacement
rg pattern                          # Search in current directory
rg -i pattern                       # Case insensitive
rg -w pattern                       # Whole words only
rg -n pattern                       # Show line numbers
rg -C 3 pattern                     # Show 3 lines context
rg --type py pattern                # Search only Python files
rg -v pattern                       # Invert match
```

### File Navigation
```bash
# z/zoxide - Smart directory jumping
z directory                         # Jump to frequently used directory
zi                                  # Interactive selection
z foo bar                           # Jump to directory matching both

# fzf - Fuzzy finder
fzf                                 # Interactive file finder
find . -type f | fzf                # Find files with fuzzy search
history | fzf                       # Search command history
kill -9 $(ps aux | fzf | awk '{print $2}')  # Kill process interactively

# ranger - Terminal file manager
ranger                              # Launch file manager
# Navigation: hjkl, Enter to open, q to quit

# nnn - Lightweight file manager
nnn                                 # Launch file manager
# Navigation: arrows, Enter, q to quit
```

## System Monitoring

### Process and System Info
```bash
# htop - Interactive process viewer
htop                                # Enhanced top
# Keys: F1-help, F2-setup, F3-search, F4-filter, F5-tree, F9-kill, F10-quit

# btop - Modern system monitor
btop                                # Resource monitor with graphs

# glances - System monitoring
glances                             # Comprehensive system info
glances -w                          # Web interface mode

# neofetch - System information
neofetch                            # Display system info with ASCII art
neofetch --ascii_distro ubuntu      # Specific distro ASCII

# duf - Modern df replacement
duf                                 # Disk usage with colors
duf --hide-fs tmpfs,devtmpfs        # Hide specific filesystems

# ncdu - Disk usage analyzer
ncdu                                # Interactive disk usage
ncdu /path/to/directory             # Analyze specific directory
```

### Network Monitoring
```bash
# bandwhich - Network utilization by process
bandwhich                           # Show network usage by process

# iftop - Network usage by connection
iftop                               # Network traffic monitor
iftop -i eth0                       # Monitor specific interface

# nethogs - Network usage by process
nethogs                             # Per-process network usage
nethogs eth0                        # Monitor specific interface

# ss - Socket statistics
ss -tuln                            # Show listening ports
ss -tulpn                           # Show with process names
ss -s                               # Summary statistics
```

## Text Processing

### Advanced Text Tools
```bash
# jq - JSON processor
jq '.' file.json                    # Pretty print JSON
jq '.key' file.json                 # Extract specific key
jq '.[] | .name' file.json          # Extract names from array
curl -s api.url | jq '.data'        # Process API response

# yq - YAML processor
yq '.key' file.yaml                 # Extract YAML key
yq -i '.key = "value"' file.yaml    # Edit YAML in place

# miller (mlr) - CSV/JSON/TSV processor
mlr --csv cat file.csv              # Display CSV nicely
mlr --csv cut -f name,age file.csv  # Select columns
mlr --csv filter '$age > 25' file.csv  # Filter rows

# column - Columnate text
column -t file.txt                  # Align columns
ps aux | column -t                  # Align ps output

# xmlstarlet - XML processor
xmlstarlet sel -t -v "//title" file.xml  # Extract XML elements
```

### Text Manipulation
```bash
# sed - Stream editor
sed 's/old/new/g' file              # Replace text
sed -i 's/old/new/g' file           # Replace in place
sed -n '5,10p' file                 # Print lines 5-10
sed '/pattern/d' file               # Delete lines matching pattern

# awk - Text processing
awk '{print $1}' file               # Print first column
awk -F: '{print $1}' /etc/passwd    # Use : as delimiter
awk 'NR==5' file                    # Print 5th line
awk '/pattern/ {print $0}' file     # Print lines matching pattern

# tr - Character translation
tr 'a-z' 'A-Z' < file              # Convert to uppercase
tr -d ' ' < file                    # Delete spaces
tr -s ' ' < file                    # Squeeze multiple spaces

# sort and uniq
sort file                           # Sort lines
sort -n file                        # Numeric sort
sort -r file                        # Reverse sort
sort -k2 file                       # Sort by second field
uniq file                           # Remove duplicate lines
sort file | uniq -c                 # Count occurrences
```

## Development Tools

### Version Control Helpers
```bash
# tig - Text-mode Git interface
tig                                 # Git repository browser
tig status                          # Git status view
tig blame file                      # Git blame view

# lazygit - Simple terminal UI for git
lazygit                             # Interactive git interface

# delta - Better git diff
git config --global core.pager delta
git diff                            # Enhanced diff output

# gh - GitHub CLI
gh repo list                        # List repositories
gh pr list                          # List pull requests
gh issue create                     # Create issue
gh pr create                        # Create pull request
```

### Code Analysis
```bash
# tokei - Code statistics
tokei                               # Count lines of code
tokei --languages                   # List supported languages
tokei --exclude '*.min.js'          # Exclude patterns

# cloc - Count lines of code
cloc .                              # Count code in current directory
cloc --exclude-dir=node_modules .   # Exclude directories

# tree - Directory structure
tree                                # Show directory tree
tree -L 2                           # Limit depth to 2
tree -I 'node_modules|.git'         # Ignore patterns
tree -a                             # Show hidden files
```

## Archive and Compression

### Modern Archive Tools
```bash
# 7z - 7-Zip archiver
7z a archive.7z files/              # Create archive
7z x archive.7z                     # Extract archive
7z l archive.7z                     # List contents

# unrar - RAR extractor
unrar x archive.rar                 # Extract RAR archive
unrar l archive.rar                 # List RAR contents

# atool - Archive tool wrapper
aunpack archive.*                   # Extract any archive type
apack archive.tar.gz files/         # Create archive
als archive.*                       # List archive contents
```

## Network Tools

### HTTP and API Tools
```bash
# curl - Transfer data
curl -X GET https://api.example.com # GET request
curl -X POST -H "Content-Type: application/json" \
     -d '{"key":"value"}' https://api.example.com  # POST with JSON
curl -o file.zip https://example.com/file.zip      # Download file
curl -L https://example.com         # Follow redirects

# httpie - User-friendly HTTP client
http GET https://api.example.com    # GET request
http POST https://api.example.com key=value  # POST request
http --download https://example.com/file.zip # Download file

# wget - Download files
wget https://example.com/file.zip   # Download file
wget -c https://example.com/file.zip # Continue partial download
wget -r https://example.com/        # Recursive download
```

### Network Diagnostics
```bash
# mtr - Network diagnostic tool
mtr google.com                      # Continuous traceroute
mtr --report google.com             # Generate report

# nmap - Network scanner
nmap localhost                      # Scan local ports
nmap -sV localhost                  # Service version detection
nmap 192.168.1.0/24                # Scan network range

# dig - DNS lookup
dig example.com                     # DNS query
dig @8.8.8.8 example.com           # Use specific DNS server
dig example.com MX                  # Query MX records
```

## Productivity Tools

### Terminal Multiplexers
```bash
# tmux - Terminal multiplexer
tmux new-session -s mysession       # Create named session
tmux attach -t mysession            # Attach to session
tmux list-sessions                  # List sessions
tmux kill-session -t mysession      # Kill session

# tmux key bindings (default prefix: Ctrl+b)
# Ctrl+b c - New window
# Ctrl+b n - Next window
# Ctrl+b p - Previous window
# Ctrl+b % - Split vertically
# Ctrl+b " - Split horizontally
# Ctrl+b arrow - Navigate panes

# screen - Terminal multiplexer
screen -S mysession                 # Create named session
screen -r mysession                 # Reattach to session
screen -list                        # List sessions
```

### Task Management
```bash
# task - Task management
task add "Do something"             # Add task
task list                           # List tasks
task 1 done                         # Mark task as done
task 1 modify priority:H            # Set high priority

# calcurse - Calendar and todo
calcurse                            # Terminal calendar/todo app
```

## System Administration

### Service Management
```bash
# systemctl shortcuts
alias sctl='systemctl'
alias sctle='systemctl enable'
alias sctld='systemctl disable'
alias sctls='systemctl start'
alias sctlr='systemctl restart'
alias sctlst='systemctl status'

# journalctl shortcuts
alias jctl='journalctl'
alias jctlf='journalctl -f'         # Follow logs
alias jctlu='journalctl -u'         # Unit logs
```

### Performance Monitoring
```bash
# iotop - I/O monitoring
iotop                               # Monitor disk I/O
iotop -o                            # Only show active processes

# powertop - Power consumption
powertop                            # Monitor power usage

# lsof - List open files
lsof                                # List all open files
lsof -i :80                         # Files using port 80
lsof -u username                    # Files opened by user
lsof +D /path                       # Files in directory
```

## Keyboard Shortcuts for Terminal Tools

### Universal Shortcuts
- `Ctrl + C` - Interrupt/cancel
- `Ctrl + Z` - Suspend process
- `Ctrl + D` - EOF/exit
- `Ctrl + L` - Clear screen
- `Ctrl + R` - Search history
- `Ctrl + A` - Beginning of line
- `Ctrl + E` - End of line
- `Ctrl + U` - Delete to beginning
- `Ctrl + K` - Delete to end
- `Ctrl + W` - Delete word backward

### Tool-Specific Shortcuts

#### htop
- `F1` - Help
- `F2` - Setup
- `F3` - Search
- `F4` - Filter
- `F5` - Tree view
- `F6` - Sort by
- `F9` - Kill process
- `F10` - Quit

#### less/bat
- `Space` - Page down
- `b` - Page up
- `g` - Go to beginning
- `G` - Go to end
- `/pattern` - Search forward
- `?pattern` - Search backward
- `n` - Next search result
- `q` - Quit

#### fzf
- `Ctrl + J/K` - Move down/up
- `Ctrl + C` - Cancel
- `Enter` - Select
- `Tab` - Multi-select
- `Ctrl + A` - Select all
- `Ctrl + D` - Deselect all

This comprehensive guide covers essential terminal tools and utilities for enhanced productivity in Linux environments.

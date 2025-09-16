# Linux Terminal Shortcuts & Key Bindings

## Bash/Zsh Command Line Editing

### Cursor Movement
- `Ctrl + A` - Move to beginning of line
- `Ctrl + E` - Move to end of line
- `Ctrl + F` - Move forward one character
- `Ctrl + B` - Move backward one character
- `Alt + F` - Move forward one word
- `Alt + B` - Move backward one word
- `Ctrl + XX` - Toggle between start of line and current cursor position

### Text Deletion
- `Ctrl + H` - Delete character before cursor (backspace)
- `Ctrl + D` - Delete character under cursor
- `Ctrl + W` - Delete word before cursor
- `Alt + D` - Delete word after cursor
- `Ctrl + K` - Delete from cursor to end of line
- `Ctrl + U` - Delete from cursor to beginning of line
- `Ctrl + Y` - Paste (yank) deleted text
- `Alt + Y` - Cycle through kill ring after Ctrl+Y

### Text Manipulation
- `Ctrl + T` - Transpose characters (swap current and previous)
- `Alt + T` - Transpose words
- `Alt + U` - Uppercase word from cursor to end of word
- `Alt + L` - Lowercase word from cursor to end of word
- `Alt + C` - Capitalize word from cursor to end of word
- `Ctrl + V` - Insert literal character (escape next character)

## History Navigation

### Command History
- `Ctrl + R` - Reverse search through command history
- `Ctrl + S` - Forward search through command history (if enabled)
- `Ctrl + G` - Escape from history search mode
- `Ctrl + P` - Previous command in history (↑ arrow)
- `Ctrl + N` - Next command in history (↓ arrow)
- `Alt + .` - Insert last argument of previous command
- `Alt + _` - Same as Alt + . (insert last argument)
- `!!` - Execute last command
- `!n` - Execute command number n from history
- `!string` - Execute most recent command starting with string
- `!?string?` - Execute most recent command containing string
- `^old^new` - Replace 'old' with 'new' in last command and execute

### History Expansion
- `!$` - Last argument of previous command
- `!^` - First argument of previous command
- `!*` - All arguments of previous command
- `!:n` - nth argument of previous command
- `!:n-m` - Arguments n through m of previous command
- `!:n*` - Arguments n through last of previous command

## Process Control

### Job Control
- `Ctrl + C` - Interrupt (SIGINT) current process
- `Ctrl + Z` - Suspend current process (SIGTSTP)
- `Ctrl + D` - Send EOF (end-of-file) or exit shell
- `Ctrl + \` - Quit current process (SIGQUIT)
- `jobs` - List active jobs
- `bg %n` - Put job n in background
- `fg %n` - Bring job n to foreground
- `kill %n` - Kill job n
- `disown %n` - Remove job n from job table

### Terminal Control
- `Ctrl + S` - Stop output to screen (XOFF)
- `Ctrl + Q` - Resume output to screen (XON)
- `Ctrl + L` - Clear screen (same as `clear` command)
- `reset` - Reset terminal to default state
- `stty sane` - Restore terminal to sane settings

## Tab Completion

### File and Command Completion
- `Tab` - Complete filename/command
- `Tab Tab` - Show all possible completions
- `Alt + ?` - Show possible completions
- `Alt + *` - Insert all possible completions
- `Ctrl + X Ctrl + E` - Edit command line in $EDITOR

### Advanced Completion (Bash)
- `Alt + /` - Complete filename
- `Alt + ~` - Complete username
- `Alt + $` - Complete variable name
- `Alt + @` - Complete hostname
- `Alt + !` - Complete command name

## Terminal Multiplexer Shortcuts

### Tmux Key Bindings (Default prefix: Ctrl+B)
```bash
# Session management
Ctrl+B d        # Detach from session
Ctrl+B s        # List sessions
Ctrl+B $        # Rename session

# Window management
Ctrl+B c        # Create new window
Ctrl+B ,        # Rename current window
Ctrl+B n        # Next window
Ctrl+B p        # Previous window
Ctrl+B 0-9      # Switch to window number
Ctrl+B &        # Kill current window
Ctrl+B w        # List windows

# Pane management
Ctrl+B %        # Split vertically
Ctrl+B "        # Split horizontally
Ctrl+B o        # Switch to next pane
Ctrl+B ;        # Switch to last active pane
Ctrl+B x        # Kill current pane
Ctrl+B z        # Toggle pane zoom
Ctrl+B {        # Move pane left
Ctrl+B }        # Move pane right
Ctrl+B Ctrl+O   # Rotate panes
Ctrl+B Alt+1-5  # Arrange panes in layouts

# Copy mode
Ctrl+B [        # Enter copy mode
Space           # Start selection (in copy mode)
Enter           # Copy selection (in copy mode)
Ctrl+B ]        # Paste
```

### Screen Key Bindings (Default prefix: Ctrl+A)
```bash
# Session management
Ctrl+A d        # Detach from session
Ctrl+A D D      # Detach and logout

# Window management
Ctrl+A c        # Create new window
Ctrl+A A        # Rename current window
Ctrl+A n        # Next window
Ctrl+A p        # Previous window
Ctrl+A 0-9      # Switch to window number
Ctrl+A k        # Kill current window
Ctrl+A w        # List windows

# Split screen
Ctrl+A S        # Split horizontally
Ctrl+A |        # Split vertically (if enabled)
Ctrl+A Tab      # Switch between regions
Ctrl+A Q        # Close all regions except current
Ctrl+A X        # Close current region

# Copy mode
Ctrl+A [        # Enter copy mode
Ctrl+A ]        # Paste
```

## File Manager Shortcuts

### Ranger File Manager
```bash
# Navigation
h, j, k, l      # Left, down, up, right
gg              # Go to top
G               # Go to bottom
H               # Go back in history
L               # Go forward in history
gh              # Go to home directory
gr              # Go to root directory

# File operations
yy              # Copy file
dd              # Cut file
pp              # Paste file
dD              # Delete file
cw              # Rename file
I               # Rename from beginning
A               # Rename from end
Space           # Select file
v               # Select all files
uv              # Unselect all files

# View modes
i               # Display file info
zh              # Toggle hidden files
zp              # Toggle preview
zP              # Toggle preview in all columns
```

### Midnight Commander (mc)
```bash
# Navigation
Tab             # Switch panels
Ctrl+U          # Swap panels
Alt+.           # Toggle hidden files
Alt+,           # Change panel layout

# File operations
F5              # Copy
F6              # Move/rename
F8              # Delete
F3              # View file
F4              # Edit file
F9              # Menu
F10             # Exit
Insert          # Select file
Ctrl+T          # Select group
Ctrl+X Ctrl+A   # Select all
```

## Text Editor Shortcuts in Terminal

### Nano Editor
```bash
# File operations
Ctrl+O          # Save file (WriteOut)
Ctrl+X          # Exit
Ctrl+R          # Read file (insert)

# Navigation
Ctrl+A          # Beginning of line
Ctrl+E          # End of line
Ctrl+Y          # Page up
Ctrl+V          # Page down
Alt+\           # Go to first line
Alt+/           # Go to last line
Ctrl+_          # Go to line number

# Search and replace
Ctrl+W          # Search (Where is)
Alt+W           # Search next
Ctrl+\          # Replace
Alt+R           # Replace next

# Text manipulation
Ctrl+K          # Cut line
Ctrl+U          # Paste (uncut)
Alt+6           # Copy line
Ctrl+T          # Spell check
Ctrl+J          # Justify paragraph
```

### Micro Editor
```bash
# File operations
Ctrl+S          # Save
Ctrl+Q          # Quit
Ctrl+O          # Open file

# Navigation
Ctrl+A          # Select all
Ctrl+C          # Copy
Ctrl+X          # Cut
Ctrl+V          # Paste
Ctrl+Z          # Undo
Ctrl+Y          # Redo

# Search
Ctrl+F          # Find
Ctrl+N          # Find next
Ctrl+P          # Find previous
```

## System Monitoring Shortcuts

### htop Interactive Keys
```bash
# Navigation
↑↓              # Select process
PgUp/PgDn       # Scroll process list
Home/End        # Go to first/last process

# Process management
F9 or k         # Kill process
F7 or ]         # Increase nice value
F8 or [         # Decrease nice value
Space           # Tag process
U               # Untag all processes
c               # Tag process and children

# Display options
F2 or S         # Setup/configuration
F3 or /         # Search processes
F4 or \         # Filter processes
F5 or t         # Tree view
F6 or <         # Sort by column
F10 or q        # Quit

# Columns
P               # Sort by CPU%
M               # Sort by MEM%
T               # Sort by TIME+
```

### top Interactive Keys
```bash
# Display refresh
Space           # Refresh immediately
d               # Change delay interval
s               # Change secure mode

# Process management
k               # Kill process
r               # Renice process
u               # Show processes for user

# Display options
1               # Toggle CPU core display
f               # Add/remove columns
o               # Change column order
W               # Write configuration
q               # Quit

# Sorting
P               # Sort by CPU usage
M               # Sort by memory usage
T               # Sort by time
N               # Sort by PID
```

## Package Manager Shortcuts

### APT (Debian/Ubuntu)
```bash
# Quick aliases to add to ~/.bashrc
alias agi='sudo apt install'
alias agr='sudo apt remove'
alias agu='sudo apt update'
alias agg='sudo apt upgrade'
alias ags='apt search'
alias agsh='apt show'
alias agl='apt list --installed'
alias agac='sudo apt autoclean'
alias agar='sudo apt autoremove'

# Usage examples
agi package_name            # Install package
agr package_name            # Remove package
agu && agg                  # Update and upgrade
ags keyword                 # Search packages
```

### YUM/DNF (Red Hat/Fedora)
```bash
# Quick aliases
alias yi='sudo yum install'
alias yr='sudo yum remove'
alias yu='sudo yum update'
alias ys='yum search'
alias ysh='yum info'

# DNF aliases
alias di='sudo dnf install'
alias dr='sudo dnf remove'
alias du='sudo dnf update'
alias ds='dnf search'
```

### Pacman (Arch Linux)
```bash
# Quick aliases
alias paci='sudo pacman -S'        # Install
alias pacr='sudo pacman -R'        # Remove
alias pacu='sudo pacman -Syu'      # Update system
alias pacs='pacman -Ss'            # Search
alias pacq='pacman -Q'             # Query installed
alias pacqi='pacman -Qi'           # Package info
alias pacqo='pacman -Qo'           # Which package owns file
```

## Git Terminal Shortcuts

### Git Aliases for Speed
```bash
# Add to ~/.gitconfig or use git config --global
[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    ca = commit -a
    cm = commit -m
    cam = commit -am
    df = diff
    dc = diff --cached
    lg = log --oneline --graph --all
    ll = log --oneline
    last = log -1 HEAD
    unstage = reset HEAD --
    visual = !gitk
    type = cat-file -t
    dump = cat-file -p

# Shell aliases for git
alias g='git'
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git pull'
alias gd='git diff'
alias gco='git checkout'
alias gb='git branch'
alias glog='git log --oneline --graph'
```

## Advanced Terminal Tricks

### Command Substitution Shortcuts
```bash
# Backticks (legacy)
`command`

# Modern syntax
$(command)

# Examples
cd $(dirname $(which python))      # Go to directory containing python
echo "Today is $(date)"            # Include command output in string
ls -la $(which bash)               # List details of bash executable
```

### Brace Expansion
```bash
# Create multiple files
touch file{1,2,3}.txt              # Creates file1.txt, file2.txt, file3.txt
mkdir -p project/{src,docs,tests}  # Create directory structure
cp file.txt{,.bak}                 # Copy file.txt to file.txt.bak

# Ranges
echo {1..10}                       # Numbers 1 through 10
echo {a..z}                        # Letters a through z
echo {01..10}                      # Zero-padded numbers
```

### Parameter Expansion
```bash
# Variable manipulation
${var:-default}                    # Use default if var is unset
${var:=default}                    # Set var to default if unset
${var:+alternate}                  # Use alternate if var is set
${var:?error}                      # Error if var is unset

# String manipulation
${var#pattern}                     # Remove shortest match from beginning
${var##pattern}                    # Remove longest match from beginning
${var%pattern}                     # Remove shortest match from end
${var%%pattern}                    # Remove longest match from end
${var/pattern/replacement}         # Replace first match
${var//pattern/replacement}        # Replace all matches
```

## Productivity Aliases and Functions

### Essential Aliases
```bash
# Add to ~/.bashrc or ~/.zshrc
# Navigation
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias ~='cd ~'
alias -- -='cd -'

# Listing files
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias lt='ls -ltr'        # Sort by time
alias lh='ls -lh'         # Human readable sizes
alias tree='tree -C'     # Colorized tree

# Safety nets
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
alias ln='ln -i'

# System info
alias df='df -h'
alias du='du -h'
alias free='free -h'
alias ps='ps auxf'
alias psg='ps aux | grep -v grep | grep -i -e VSZ -e'

# Network
alias ping='ping -c 5'
alias ports='netstat -tulanp'
alias myip='curl -s ifconfig.me'

# Development
alias serve='python3 -m http.server'
alias json='python3 -m json.tool'
```

### Useful Functions
```bash
# Extract any archive
extract() {
    if [ -f $1 ] ; then
        case $1 in
            *.tar.bz2)   tar xjf $1     ;;
            *.tar.gz)    tar xzf $1     ;;
            *.bz2)       bunzip2 $1     ;;
            *.rar)       unrar e $1     ;;
            *.gz)        gunzip $1      ;;
            *.tar)       tar xf $1      ;;
            *.tbz2)      tar xjf $1     ;;
            *.tgz)       tar xzf $1     ;;
            *.zip)       unzip $1       ;;
            *.Z)         uncompress $1  ;;
            *.7z)        7z x $1        ;;
            *)     echo "'$1' cannot be extracted via extract()" ;;
        esac
    else
        echo "'$1' is not a valid file"
    fi
}

# Create directory and cd into it
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# Find and kill process by name
killps() {
    ps aux | grep $1 | grep -v grep | awk '{print $2}' | xargs kill -9
}

# Quick backup
backup() {
    cp "$1"{,.bak-$(date +%Y%m%d-%H%M%S)}
}
```

This comprehensive terminal shortcuts reference covers all essential key bindings and productivity enhancements for Linux terminal usage.

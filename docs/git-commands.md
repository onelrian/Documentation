---
layout: page
title: Git Commands & Workflows
---

# Git Commands & Workflows

## Basic Git Operations

### Repository Setup
```bash
# Initialize repository
git init

# Clone repository
git clone <url>
git clone <url> <directory>
git clone --depth 1 <url>          # Shallow clone

# Remote management
git remote -v                       # List remotes
git remote add origin <url>         # Add remote
git remote set-url origin <url>     # Change remote URL
git remote remove origin            # Remove remote
```

### Basic Workflow
```bash
# Check status
git status
git status -s                       # Short format
git status --porcelain              # Machine readable

# Add files
git add <file>                      # Add specific file
git add .                           # Add all files
git add -A                          # Add all files (including deleted)
git add -u                          # Add modified files only
git add -p                          # Interactive staging

# Commit changes
git commit -m "message"             # Commit with message
git commit -am "message"            # Add and commit
git commit --amend                  # Amend last commit
git commit --amend -m "new message" # Amend with new message
```

### Viewing History
```bash
# View log
git log                             # Full log
git log --oneline                   # Compact log
git log --graph                     # Graph view
git log --all --graph --oneline     # All branches graph
git log -p                          # Show patches
git log --stat                      # Show file statistics
git log -n 5                       # Last 5 commits
git log --since="2 weeks ago"       # Time-based filtering
git log --author="name"             # Filter by author

# Show changes
git show <commit>                   # Show commit details
git show HEAD                       # Show last commit
git show HEAD~1                     # Show previous commit
git diff                            # Working directory vs staging
git diff --staged                   # Staging vs last commit
git diff HEAD                       # Working directory vs last commit
git diff <commit1> <commit2>        # Between commits
```

## Branching and Merging

### Branch Management
```bash
# List branches
git branch                          # Local branches
git branch -r                       # Remote branches
git branch -a                       # All branches
git branch -v                       # Verbose (with last commit)

# Create branches
git branch <name>                   # Create branch
git checkout -b <name>              # Create and switch
git switch -c <name>                # Create and switch (new syntax)

# Switch branches
git checkout <branch>               # Switch branch
git switch <branch>                 # Switch branch (new syntax)
git checkout -                      # Switch to previous branch

# Delete branches
git branch -d <branch>              # Delete merged branch
git branch -D <branch>              # Force delete branch
git push origin --delete <branch>   # Delete remote branch
```

### Merging
```bash
# Merge branches
git merge <branch>                  # Merge branch into current
git merge --no-ff <branch>          # No fast-forward merge
git merge --squash <branch>         # Squash merge

# Rebase
git rebase <branch>                 # Rebase current onto branch
git rebase -i HEAD~3                # Interactive rebase last 3 commits
git rebase --continue               # Continue after resolving conflicts
git rebase --abort                  # Abort rebase
```

## Remote Operations

### Synchronization
```bash
# Fetch and pull
git fetch                           # Fetch from origin
git fetch --all                     # Fetch from all remotes
git pull                            # Fetch and merge
git pull --rebase                   # Fetch and rebase
git pull origin <branch>            # Pull specific branch

# Push changes
git push                            # Push to origin
git push origin <branch>            # Push specific branch
git push -u origin <branch>         # Push and set upstream
git push --force                    # Force push (dangerous!)
git push --force-with-lease         # Safer force push
```

### Tracking Branches
```bash
# Set upstream
git branch -u origin/<branch>       # Set upstream for current branch
git push -u origin <branch>         # Push and set upstream

# Track remote branch
git checkout -b <local> origin/<remote>  # Create local tracking branch
git branch --set-upstream-to=origin/<branch>  # Set upstream
```

## Undoing Changes

### Working Directory
```bash
# Discard changes
git checkout -- <file>              # Discard file changes
git checkout .                      # Discard all changes
git restore <file>                  # Restore file (new syntax)
git restore .                       # Restore all files

# Clean untracked files
git clean -n                        # Dry run
git clean -f                        # Remove untracked files
git clean -fd                       # Remove untracked files and directories
```

### Staging Area
```bash
# Unstage files
git reset <file>                    # Unstage file
git reset                           # Unstage all files
git restore --staged <file>         # Unstage file (new syntax)
```

### Commits
```bash
# Reset commits
git reset --soft HEAD~1             # Undo commit, keep changes staged
git reset --mixed HEAD~1            # Undo commit, unstage changes
git reset --hard HEAD~1             # Undo commit, discard changes

# Revert commits
git revert <commit>                 # Create new commit that undoes changes
git revert HEAD                     # Revert last commit
git revert --no-commit <commit>     # Revert without committing
```

## Stashing

### Stash Operations
```bash
# Create stash
git stash                           # Stash changes
git stash push -m "message"         # Stash with message
git stash -u                        # Include untracked files
git stash -a                        # Include all files

# List and show stashes
git stash list                      # List all stashes
git stash show                      # Show latest stash
git stash show stash@{1}            # Show specific stash
git stash show -p                   # Show patch

# Apply stashes
git stash apply                     # Apply latest stash
git stash apply stash@{1}           # Apply specific stash
git stash pop                       # Apply and remove latest stash
git stash drop                      # Delete latest stash
git stash clear                     # Delete all stashes
```

## Advanced Git

### Interactive Rebase
```bash
# Interactive rebase commands
git rebase -i HEAD~3                # Rebase last 3 commits

# In interactive mode:
# pick = use commit
# reword = use commit, edit message
# edit = use commit, stop for amending
# squash = use commit, meld into previous
# fixup = like squash, discard message
# drop = remove commit
```

### Cherry Picking
```bash
git cherry-pick <commit>            # Apply commit to current branch
git cherry-pick <commit1>..<commit2>  # Apply range of commits
git cherry-pick --no-commit <commit>   # Apply without committing
```

### Bisect (Binary Search for Bugs)
```bash
git bisect start                    # Start bisect session
git bisect bad                      # Mark current commit as bad
git bisect good <commit>            # Mark commit as good
git bisect reset                    # End bisect session
```

### Submodules
```bash
git submodule add <url> <path>      # Add submodule
git submodule init                  # Initialize submodules
git submodule update                # Update submodules
git submodule update --init --recursive  # Init and update recursively
```

## Configuration

### User Configuration
```bash
# Set user info
git config --global user.name "Name"
git config --global user.email "email@example.com"

# View configuration
git config --list                   # All configuration
git config user.name                # Specific setting
git config --global --list          # Global settings only
```

### Useful Aliases
```bash
# Set up aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.lg 'log --oneline --graph --all'
```

### Advanced Configuration
```bash
# Editor and diff tool
git config --global core.editor vim
git config --global merge.tool vimdiff

# Line ending handling
git config --global core.autocrlf true    # Windows
git config --global core.autocrlf input   # Linux/Mac

# Push behavior
git config --global push.default simple
```

## Git Hooks

### Common Hooks
```bash
# Hook locations: .git/hooks/
pre-commit                          # Before commit
post-commit                         # After commit
pre-push                            # Before push
post-receive                        # After receiving push (server)
```

## Troubleshooting

### Common Issues
```bash
# Merge conflicts
git status                          # See conflicted files
# Edit files to resolve conflicts
git add <resolved-files>
git commit

# Detached HEAD
git checkout <branch-name>          # Return to branch
git checkout -b <new-branch>        # Create branch from detached state

# Accidentally committed to wrong branch
git reset --soft HEAD~1             # Undo commit, keep changes
git stash                           # Stash changes
git checkout <correct-branch>       # Switch to correct branch
git stash pop                       # Apply changes
git commit                          # Commit to correct branch
```

### Recovery
```bash
# Find lost commits
git reflog                          # Show reference log
git fsck --lost-found               # Find dangling commits

# Recover deleted branch
git reflog                          # Find branch commit
git checkout -b <branch-name> <commit-hash>
```

## Git Shortcuts and Tips

### Keyboard Shortcuts (Git Bash/Terminal)
- `Ctrl + R` - Search command history
- `Tab` - Auto-complete Git commands and branch names
- `!!` - Repeat last command
- `!git` - Repeat last git command

### Useful Git Aliases for Shell
```bash
# Add to ~/.bashrc or ~/.zshrc
alias g='git'
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git pull'
alias gco='git checkout'
alias gb='git branch'
alias gm='git merge'
alias gd='git diff'
alias glog='git log --oneline --graph'
```

### Advanced Shortcuts
```bash
# Quick commit all changes
git commit -am "message"

# Push new branch and set upstream
git push -u origin $(git branch --show-current)

# Delete merged branches
git branch --merged | grep -v "\*\|master\|main" | xargs -n 1 git branch -d

# Show files changed in last commit
git diff-tree --no-commit-id --name-only -r HEAD

# Undo last commit but keep changes
git reset --soft HEAD~1
```

This comprehensive Git reference covers essential commands and workflows for version control management.

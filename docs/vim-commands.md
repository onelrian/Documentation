---
layout: page
title: Vim/Neovim Commands & Shortcuts
---

# Vim/Neovim Commands & Shortcuts

## Modes

### Mode Switching
- `i` - Insert mode (before cursor)
- `I` - Insert at beginning of line
- `a` - Insert mode (after cursor)
- `A` - Insert at end of line
- `o` - Open new line below
- `O` - Open new line above
- `Esc` - Return to Normal mode
- `v` - Visual mode (character selection)
- `V` - Visual Line mode
- `Ctrl + v` - Visual Block mode
- `:` - Command mode
- `R` - Replace mode

## Navigation

### Basic Movement
- `h` - Left
- `j` - Down
- `k` - Up
- `l` - Right
- `w` - Next word
- `b` - Previous word
- `e` - End of word
- `ge` - End of previous word
- `0` - Beginning of line
- `^` - First non-blank character
- `$` - End of line
- `gg` - Go to first line
- `G` - Go to last line
- `nG` - Go to line n (e.g., `5G`)

### Advanced Navigation
- `f{char}` - Find character forward
- `F{char}` - Find character backward
- `t{char}` - Till character forward
- `T{char}` - Till character backward
- `;` - Repeat last f/F/t/T
- `,` - Repeat last f/F/t/T in opposite direction
- `%` - Jump to matching bracket
- `*` - Search for word under cursor (forward)
- `#` - Search for word under cursor (backward)
- `Ctrl + f` - Page down
- `Ctrl + b` - Page up
- `Ctrl + d` - Half page down
- `Ctrl + u` - Half page up

### Jumping
- `H` - Top of screen
- `M` - Middle of screen
- `L` - Bottom of screen
- `zt` - Scroll current line to top
- `zz` - Scroll current line to center
- `zb` - Scroll current line to bottom

## Editing Commands

### Basic Editing
- `x` - Delete character under cursor
- `X` - Delete character before cursor
- `dd` - Delete entire line
- `D` - Delete from cursor to end of line
- `dw` - Delete word
- `db` - Delete word backward
- `yy` - Yank (copy) line
- `Y` - Yank from cursor to end of line
- `yw` - Yank word
- `p` - Paste after cursor
- `P` - Paste before cursor
- `u` - Undo
- `Ctrl + r` - Redo
- `.` - Repeat last command

### Advanced Editing
- `cc` - Change entire line
- `C` - Change from cursor to end of line
- `cw` - Change word
- `cb` - Change word backward
- `s` - Substitute character
- `S` - Substitute line
- `r{char}` - Replace single character
- `~` - Toggle case of character
- `J` - Join lines
- `>>` - Indent line
- `<<` - Unindent line
- `==` - Auto-indent line

### Text Objects
- `diw` - Delete inner word
- `daw` - Delete a word (including spaces)
- `di"` - Delete inside quotes
- `da"` - Delete around quotes (including quotes)
- `dip` - Delete inner paragraph
- `dap` - Delete a paragraph
- `di(` or `dib` - Delete inside parentheses
- `da(` or `dab` - Delete around parentheses
- `di{` or `diB` - Delete inside braces
- `da{` or `daB` - Delete around braces

## Search and Replace

### Searching
- `/pattern` - Search forward
- `?pattern` - Search backward
- `n` - Next search result
- `N` - Previous search result
- `:noh` - Clear search highlighting
- `*` - Search for word under cursor (forward)
- `#` - Search for word under cursor (backward)

### Replace
- `:s/old/new/` - Replace first occurrence in line
- `:s/old/new/g` - Replace all occurrences in line
- `:%s/old/new/g` - Replace all occurrences in file
- `:%s/old/new/gc` - Replace all with confirmation
- `:5,10s/old/new/g` - Replace in lines 5-10

## File Operations

### File Management
- `:w` - Save file
- `:w filename` - Save as filename
- `:q` - Quit
- `:q!` - Quit without saving
- `:wq` or `:x` - Save and quit
- `:e filename` - Edit file
- `:e!` - Reload current file
- `:r filename` - Insert file contents
- `:r !command` - Insert command output

### Buffer Management
- `:ls` - List buffers
- `:b n` - Switch to buffer n
- `:bn` - Next buffer
- `:bp` - Previous buffer
- `:bd` - Delete buffer
- `:ball` - Open all buffers in windows

## Window Management

### Window Operations
- `:sp` or `:split` - Horizontal split
- `:vsp` or `:vsplit` - Vertical split
- `Ctrl + w + h/j/k/l` - Navigate between windows
- `Ctrl + w + w` - Cycle through windows
- `Ctrl + w + q` - Close current window
- `Ctrl + w + o` - Close all other windows
- `Ctrl + w + =` - Equalize window sizes
- `Ctrl + w + +/-` - Resize window height
- `Ctrl + w + </>` - Resize window width

### Tab Management
- `:tabnew` - New tab
- `:tabc` - Close tab
- `:tabo` - Close all other tabs
- `gt` - Next tab
- `gT` - Previous tab
- `:tabm n` - Move tab to position n

## Visual Mode

### Visual Selection
- `v` - Character-wise visual mode
- `V` - Line-wise visual mode
- `Ctrl + v` - Block-wise visual mode
- `gv` - Reselect last visual selection
- `o` - Move to other end of selection

### Visual Operations
- `d` - Delete selection
- `y` - Yank selection
- `c` - Change selection
- `>` - Indent selection
- `<` - Unindent selection
- `=` - Auto-indent selection
- `u` - Lowercase selection
- `U` - Uppercase selection

## Marks and Jumps

### Marks
- `ma` - Set mark 'a'
- `'a` - Jump to mark 'a'
- `''` - Jump to previous position
- `:marks` - List all marks
- `Ctrl + o` - Jump to older position
- `Ctrl + i` - Jump to newer position

### Special Marks
- `'.` - Last change
- `'"` - Last position when exiting
- `'[` - Beginning of last change/yank
- `']` - End of last change/yank

## Macros

### Recording and Playing
- `qa` - Start recording macro 'a'
- `q` - Stop recording
- `@a` - Play macro 'a'
- `@@` - Repeat last macro
- `5@a` - Play macro 'a' 5 times

## Folding

### Fold Operations
- `zf` - Create fold
- `zo` - Open fold
- `zc` - Close fold
- `za` - Toggle fold
- `zR` - Open all folds
- `zM` - Close all folds
- `zj` - Move to next fold
- `zk` - Move to previous fold

## Command Mode

### Useful Commands
- `:help topic` - Get help on topic
- `:set number` - Show line numbers
- `:set nonumber` - Hide line numbers
- `:set relativenumber` - Show relative line numbers
- `:set paste` - Enable paste mode
- `:set nopaste` - Disable paste mode
- `:syntax on` - Enable syntax highlighting
- `:syntax off` - Disable syntax highlighting
- `:colorscheme name` - Change color scheme

### Line Numbers and Navigation
- `:n` - Go to line n
- `:$` - Go to last line
- `:+n` - Go n lines down
- `:-n` - Go n lines up

## Advanced Features

### Registers
- `"ay` - Yank into register 'a'
- `"ap` - Paste from register 'a'
- `:reg` - Show all registers
- `"0p` - Paste from yank register (register 0)
- `"+y` - Yank to system clipboard
- `"+p` - Paste from system clipboard

### Global Commands
- `:g/pattern/d` - Delete all lines matching pattern
- `:g!/pattern/d` - Delete all lines NOT matching pattern
- `:g/pattern/s/old/new/g` - Replace in lines matching pattern

### Sorting and Filtering
- `:sort` - Sort lines
- `:sort!` - Reverse sort
- `:sort u` - Sort and remove duplicates
- `!}sort` - Sort paragraph

## Neovim-Specific Features

### Terminal
- `:terminal` - Open terminal
- `Ctrl + \` then `Ctrl + n` - Exit terminal mode
- `:sp | terminal` - Terminal in horizontal split
- `:vsp | terminal` - Terminal in vertical split

### LSP (Language Server Protocol)
- `gd` - Go to definition
- `gr` - Go to references
- `K` - Show hover information
- `<leader>rn` - Rename symbol
- `<leader>ca` - Code actions
- `]d` - Next diagnostic
- `[d` - Previous diagnostic

## Configuration Tips

### Essential Settings (.vimrc)
```vim
set number              " Show line numbers
set relativenumber      " Show relative line numbers
set tabstop=4          " Tab width
set shiftwidth=4       " Indent width
set expandtab          " Use spaces instead of tabs
set autoindent         " Auto indent
set smartindent        " Smart indent
set hlsearch           " Highlight search results
set incsearch          " Incremental search
set ignorecase         " Case insensitive search
set smartcase          " Case sensitive if uppercase used
set clipboard=unnamedplus  " Use system clipboard
```

### Key Mappings
```vim
" Map jj to escape
inoremap jj <Esc>

" Map leader key
let mapleader = " "

" Quick save
nnoremap <leader>w :w<CR>

" Quick quit
nnoremap <leader>q :q<CR>
```

This comprehensive guide covers essential Vim/Neovim commands for efficient text editing and navigation.

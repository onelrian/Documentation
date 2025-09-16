# Emacs Keyboard Shortcuts

## Basic Navigation

### Cursor Movement
- `C-f` - Forward character (right)
- `C-b` - Backward character (left)
- `C-n` - Next line (down)
- `C-p` - Previous line (up)
- `M-f` - Forward word
- `M-b` - Backward word
- `C-a` - Beginning of line
- `C-e` - End of line
- `M-a` - Beginning of sentence
- `M-e` - End of sentence
- `M-<` - Beginning of buffer
- `M->` - End of buffer

### Page Navigation
- `C-v` - Page down
- `M-v` - Page up
- `C-l` - Center cursor on screen
- `M-g g` - Go to line number
- `C-u C-SPC` - Jump to previous mark

## File Operations

### File Management
- `C-x C-f` - Find/open file
- `C-x C-s` - Save file
- `C-x C-w` - Save as (write file)
- `C-x s` - Save some buffers
- `C-x C-c` - Exit Emacs
- `C-x C-r` - Find file read-only
- `C-x C-v` - Find alternate file

### Buffer Management
- `C-x b` - Switch buffer
- `C-x C-b` - List buffers
- `C-x k` - Kill buffer
- `C-x 4 b` - Switch buffer in other window
- `C-x 4 f` - Find file in other window
- `C-x 5 b` - Switch buffer in new frame
- `C-x 5 f` - Find file in new frame

## Text Editing

### Basic Editing
- `C-d` - Delete character forward
- `DEL` - Delete character backward
- `M-d` - Delete word forward
- `M-DEL` - Delete word backward
- `C-k` - Kill line (from cursor to end)
- `C-a C-k` - Kill entire line
- `M-k` - Kill sentence
- `C-w` - Kill region (cut)
- `M-w` - Copy region
- `C-y` - Yank (paste)
- `M-y` - Cycle through kill ring

### Advanced Editing
- `C-t` - Transpose characters
- `M-t` - Transpose words
- `C-x C-t` - Transpose lines
- `M-u` - Uppercase word
- `M-l` - Lowercase word
- `M-c` - Capitalize word
- `C-x C-u` - Uppercase region
- `C-x C-l` - Lowercase region

### Undo and Redo
- `C-/` or `C-_` - Undo
- `C-g C-/` - Redo (after undo)
- `M-x undo-tree-mode` - Enable undo tree visualization

## Selection and Regions

### Text Selection
- `C-SPC` - Set mark (start selection)
- `C-x C-x` - Exchange point and mark
- `C-u C-SPC` - Pop mark (go to previous mark)
- `M-h` - Mark paragraph
- `C-x h` - Mark whole buffer
- `M-@` - Mark word

### Rectangle Operations
- `C-x r k` - Kill rectangle
- `C-x r y` - Yank rectangle
- `C-x r o` - Open rectangle
- `C-x r c` - Clear rectangle
- `C-x r t` - String rectangle (replace with text)

## Search and Replace

### Basic Search
- `C-s` - Incremental search forward
- `C-r` - Incremental search backward
- `C-s C-s` - Search for last search string
- `C-s C-w` - Search for word at cursor
- `C-s C-y` - Search for text from cursor to end of line
- `M-s w` - Word search
- `M-s .` - Symbol search

### Replace Operations
- `M-%` - Query replace
- `C-M-%` - Query replace regexp
- `M-x replace-string` - Replace all occurrences
- `M-x replace-regexp` - Replace with regexp

### During Search/Replace
- `SPC` or `y` - Replace this occurrence
- `n` or `DEL` - Skip this occurrence
- `!` - Replace all remaining
- `^` - Back to previous occurrence
- `q` or `RET` - Quit

## Window Management

### Window Operations
- `C-x 2` - Split window horizontally
- `C-x 3` - Split window vertically
- `C-x 1` - Delete other windows
- `C-x 0` - Delete current window
- `C-x o` - Switch to other window
- `C-x 4 0` - Kill buffer and window
- `C-x ^` - Make window taller
- `C-x }` - Make window wider
- `C-x {` - Make window narrower

### Frame Operations
- `C-x 5 2` - Create new frame
- `C-x 5 0` - Delete current frame
- `C-x 5 1` - Delete other frames
- `C-x 5 o` - Switch to other frame

## Programming Features

### Code Navigation
- `M-.` - Find definition (xref)
- `M-,` - Pop back from definition
- `M-?` - Find references
- `C-M-f` - Forward s-expression
- `C-M-b` - Backward s-expression
- `C-M-u` - Up s-expression
- `C-M-d` - Down s-expression
- `C-M-a` - Beginning of function
- `C-M-e` - End of function

### Code Editing
- `C-M-\` - Indent region
- `C-x TAB` - Indent rigidly
- `M-;` - Comment/uncomment
- `C-M-q` - Indent s-expression
- `M-^` - Join with previous line
- `C-o` - Open line
- `C-x C-o` - Delete blank lines

### Compilation and Debugging
- `M-x compile` - Compile
- `C-x `` ` - Next compilation error
- `M-g n` - Next error
- `M-g p` - Previous error
- `M-x gdb` - Start debugger

## Help System

### Getting Help
- `C-h ?` - Help on help
- `C-h k` - Describe key
- `C-h f` - Describe function
- `C-h v` - Describe variable
- `C-h m` - Describe mode
- `C-h b` - Show all key bindings
- `C-h a` - Apropos (search commands)
- `C-h i` - Info documentation
- `C-h t` - Tutorial

### Info Navigation
- `SPC` - Scroll down
- `DEL` - Scroll up
- `n` - Next node
- `p` - Previous node
- `u` - Up node
- `m` - Menu item
- `f` - Follow cross-reference
- `l` - Last node visited
- `q` - Quit info

## Dired (Directory Editor)

### Dired Navigation
- `C-x d` - Open dired
- `n` - Next line
- `p` - Previous line
- `^` - Parent directory
- `g` - Refresh
- `s` - Sort by name/date
- `RET` - Open file/directory
- `o` - Open in other window
- `v` - View file (read-only)

### File Operations in Dired
- `m` - Mark file
- `u` - Unmark file
- `U` - Unmark all
- `t` - Toggle marks
- `d` - Mark for deletion
- `x` - Execute deletions
- `C` - Copy files
- `R` - Rename/move files
- `D` - Delete files immediately
- `+` - Create directory

## Org Mode

### Basic Org Commands
- `TAB` - Cycle visibility
- `S-TAB` - Global cycle visibility
- `C-c C-n` - Next heading
- `C-c C-p` - Previous heading
- `C-c C-f` - Next same level
- `C-c C-b` - Previous same level
- `C-c C-u` - Up heading level

### TODO and Scheduling
- `C-c C-t` - Cycle TODO state
- `C-c C-s` - Schedule item
- `C-c C-d` - Set deadline
- `C-c a` - Agenda
- `C-c C-c` - Set tags

### Links and Tables
- `C-c C-l` - Insert/edit link
- `C-c C-o` - Open link
- `C-c |` - Create table
- `TAB` - Next table field
- `S-TAB` - Previous table field
- `C-c C-c` - Align table

## Advanced Features

### Macros
- `C-x (` - Start macro recording
- `C-x )` - End macro recording
- `C-x e` - Execute macro
- `C-u C-x e` - Execute macro multiple times
- `M-x name-last-kbd-macro` - Name macro

### Registers
- `C-x r SPC` - Save position to register
- `C-x r j` - Jump to register
- `C-x r s` - Save region to register
- `C-x r i` - Insert register contents
- `C-x r w` - Save window config to register

### Bookmarks
- `C-x r m` - Set bookmark
- `C-x r b` - Jump to bookmark
- `C-x r l` - List bookmarks

## Customization

### Configuration
- `M-x customize` - Customization interface
- `M-x customize-group` - Customize specific group
- `M-x customize-variable` - Customize variable
- `M-x customize-face` - Customize appearance

### Package Management
- `M-x package-list-packages` - List packages
- `M-x package-install` - Install package
- `M-x package-delete` - Delete package

## Shell and Terminal

### Shell Integration
- `M-x shell` - Start shell
- `M-x eshell` - Start Emacs shell
- `M-x term` - Start terminal emulator
- `M-x ansi-term` - Start ANSI terminal
- `C-c C-c` - Send C-c to shell
- `C-c C-z` - Send C-z to shell

## Version Control

### VC Commands
- `C-x v v` - Next VC action
- `C-x v =` - Show diff
- `C-x v l` - Show log
- `C-x v u` - Revert file
- `C-x v ~` - Show other version
- `C-x v g` - Annotate (blame)

### Magit (if installed)
- `M-x magit-status` - Git status
- `C-x g` - Magit status (if configured)

## Emergency Commands

### Recovery
- `C-g` - Quit/cancel current command
- `C-]` - Abort recursive edit
- `M-x recover-file` - Recover auto-saved file
- `M-x recover-session` - Recover crashed session
- `C-x C-c` - Exit Emacs (with save prompts)

### When Emacs is Stuck
- `C-g C-g C-g` - Multiple quits
- `ESC ESC ESC` - Get out of recursive edit
- `M-x top-level` - Return to top level

This comprehensive Emacs reference covers essential keyboard shortcuts for efficient text editing and programming.

# Vim Introduction Guide

## Why Use Vim?

Vim (Vi Improved) is a powerful, highly configurable text editor that runs in the terminal. While it has a steep learning curve, mastering Vim can significantly boost your productivity, especially for coding and scientific computing. Here's why it's worth learning:

- **Efficiency**: Edit text without leaving the keyboard—no mouse needed. Commands are designed for speed once memorized.
- **Terminal-Based**: Works over SSH, on remote servers, or in environments without GUI (e.g., HPC clusters).
- **Lightweight**: Minimal resource usage, fast startup, and runs everywhere Linux is installed.
- **Ubiquitous**: Pre-installed on most Linux systems; essential for system administration and quick edits.

If you're coding in Python, R, or C++, Vim can be your go-to editor with plugins like YouCompleteMe for autocompletion or NERDTree for file browsing. Start with basics, and you'll wonder how you lived without it!

## Command Mode

Vim starts in Command mode, where you navigate and manipulate text. Press `Esc` to return here from other modes.

### Cursor Movements

Navigate efficiently without arrow keys:

- `h`: Move left (one character)
- `j`: Move down (one line)
- `k`: Move up (one line)
- `l`: Move right (one character)
- `0` or `^`: Jump to beginning of line
- `$`: Jump to end of line
- `w`: Move forward one word (to start of next word)
- `b`: Move backward one word
- `e`: Move to end of current word

:::{tip}

Combine with numbers, e.g., `5j` moves down 5 lines. Use `H` (top of screen), `M` (middle), `L` (bottom) for screen-relative movement.

:::

### Editing Commands

#### Deletion

Delete text (acts like cut—can be pasted):

- `x`: Delete character under cursor
- `dd`: Delete entire line
- `ndd`: Delete n lines (e.g., `3dd` deletes 3 lines)
- `dw`: Delete word from cursor
- `D` or `d$`: Delete from cursor to end of line
- `d0`: Delete from cursor to start of line

**Examples**:
- `d2w`: Delete 2 words
- `dG`: Delete from cursor to end of file

#### Copy and Paste

- `yy`: Yank (copy) entire line
- `yw`: Yank word
- `y$`: Yank to end of line
- `p`: Paste after cursor
- `P`: Paste before cursor

**Examples**:
- `y3w`: Copy 3 words
- `yyp`: Duplicate current line

#### Undo and Redo

- `u`: Undo last change
- `Ctrl + r`: Redo undone change
- `:earlier 5m`: Go back 5 minutes in edit history

### Window and File Navigation

- `Ctrl + f` or `Page Down`: Scroll down one page
- `Ctrl + b` or `Page Up`: Scroll up one page
- `Ctrl + d`: Scroll down half page
- `Ctrl + u`: Scroll up half page
- `G`: Go to last line of file
- `gg`: Go to first line
- `:n` or `nG`: Go to line n (e.g., `:42` jumps to line 42)
- `Ctrl + o`: Go back to previous location
- `Ctrl + i`: Go forward

:::{tip}

Use marks to bookmark positions: `ma` sets mark 'a', `'a` jumps to it.

:::

## Insert Mode

Switch to Insert mode to type text. Press `i`, `a`, `o`, etc., then type. Press `Esc` to return to Command mode.

- `i`: Insert before cursor
- `a`: Append after cursor
- `o`: Open new line below and insert
- `O`: Open new line above and insert
- `I`: Insert at beginning of line
- `A`: Append at end of line
- `:r filename`: Insert contents of another file below current line

:::{tip}

Use `Ctrl + w` in Insert mode to delete last word, `Ctrl + u` to delete entire line.

:::

## Visual Mode

Select text visually for operations. Press `v` to enter, then move cursor to select.

- `v`: Character-wise visual mode
- `V`: Line-wise visual mode (selects whole lines)
- `Ctrl + v`: Block-wise visual mode (rectangular selection)

Once selected, use commands like `d` (delete), `y` (yank), `>` (indent), etc.

**Examples**:
- Select lines 10-20: `V` then move to line 20, then `d` to delete.
- Comment out code: Select block, then `:s/^/# /` to add # to start of lines.

## Search and Replace

### Basic Search

- `/pattern`: Search forward for pattern
- `?pattern`: Search backward
- `n`: Next match
- `N`: Previous match
- `*`: Search for word under cursor forward
- `#`: Search backward

**Options**: Add `\c` for case-insensitive (e.g., `/pattern\c`).

### Replace

Syntax: `:[range]s/old/new/[flags]`

- **Range**: Where to search/replace
  - `%`: Entire file
  - `.`: Current line
  - `n`: Line n
  - `n,m`: Lines n to m
  - `'<,'>`: Visual selection

- **Flags**:
  - `g`: Global (all matches per line)
  - `c`: Confirm each replacement
  - `i`: Case-insensitive

**Examples**:
- Replace all "old" with "new" in file: `:%s/old/new/g`
- Replace in lines 5-10: `:5,10s/foo/bar/g`
- Confirm replacements: `:%s/old/new/gc`

### Regular Expressions

Vim supports regex for powerful patterns. Use `\(` and `\)` for groups, `\1` to reference in replace.

**Common Metacharacters**:
- `.`: Any character
- `*`: 0 or more of previous
- `\+`: 1 or more
- `\?`: 0 or 1
- `^`: Start of line
- `$`: End of line
- `\w`: Word character ([a-zA-Z0-9_])
- `\d`: Digit
- `[abc]`: Any of a, b, c
- `[^abc]`: Not a, b, c

**Examples**:
- Match email: `/[a-zA-Z0-9._%+-]\+@[a-zA-Z0-9.-]\+\.[a-zA-Z]\{2,\}`
- Replace multiple spaces: `:%s/\s\+/ /g`
- Swap words: `:%s/\(word1\) \(word2\)/\2 \1/g`

:::{tip}

Use `:help regex` for full reference. Practice on regex101.com.

:::

## Advanced Features

### Macros

Record repetitive actions:
- `qa`: Start recording macro 'a'
- Perform actions
- `q`: Stop recording
- `@a`: Play macro
- `@@`: Repeat last macro

**Example**: Record indenting lines: `qa` then `>>` then `j` then `q`, then `@a` to apply.

### Splits and Tabs

- `:vsplit filename`: Vertical split
- `:split filename`: Horizontal split
- `Ctrl + w` then direction (h/j/k/l): Switch panes
- `:tabnew`: New tab
- `gt`: Next tab

### Configuration (.vimrc)

Customize Vim in `~/.vimrc`:

```vim
syntax on              " Syntax highlighting
set number             " Line numbers
set autoindent         " Auto-indent
set tabstop=4          " Tab width
set expandtab          " Use spaces instead of tabs
set incsearch          " Incremental search
set hlsearch           " Highlight matches
```

:::{tip}

Install plugins with vim-plug or Vundle for more features.

:::

<!-- ## Ctags and Taglist for Code Navigation

Ctags generates tags for functions, classes, etc., enabling jumps in code.

### Setting Up Ctags

1. Install ctags: `sudo apt install exuberant-ctags`
2. Generate tags: `ctags -R .` in project root
3. In .vimrc: `set tags=./tags,tags`

**Navigation**:
- `Ctrl + ]`: Jump to definition
- `Ctrl + t`: Jump back
- `:tag function_name`: Jump to tag

### Taglist Plugin

Install Taglist (from vim-taglist.sourceforge.net), extract to ~/.vim/.

- `:Tlist`: Open taglist window
- Shortcuts: `o` (open in new window), `s` (sort), `+` (expand), etc.

**For Python**: Generate tags for stdlib: `ctags -R -f ~/.python.tags /usr/lib/python3.x/`, add to .vimrc.

**For C/C++**: `ctags -R -f ~/.sys.tags /usr/include/`, add to tags.

## Summary

Vim is a lifelong tool—start with basics (navigation, edit), then explore search, regex, and plugins. Practice daily: `vimtutor` is a built-in tutorial. For coding, pair with tools like tmux for multitasking.

:::{admonition} Further Resources
- `:help` in Vim
- Vim Advent Calendar (vimcasts.org)
- Plugins: NERDTree, YouCompleteMe, fugitive (Git integration)
::: -->

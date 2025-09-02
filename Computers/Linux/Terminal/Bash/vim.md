---
created: 2024-02-13 00:58:00Z
---

# Resources
- [Cheatsheet](https://vim.rtorr.com/)
- [VimScriptTheHardWay](https://learnvimscriptthehardway.stevelosh.com/)
- [Premade .vimrc](https://www.freecodecamp.org/news/vimrc-configuration-guide-customize-your-vim-editor/)

# Primary
## Undo / Redo
```
"UNDO"
	[n]u
	:u[ndo]
	Ctrl + u
"REDO"
	Ctrl + r
"UndoLIST"
	:undolist
```

# VISUAL mode

- `v` - enter VISUAL mode

#### Words

- `iw` - select till word end
- `aw` - select till space after word end

# Normal mode

## In- & Output

### Lines

- `yy` / `dd` - yank / cut line
- `y$` or `Y` - yank to end of line
- `d$` or `D` - cut to end of line
- `p`               - paste

### Characters

- `x` - cut character

## Folding

- `zo` / `zc` - open / close fold under cursor
- `zR` / `zM` - open / close all folds

# Commands

## General

- `:set var?` - queries the value of `var`
- `:f[ile]` - for the filename also - `{count}Ctrl+g`
- `:browse oldfiles` - lists recent file paths
- `:sav[e as] file` - save file as
- `:ter[minal]` - open a terminal
- `K` - open man page

### Recording

- `q` `<letter>` - to start recording
- `q` - to stop recording
- `@` `<letter>` - to play it back

## Buffers, Windows, & Tabs

### Buffers

#### Opening / Closing

- `:[N]bd[elete] [N]/{bufname}` - Unloads and removes buffer `N/bufname`\--current from the buffer list
- `:e[dit] file` - open file in new buffer
- `:sp[lit] file` or `:vs[plit] file` - split window with file as new buffer
- `:ls` - list buffers

#### Navigation

- `:bn[ext]` and `:bp[revious]`
- `Ctrl + w{}`
    - `w` - switch windows
    - `h`, `l`, `k`, or `j` - switch left, right, up, or down
    - `s` or `v` - split window
    - `x` - exchange window w/ next

## Mapping Keys

1.  `:map -d dd` - maps the sequence \[`-`,`d`\] to delete line
2.  `:map <c-d> dd` - Ctrl+d to delete line
3.  `:map <space> dd` - Spacebar to delete line
4.  `:unmap <space>` - Removes the mapping on spacebar

#### Leader Key

`:let mapleader = "-"` - maps the `-` key to `<leader>`

- `:nnoremap <leader>d dd` - same as **1.** above

### Types of Mappings

#### Mode Specific

`:*cmd` represents `:cmd` constrained to one of the modes by its respective prefix in `[n, v, i]`

- `:nmap` - **normal** mode
- `:vmap` - **VISUAL** mode
- `:imap` - **INSERT** mode

#### Mapping & Unmapping

`:*map` & `:*unmap`

#### Strict Mapping

`*noremap a b` - maps `a` to the **default** function of `b` in mode `*`, i.e. any other mappings of `b` are ignored.

#### Abbreviations

`*abbrev`

### Key Open for Mapping

- `-`, `H`, `L`, `<space>`, `<cr>`, `<bs>`

# Configuration

## Config Files

### Settings

#### Global

- `/etc/vim/vimrc`
    - `/usr/share/vim/vimrc` : symlink
    - `/etc/vim/vimrc.local` : For keep modifications isolated

#### User

- `/home/robot/.vimrc`

### Other Files

- `/usr/share/vim/vim81/`

## Plugins

### Manager

```bash
$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### Installing Plugins

1.  Include the following lines into ~/.vimrc

```vimscript
call plug#begin('~/.vim/plugged')

Plug 'dense-analysis/ale'
Plug 'preservim/nerdtree'

call plug#end()
```

2.  Run the `:PlugInstall` command in vim to install the plugins

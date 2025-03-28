## log
`git log --oneline --graph --decorate --all --date=short`

## reflog
> [!info] Every commit or branch `HEAD` tip update is logged
`git reflog` to view
- `HEAD@{n}`
	- where `HEAD` was `n` moves ago (e.g. `n reset` commands )
	- `git checkout HEAD@{1} .`
- `master@{one.week.ago}`
	- where `master` branch pointed 1 week ago

## config
`git config [<level>] [<category.config> [<value>]]`
- `[<level>]`
	- `--system` : System-wide `$(prefix)/etc/gitconfig`
	- `--global` : User-specific `~/.gitconfig`
	- `--local` : Repository `.git/config`
`git config list [<level>] [--show-origin]`
`git config edit [<level>]`
- Opens the level's corresponding config file for editing.


## remote
`git remote` : lists remote repos
`git remote show <origin>` : prints un-/tracked branches
`git push <origin> --all --dry-run`


## file info
`git cat-file -s 033b4468fa6b2a9547a70d88d1bbe8bf3f9ed0d5`
`git cat-file -p master^{tree}`


## loose object compression
`git gc`
`find .git/objects -type f`


## checkout & branch
`git checkout -b <new-branch-name> <start-commit>`
- `<start-commit>` : for example `origin\branch-to-track`
`git checkout -t origin/branch-to-track`
`git checkout <branch-name>`
`git checkout <tree-ish> -- <path>`

`git branch -d <branch-name>`
`git branch -d -r origin/<remote-branch-name>`
- stops tracking named remote branch locally (deletes remote-tracking branch)


## rename
`git mv ./old ./new`


## rm
`git rm -r --cached .`
- Unstages & removes **paths** only from the index


## add
`git add -p` or `--patch`
- Interactively choose hunks of patch between the index and working tree


## restore
`git restore [-s <tree>] [-S] [-W] [--] <pathspec>`
- restores **working tree** to **the index** for all paths matching `<pathspec>`
	- `[-S] --staged` : restores **index** to **`HEAD`**
		- `[-W] --worktree` : also restores **working tree** to **`HEAD`**
	- `[-s <tree>] --source=<tree>` : restores to `<source>=commit,branch,tag`


## reset
`git reset [-p] [<tree-ish>] [--] <pathspec>`
- Copies files from **`HEAD`** to **the index** for all paths matching `<pathspec>`
	- `<tree-ish>` : replaces **`HEAD`** as source
	- `[-p] --patched`
	- `git restore [--source=<tree-ish>] --staged <pathspec>` : equivalent

`git reset [<mode>] <commit>`
- Resets branch **`HEAD`** to `<commit>`, along with...
- `[<mode>]`
	- `--mixed` : **the index** ***(default)***
		- `-N` : adds [intent-to-add](https://stackoverflow.com/questions/24329051/what-does-git-add-intent-to-add-or-n-do-and-when-should-it-be-used) for removed paths (deleted files)
	- `--soft` : 
	- `--hard` : **the index** & **working tree**
		- `--keep` : aborts if a reset file has local changes
			- use to revert commits while local changes exist


## Amending
`git commit --amend`
`git commit --amend -m "new message"`
`git commit --amend --no-edit`
- does not change commit message


## Tree Traversal
`git rev-parse --short HEAD~~~^2~3`
- caret `^n` selects a the **nth**-path at a fork
- each `~` or `~n` goes backwards by **1** or **n** respectively, always choosing the first parent at forks 

![[git_diff.png|]]


# \<tree-ish\>
```
----------------------------------------------------------------------
|    Commit-ish/Tree-ish    |                Examples
----------------------------------------------------------------------
|  1. <sha1>                | dae86e1950b1277e545cee180551750029cfe735
|  2. <describeOutput>      | v1.7.4.2-679-g3bee7fb
|  3. <refname>             | master, heads/master, refs/heads/master
|  4. <refname>@{<date>}    | master@{yesterday}, HEAD@{5 minutes ago}
|  5. <refname>@{<n>}       | master@{1}
|  6. @{<n>}                | @{1}
|  7. @{-<n>}               | @{-1}
|  8. <refname>@{upstream}  | master@{upstream}, @{u}
|  9. <rev>^                | HEAD^, v1.5.1^0
| 10. <rev>~<n>             | master~3
| 11. <rev>^{<type>}        | v0.99.8^{commit}
| 12. <rev>^{}              | v0.99.8^{}
| 13. <rev>^{/<text>}       | HEAD^{/fix nasty bug}
| 14. :/<text>              | :/fix nasty bug
----------------------------------------------------------------------
|       Tree-ish only       |                Examples
----------------------------------------------------------------------
| 15. <rev>:<path>          | HEAD:README, :README, master:./README
----------------------------------------------------------------------
|         Tree-ish?         |                Examples
----------------------------------------------------------------------
| 16. :<n>:<path>           | :0:README, :README
----------------------------------------------------------------------
```


# .gitconfig
```
[user]
	name = Aron Lloyd
	email = aron.lloyd@innovis-kg.de
[alias]
	tree = log --graph --all --pretty=format:'%C(auto)%h%d [%cs](%cn): %s'
```
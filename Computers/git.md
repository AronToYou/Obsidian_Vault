# Commands
## Primary
---
### git
`git --no-pager <command>`
- avoids interactive paging and simply outputs everything

### log
`git log --oneline --graph --decorate --all --date=short --parent-branch <branch-name>`

### remote
> [!info]
> `git remote` : lists remote repos
> `git remote show <origin>` : prints un-/tracked branches
> `git push <origin> --all --dry-run`

### diff
> [!info]
> `git diff [<options>] [<commitB> [<commitA>]] [[--] <path>]`
> - Display the difference `<commitA> - <commitB>` per project file
> 	- `[<commitB>]` : defaults to the **Index**
> 	- `[<commitA>]` : defaults to the **Working Tree**
> 	- `[<path>]` : instead only checks files found on `<path>`
> 	- `[<options>]`
> 		- `--stat` : only output changed filenames & number of changes
> 		- `--relative[=<path>]` : restrict output to current or `<path>` subdirectory
> 
> `git diff --cached [<commitB>] [--] [<path>]`
> - Same as above if `<commitA>` is replaced with **Index**
> 	- `[<commitB>]` : defaults to `HEAD`
> 	- `--staged` is the same as `--cached`
>
> `git diff test...master`
> - Changes on `master` since `test` branch fork.
> 
> `git diff --no-index [--] <path> <path>`
> - Compares two filesystem paths outside of repo
> 
> > [!tip]- Diagram of Repo `diff` Options
> > ![[git_diff.png|]]

### checkout
> [!info]
> `git checkout <commit>`
> - Redirects HEAD pointer to `<commit>` then overwrites index & working tree accordingly
> 	- Only proceeds if current changes in index & working tree would remain unchanged
> 	- HEAD is detached at end
>
> `git checkout [--detach] <branch>`
> - Same as above except detachment is optional
> - `[--detach]` : Detach & redirect HEAD to `<commit>`
> 	- preserves Index & Working directory
> 
> `git checkout [-p] [<tree-ish>] [--] <pathspec>`
> - Overwrite matching working tree paths with the index
> - `[<tree-ish>]` : overwrite both working tree & index paths with `<tree-ish>`
> 	- for example `<commit>`
> - `[-p]` : `--patch`
  > 
> `git checkout -b <new-branch> [<start-point>]`
> - Create a new branch pointing to HEAD & checks it out
> 	- `[<start-point>]` : points initially to this commit, branch, or tag instead
> 		- for example `origin\branch-to-track`
> 
> `git checkout -t origin/branch-to-track`
> 
> `git checkout <branch-name>`
> 
> `git checkout <tree-ish> -- <path>`

### branch
> [!info]
> `git branch [--force] <branch-name> [<new-tip-commit>]`
> - Creates a new branch pointing to current commit.
> - `[<new-tip-commit>]` : New branch initially points here instead.
> - `[--force|-f]` : If `<branch-name>` already exists, then resets it to target commit.
> 	- Doesn't work if branch is currently checked-out in another working tree linked to same repo.
> 
> `git branch [-a]`
> - list branches
> - use `-a` to show hidden branches as well
> 
> `git branch -d <branch-name>`
> 
> `git branch -d -r origin/<remote-branch-name>`
> - stops tracking named remote branch locally (deletes remote-tracking branch)
>
>> [!tip]- Rename branch locally & remotely
>> from [here](https://stackoverflow.com/questions/30590083/git-how-to-rename-a-branch-both-local-and-remote)
>> ```bash
>> # Names of things - allows you to copy/paste commands
>> old_name=feature/old
>> new_name=feature/new
>> remote=origin
>> 
>> # Rename the local branch to the new name
>> git branch -m $old_name $new_name
>> 
>> # Delete the old branch on remote
>> git push $remote --delete $old_name
>> 
>> # Or shorter way to delete remote branch [:]
>> git push $remote :$old_name
>> 
>> # Prevent git from using the old name when pushing in the next step.
>> # Otherwise, git will use the old upstream name instead of $new_name.
>> git branch --unset-upstream $new_name
>> 
>> # Push the new branch to remote
>> git push $remote $new_name
>> 
>> # Reset the upstream branch for the new_name local branch
>> git push $remote -u $new_name
>> ```

### mv
> [!info]
> `git mv ./old ./new`
> - renames git path

### rm
> [!info]
> `git rm -r --cached .`
> - Unstages & removes **paths** only from the index

### add
> [!info]
> `git add [-p] [--] [<pathspec>]`
> - add changes from working directory to index
> 	- `[-p] --patch` : Interactively choose hunks of patch between the index and working tree

### restore
> [!info]
> `git restore [-s <tree>] [-S] [-W] [--] <pathspec>`
> - restores **working tree** to **the index** for all paths matching `<pathspec>`
> 	- `[-S] --staged` : restores **index** to **`HEAD`**
> 		- `[-W] --worktree` : also restores **working tree** to **`HEAD`**
> 	- `[-s <tree>] --source=<tree>` : restores to `<source>=commit,branch,tag`

### reset
> [!info]
> `git reset [-p] [<tree-ish>] [--] <pathspec>`
> - Copies files from **`HEAD`** to **the index** for all paths matching `<pathspec>`
> 	- equivalent to : `git restore [--source=<tree-ish>] --staged <pathspec>`
> - `[<tree-ish>]` : replaces **`HEAD`** as source
> - `[-p] : --patched`
>  
>  
> `git reset [<mode>] <commit>`
> - Resets branch **`HEAD`** to `<commit>`, along with...
> - `[<mode>]`
> 	- `--mixed` : **the index** ***(default)***
> 		- `-N` : adds [intent-to-add](https://stackoverflow.com/questions/24329051/what-does-git-add-intent-to-add-or-n-do-and-when-should-it-be-used) for removed paths (deleted files)
> 	- `--soft` : 
> 	- `--hard` : **the index** & **working tree**
> 		- `--keep` : aborts if a reset file has local changes
> 			- use to revert commits while local changes exist

### commit --amend
> [!info]
> `git commit --amend`
> 
> `git commit --amend -m "new message"`
> 
> `git commit --amend --no-edit`
> - does not change commit message

### merge
> [!info]
> `git merge [--no-commit] <branch>`
> - merges `<branch>` into currently checked out branch
> 	- `[--no-commit]` : does not commit result
> 		- `git merge --continue` : commits the merge, if finished
> 		- `git merge --abort` : undoes changes to **Index** & **Working Tree**

### stash
> [!info]
> `git stash push [--include-untracked] [--keep-index]`
> - merges `<branch>` into currently checked out branch

### tag
> [!info]
> `git tag`
> - lists all tags
> 
> `git tag [-a [-m "<msg>"]] <tagname> [<commit>]`
> - creates tag at `HEAD` by default
> - `[-a]` : creates annotated tag
> 	- `[-m "<msg>"]` : annotation
> 
> `git push origin <tagname>`
> - push tag to remote


## Extra
---
### reflog - Tree Traversal
#### rev-parse
> [!info] Every commit or branch `HEAD` tip update is logged
> `git reflog [show <ref>]`
> Displays reference logs: movements of branch tips
> - `[show <ref>]` : default subcommand, `<ref>` defaults to `HEAD` 
> - `HEAD@{n}`
> 	- where `HEAD` was `n` `reflog` entries ago (e.g. `n reset` commands )
> 	- `git checkout HEAD@{1} .`
> - `master@{one.week.ago}`
> 	- where `master` branch pointed 1 week ago
> - `@` is equivalent to `HEAD`
> 	- `HEAD@{1}` is the same as `@@{1}`
> 
> `git rev-parse --short HEAD~~~^2~3`
> - `<rev>^n` selects **nth**-parent of `<rev>`
> 	- `<rev>^@` all parents
> 	- `<rev>^!` no parents, only `<rev>`
> - `~` or `~n` goes backwards by **1** or **n** graph nodes respectively, always choosing the first parent at forks 

### config
> [!info]
> `git config [<level>] <category.config> [<value>]`
> - Gets the value of a particular git configuration field (same as `git config get`)
> - `[<value>]` : Sets the value instead (same as `git config set`)
> - `[<level>]`
> 	- `--system` : System-wide `$(prefix)/etc/gitconfig`
> 	- `--global` : User-specific `~/.gitconfig`
> 	- `--local` : Repository `.git/config`
> 
> `git config list [<level>] [--show-origin]`
> - Lists all configs in a file
>
> `git config get [<level>] [--all] <category.config>`
> - Reads the value of a particular git configuration field
>
> `git config edit [<level>]`
> - Opens the level's corresponding config file for editing.
> `git config --get-regexp ^alias`

### file info
> [!info]
> `git cat-file -s 033b4468fa6b2a9547a70d88d1bbe8bf3f9ed0d5`
> `git cat-file -p master^{tree}`

### gc
loose object compression
> [!info]
> `git gc`
> `find .git/objects -type f`

### gitk & rev-list
> [!info]
> `gitk`
> `git rev-list`
> `git rev-parse`?
> allegedly for visualization purposes

---


# Miscellaneous
---
## \<tree-ish\>
```shell
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

## .gitconfig
> [!info]
> ```
> [user]
> 	name = Aron Lloyd
> 	email = aron.lloyd@innovis-kg.de
> [alias]
> 	tree = log --graph --all --pretty=format:'%C(auto)%h%d [%cs](%cn): %s'
> ```

## hub
[[https://hub.github.com|hub]] is a cli tool from GitHub.

### sync
`git sync`
- Update all local branches from remote
- like [[https://stackoverflow.com/questions/4318161/can-git-pull-all-update-all-my-local-branches|here]]

## log
`git log --oneline --graph --decorate --all --date=short`

## remote
> [!info]
> `git remote` : lists remote repos
> `git remote show <origin>` : prints un-/tracked branches
> `git push <origin> --all --dry-run`

## file info
> [!info]
> `git cat-file -s 033b4468fa6b2a9547a70d88d1bbe8bf3f9ed0d5`
> `git cat-file -p master^{tree}`

## gc
loose object compression
> [!info]
> `git gc`
> `find .git/objects -type f`

## checkout
> [!info]
> `git checkout -b <new-branch-name> <start-commit>`
> - `<start-commit>` : for example `origin\branch-to-track`
> `git checkout -t origin/branch-to-track`
> `git checkout <branch-name>`
> `git checkout <tree-ish> -- <path>`

## branch
> [!info]
> `git branch [-a]`
> - list branches
> - use `-a` to show hidden branches as well
> `git branch -d <branch-name>`
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

## mv
### Rename
> [!info]
> `git mv ./old ./new`

## rm
> [!info]
> `git rm -r --cached .`
> - Unstages & removes **paths** only from the index

## add
> [!info]
> `git add -p` or `--patch`
> - Interactively choose hunks of patch between the index and working tree

## restore
> [!info]
> `git restore [-s <tree>] [-S] [-W] [--] <pathspec>`
> - restores **working tree** to **the index** for all paths matching `<pathspec>`
> 	- `[-S] --staged` : restores **index** to **`HEAD`**
> 		- `[-W] --worktree` : also restores **working tree** to **`HEAD`**
> 	- `[-s <tree>] --source=<tree>` : restores to `<source>=commit,branch,tag`

## reset
> [!info]
> `git reset [-p] [<tree-ish>] [--] <pathspec>`
> - Copies files from **`HEAD`** to **the index** for all paths matching `<pathspec>`
> 	- `<tree-ish>` : replaces **`HEAD`** as source
> 	- `[-p] --patched`
> 	- `git restore [--source=<tree-ish>] --staged <pathspec>` : equivalent
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

## commit --amend
> [!info]
> `git commit --amend`
> `git commit --amend -m "new message"`
> `git commit --amend --no-edit`
> - does not change commit message

## merge
> [!info]
> `git merge [--no-commit] <branch>`
> - merges `<branch>` into currently checked out branch

## tag
> [!info]
> `git tag`
> - lists all tags
> 
> `git tag [-a [-m "<msg>"]] <tagname> [<commit>]`
> - creates tag at `HEAD` by default
> - `-a` : creates annotated tag
> 	- `-m` : annotation
> `git push origin <tagname>`
> - push tag to remote

## reflog - Tree Traversal
### rev-parse
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
> > [!tip]- Diagram of Repo `diff` Options
> > ![[git_diff.png|]]

## config
> [!info]
> `git config [<level>] [<category.config> [<value>]]`
> - Sets the value of a particular git configuration field
> - `[<level>]`
> 	- `--system` : System-wide `$(prefix)/etc/gitconfig`
> 	- `--global` : User-specific `~/.gitconfig`
> 	- `--local` : Repository `.git/config`
> `git config list [<level>] [--show-origin]`
> `git config edit [<level>]`
> - Opens the level's corresponding config file for editing.
> `git config --get-regexp ^alias`

# Miscellaneous
## Visualizing?
### rev-list
> [!info]
> `gitk`
> `git rev-list`
> `git rev-parse`?

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
	
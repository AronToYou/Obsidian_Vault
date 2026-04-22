# Examples
---
```sh
tr -d -c ',\n' < file.dpl | 
awk 'length!=0 { print length }'
```
- `tr`
	- translate or delete characters from standard input
	- `-d` delete
	- `-c 'CHARS'` apply to complement (inverse set) of `CHARS`
---
`{sh}find . -name "*.txt" -exec sh -c 'mv "$1" "${1%.txt}.md"' _ {} \;`
- `_` is placeholder for `{sh}$0`
- `{sh}"${1%.txt}.md"` substring match and delete
`{sh}find . -name "awl_*.pnl" -exec sh -c 'git mv "$1" "../vision/${1#./awl_}"' _ {} \;`

`{sh}find . -name "*.pnl" -exec sh -c 'git diff "$1" $(find ../wincc-oa -name $(basename "$1"))' _ {} \;`

---
```sh
git diff --numstat ..B | 
awk '{ $1=$2=""; sub(/^[ \t]+/, ""); print }' |
xargs -d '\n' -I{} sh -c 'git diff ..B -- "{}"'
```
- `{sh}xargs -d '\n'`
	- treats newlines as delimiters instead of whitespaces
- `{sh}-I{}`
	- turns on "replace mode" where `{}` becomes the placeholder

---
```sh
# .gitconfig alias
child = "!bash -c 'git log ${1:-HEAD}..${2:-$(git rev-parse --abbrev-ref HEAD)} | head -1' -"
child = !bash -c 'git rev-list ${1:-HEAD}..${git rev-parse --abbrev-ref HEAD)} | head -1' -
# then in bash
git child A B
```
- Returns first immediate child of `A` (default: `HEAD`)
	- by stepping in direction of `B` (default: current branch)
		- assumes one is not in detached head state
	- `{c}!bash -c '...' -`
		- the `{c}!` tells `{c}git` to fork `{c}alias` in `{c}/bin/sh -c` rather than interpret it as a git subcommand
			- `{sh}bash -c '...' -` then forks **another** child shell
				- which `{c}/bin/sh` may replace itself with via `{c}exec`
		- the `{c}-` tells `{c}bash` to assign `{c}$0` with dummy value `{c}-`
			- avoids accidental "login-shell", non `shift`ing, and/or weird logging behavior
	- `{c}${1:-HEAD}` : evaluates to HEAD 
		- or, if available, the 1st passed arg `{c}A`
	- `{c}${2:-$(git rev-parse --abbrev-ref HEAD)}` : evaluates to the short name (branch) of `HEAD`
		- or, if available, 2nd passed arg `{c}B`
	- `{c} | head -1`
		- pipes `{c}git log` output to `{c}head` where the `{c}-1` arg says to take only the first line
---
```sh
git --no-pager log --oneline --follow -n 5 -- lib/file.cpp 
	| awk '{ print $1 }'
	| xargs -d '\n' -I{} sh -c '
		git show {}:./lib/file.cpp 2>/dev/null > ./lib/tmp.cpp;
		git diff --numstat ./lib/tmp.cpp ../otherRepo/lib/file.cpp'
```
---

|     | owner | group | other |
| --- | ----- | ----- | ----- |
| r   | 400   | 40    | 4     |
| w   | 200   | 20    | 2     |
| x   | 100   | 10    | 1     |
`{sh}chmod u+x .\file`

# Core Syntax
---
## Parameter Expansion
[here!](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02)
`${parameter<operator>word}`

|                      | Set &  !Null    | Set but Null  | Unset         |
| -------------------- | --------------- | ------------- | ------------- |
| `${parameter:-word}` | sub `parameter` | sub `word`    | sub `word`    |
| `${parameter-word}`  | sub `parameter` | sub Null      | sub `word`    |
| `${parameter:=word}` | sub `parameter` | assign `word` | assign `word` |
| `${parameter=word}`  | sub `parameter` | sub null      | assign `word` |
| `${parameter:?word}` | sub `parameter` | error, exit   | error, exit   |
| `${parameter?word}`  | sub `parameter` | sub Null      | error, exit   |
| `${parameter:+word}` | sub `word`      | sub Null      | sub Null      |
| `${parameter+word}`  | sub `word`      | sub `word`    | sub Null      |

## Quotations
### Double Quotes
Enclosure of characters in `""` preserves their literal values with exceptions:
- `$`
-  `` ` ``
- `\`
- `!`
Single quotes inside double quotes will preserve 
### Single Quotes
The literal value of all characters are preserved.
Single quotes cannot exist inside single quotes

## Alias
`$ alias myAlias="command"`
`$ myAlias` => `$ command`
> [!note]-
> `command` is parsed & expanded before execution.
> > [!example]
> > `$ alias mycmd="echo \"*\""`
> > `$ mycmd`
> > `$ *`

## Variable
`$ VAR="anything"`
> [!note]-
> `anything` is interpreted *literally*, meaning no expansions take place.
> > [!example]
> > `$ MYVAR="echo \"*\""`
> > `$ $MYVAR`
> > `$ "*"`

## Evaluation
### Commands
`$ $(command)`
``$ `command` ``
Evaluates the `command` first, then substitutes in its output.

### Variables
[Shell Parameter Expansion](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)
`$ $variable`
	Expands the variable `variable` and substitutes in the result. 
`$ ${variable}`
	Same as w/o curly braces, only for disambiguation when necessary.
#### Double Quotes
`$ "$variable"`
	Forces `variable` to be interpreted as a single ***word***
> [!example]
> `$ var="foo bar"`
> `$ for i in $var; do echo $i; done`
> `foo`
> `bar`
> `$ for i in "$var"; do echo $i; done`
> `foo bar`

#### Special Expansion
`$ ${!variable}`
	First expands `variable`, then expands the result once more, which after is finally substituted it.
`$ ${!var*}`
	Expands into the *name* of all variables containing the prefix `var`
`$ ${var//pattern/sub}`
	Replaces all occurrences of `pattern` in `var` with `sub`

### Arrays
[introduction](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_02.html)
`$ foo=(a b c)`
#### 1st Element
`$ echo $foo`  -  curly braces *optional*
`a`
#### All Elements
`$ echo ${foo[@]}`  -  curly braces **required**
`a b c`
#### Double Quotes
Same as for variables
> [!example]
> `$ foo=("a b" "c d")`
> `$ for i in ${foo[@]}; do echo $i; done`
> `a`
> `b`
> `c`
> `d`
> `$ for i in "${foo[@]}"; do echo $i; done`
> `a b`
> `c d`
## Redirection
[Here](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)
### stdin
`>` -- creates or overwrites
`>>` -- appends

### stdout
`<` -- 
`<<` -- 

## Detached Processes
### Long-way
`$ COMMAND`  -  begin process w/ `COMMAND`
`Ctrl + z`  -  pause process
`$ bg`  -  start in background
`$ disown`  -  detach process from terminal s.t. it persists despite terminal termination

### Short-way
`$ COMMAND &`  -  the `&` at the end runs `COMMAND` in background
`$ jobs`  -  view processes

# Examples
```bash
logs=(Alarm, Set, Limit, Note, Cmd)
for i in ${logs[*]};
do git diff REMS_BL/scripts/libs/classes/logType$i.ctl ../REMS_main/scripts/libs/classes/logType$i.ctl;
done

echo ${logs[@]}
```
# Core Syntax
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
`>` -- creates or overwrites
`>>` -- appends

## Detached Processes
### Long-way
`$ COMMAND`  -  begin process w/ `COMMAND`
`Ctrl + z`  -  pause process
`$ bg`  -  start in background
`$ disown`  -  detach process from terminal s.t. it persists despite terminal termination

### Short-way
`$ COMMAND &`  -  the `&` at the end runs `COMMAND` in background
`$ jobs`  -  view processes

# Other Commands
## Text Manipulation
> [!bash]
> `$ echo $var | sed 's/pattern/sub/g'`
> `$ echo $var | tr "pattern" "sub"`

## Regular Expressions
Use Perl-syntax
`$ grep -P "pattern"`
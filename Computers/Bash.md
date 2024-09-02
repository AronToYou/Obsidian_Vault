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
`$ ${variable}`
Expands the variable `variable` and substitutes in the result.
`$ ${!variable}`
First expands `variable`, then expands the result once more, which after is finally substituted it.
`$ ${!var*}`
Expands into the *name* of all variables containing the prefix `var`

## Redirection
`>` -- creates or overwrites
`>>` -- appends
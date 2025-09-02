---
created: 2024-01-03 15:17:03Z
---

# Basics
[Official Guide to awk](https://www.gnu.org/software/gawk/manual/gawk.html)
## Essential Procedure
`awk` works line by line, running the **Program** on each line, which generally parses the line into **Fields**.

# Components
## Fields
For a given line, each string of characters surrounded by whitespace, start of line, or end of line is a **Field**.
### Special Field Identifiers
- `$0`: Entire line
- `$1`: First field
- `$5`: Fifth field
- `$NF`: Number of fields
 
 ## Program
- Composed of 
	- a list of **Rules**, each on a new line
	- optional **Variables**
- Entirely contained within single quotes
`$ awk 'variable rule1 
				rule2' input.txt`

## Rules
- A **Pattern** and **Action** together form a rule, all contained within curly-braces `{action}`
`$ awk 'variable pattern1 {action1} 
									pattern2 {action2}' input.txt`

### Patterns
Can be logical operators or regular expressions
- `$3 >= 1000`
- `/regex/`
### Actions
- `print`

## Variables
### OFS (Output Field Separator)
- `OFS="char"` will use `char` as the seperator between the fields listed as arguments for a command, e.g.
```
$ date
Mi 3. Jan 16:21:35 CET 2024
$ date | awk 'OFS="/" {print$2,$3,$6}'
3./Jan/2024
```
### BEGIN und END
#### BEGIN
- Executes a **Rule** before `awk` reads any text
#### END
- Executes a **Rule** after all processing has completed
`$ awk 'BEGIN {print "Dennis Ritchie"} {print $0}' dennis_ritchie.txt`

## Options
Placed outside of the single-quoations enclosing the **Program**.
### Input Field Seperator
- `-F` immediately followed by the character to treat as seperator
- `$ awk -F: '{print $1,$6}' /etc/passwd`

# Examples
`awk -v count=2 '{a[++i]=$0;}/lorem/{for(j=NR-count;j<NR;j++)print a[j];}' file`
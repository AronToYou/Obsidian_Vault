---
created: 2023-11-15 10:53:00Z
---

# General
- `xdg-open` - Essentially double-clicks the file.
- `watch -n[seconds] [command]`

## Expansions
**In order of execution**, see [here](https://www.gnu.org/software/bash/manual/html_node/Shell-Expansions.html) for documentation.
### Curly Braces
- `first/{A,B,...}.txt` --> `first/A.txt first/B.txt ...`

### Commands
Executes the given `COMMAND` and subtitutes its output in-place
- `$(COMMAND)` or `` `COMMAND` ``

### Arithmetic
- `$(( EXPRESSION ))`

## ls
![7551f5b61cfa34612d6ed3329e05e90e.png](../../_resources/7551f5b61cfa34612d6ed3329e05e90e.png)

## Dash
- `dash` or `sh`
	- `sh -c 'command -- "$1"' x-sh arg1`
		- injects user supplied `arg1` into placeholder `"$1"`
		- Error messages are sent to `x-sh`, could also just have written `2>/dev/null`

## Piping Outputs Into Arguements
`find -print0`, `sort -z`, `xargs -0`, and `grep -z`
Terminates results with NULL character instead.
### xargs
- `xargs`
	- `-i` - reads 1 line at a time, i.e. `-L 1`
	- `-I@` - same as `-i`, except each read line replaces every occurance of `@` (or whichever symbol you choose)

## File Compression
`tar cvzf compressed.tar.gz ./notcompressed/`
`tar -xvzf compressed.tar.gz -C ./folder/`
Compressing tar balls.

# Searching & Sorting
## Searching w/ `find`
`find / -name something -type d -print 2>/dev/null`

## Filtering w/ `grep`
- `egrep 'SSID|signal' | egrep -B1 'SSID1|SSID2'`
### Pass Matches from `find` as Arguments to grep
- `find / -iname something | grep -P '^(?:(?!find).)*$'`
- `find / -iname something -exec grep -P '^(?:(?!find).)*$' {} \+`
- `find / -iname something -print0 | xargs -0 grep -P '^(?:(?!find).)*$'`

		-L : print files without match
		-v : invert matching

### Non-including Look-Ahead/Behind
`grep -Po '(?<=pattern)pattern-to-match(?=pattern)'`
`grep -Po 'pattern\Kpattern-to-match(?=pattern)'`


## Sorting w/ `sort`
### Filter for Unique Results
`grep something | sort --unique`

# Package Management
`apt-cache rdepends --installed ` **OR** `apt-cache showpkg`
Lists reverse dependencies of a package

# Text Manipulation
`tr SET1 SET2`
Replaces all occurrences of characters, defined by `SET1`, in the standard input with replacement characters, defined by `SET2`

`wc FILE`
Prints file name, as well as number of lines, words, & characters.
## Editing Streams w/ `sed`
### Substitution
	Replaces 'this' with 'that' via regex substitution syntax. Different delimiters other than '/' may be used.
- `sed 's/this/that/'`

# Utility
`date -d @1606320072`
## Man pages
* `man -K "something"`  -  searches all man
* `/`  -  regex search within manpage  -  `n` & `Shift`+`n` to cycle through results

/home/robot/catkin_ws/src/robotise_driver/robotise_driver_base/config/base/robotise_urdf.xml

## Unix Epoch Timestamp Conversion
- `date -d @UNIX_EPOCH_TIMESTAMP`
- `date +%s -d "UTC_DATE"`
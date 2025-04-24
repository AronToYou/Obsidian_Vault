# System Commands
`ps xawf -eo pid,user,cgroups,args`
to see which service a process belongs to

`tar cvzf compressed.tar.gz ./notcompressed/` -- creates archive
`tar -xvzf compressed.tar.gz -C ./folder/` -- extracts archive

# Other Programs
## Text Manipulation
### sed & tr
> [!bash]
> `$ echo $var | sed 's/pattern/sub/g'`
> `$ echo $var | tr "pattern" "sub"`

### xclip
`xclip -sel[ection] c[lipboard] file.txt`
- copies file contents to clipboard
`xclip -o > file.txt`
- writes clipboard to file, overwriting contents
- use `>>` to append to file

## Regular Expressions
### grep
Use Perl-syntax
`$ grep -P "pattern"`
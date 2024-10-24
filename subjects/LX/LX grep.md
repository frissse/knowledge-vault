---
alias: grep 
usage: see more-info
example: cat file | grep "match this"
definition: a string and pattern matching utility that displays matching lines from multiple files
type: bash-command
subject: basic-commands
more-info: "https://www.howtogeek.com/496056/how-to-use-the-grep-command-on-linux/"
---
 
[[LX command]]

### usage

| command                                                                | usage                                        |
| ---------------------------------------------------------------------- | -------------------------------------------- |
| `journalctl \| grep -oE '([0-9]{1,3}\.){3}[0-9]{1,3}' \| sort \| uniq` | grep command to filter ips out of journalctl |

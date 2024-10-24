---
alias: umask 
usage: umask [-p] [-S] [mode]
example: umask 022
definition: sets default permissions for newly created files and directories 
type: bash-command
subject: user management
more-info: "https://www.howtogeek.com/812961/umask-linux/"
---
[[LX command]]
 

Key
   mode  File creation mask
   -S    Print the mask in symbolic format
   -p    Output in a form that can be reused as input

De waarden bij umask zijn tegengesteld aan de chmod waarden. Ze geven aan wat je NIET mag doen.

Ze gelden voor alle nieuwe bestanden en directories in de toekomst

standaard = 022

---
alias: picoCTF
type: documentation-writeup
---
### verify

checksum decrypt script to run on a bunch of files

`for file in /path/to/your/folder/*; do <bashscript.sh> <parameters>`
### scan surprise

scan a QR code
### binary search

use the [[PR binary search]] algorithms to find a number between 0 and 1000

### heap 0

use the [[CS buffer overflow]] concept to overflow the heap allocation to get the flag

### format string 0

[[PR segmentation fault]]

Unescaped % symbols: The % symbol in Cla%sic_Che%s%steak is being interpreted by functions like printf as format specifiers. 

But in this case, there are no valid specifiers after %, which causes undefined behavior and potentially a segmentation fault.

For example, in printf("Cla%sic_Che%s%steak");, the following issues occur:

%s expects a string (a char *), but since you didn't pass any additional arguments, it tries to access invalid memory, leading to a segmentation fault.

### WebDecode

use the website Inspect tool to search for the flag 
it use base64 encrypted so you need to use a tool like [[,base64 decoder]] or the cli tool on macos

### Unminify

same as idem

### Time Machine

check the git log of the file
### Super SSH

just log in with the right SSH command: right port, username and server address

### Secret of the Polyglot

file is saved in the wrong format
check it with `file` command
also for meta data use [[,exiftool]]

vervolgens kan je dan de hex gegevens bekijken met een andere tool [[,hex fiend]] 

### introToBurp

[[,burpsuite]] used to intercept traffic
by removing/replacing a part of the payload the picoCTF flag was shown in the /POST request in the 2FA

### interencdec


[[NT Networking MOC]]

### git

| command                    | explanation                                     | obsidian link                      |
| -------------------------- | ----------------------------------------------- | ---------------------------------- |
| `git log`                  | see commit history                              | [[CS picoCTF\|picoCTF]] |
| `git checkout <commit id>` | to rollback to previous commit of a file        | [[CS picoCTF\|picoCTF]] |
| `git log <file>`           | see only the commits of which the file was part | [[CS picoCTF\|picoCTF]] |
| `git checkout -`           | go back to latest commit                        | [[CS picoCTF\|picoCTF]] |
|                            |                                                 |                                    |

### ssh

| command                               | explanation                         | obsidian link                      |
| ------------------------------------- | ----------------------------------- | ---------------------------------- |
| `ssh -p <port> <>user@server-address` | login to a certain port on a server | [[CS picoCTF\|picoCTF]] |

### ftp

| `ftp<br>> get`               | downloads a file from the server onto the host | [more commands](https://en.wikipedia.org/wiki/List_of_FTP_commands) | [[NT FTP]]                     |
| ---------------------------- | ---------------------------------------------- | ------------------------------------------------------------------- | ------------------------------ |
| `smbclient -L  <ip address>` | login to SMB server                            |                                                                     | [[NT SMB]]<br>[[MT Microsoft MOC]] |

### smb

| `smbclient -L  <ip address>`      | login to SMB server                                                                                                                                             |     | [[NT SMB]]<br>[[MT Microsoft MOC]] |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | ------------------------------ |
| `smbclient \\\\ip address\\share` | inloggen op specifieke share op SMB server<br><br>rond navigeren doe je met de gebruikelijke ls cd en pwd commandos<br><br>![[Pasted image 20240912203337.png]] |     | [[NT SMB]]<br>[[MT Microsoft MOC]] |
|                                   |                                                                                                                                                                 |     |                                |

### redis

| command              | explanation                    | obsidian link |
| -------------------- | ------------------------------ | ------------- |
| `info`               | see info of database           | [[,redis]]    |
| `keys *`             | see all the keys in a database |               |
| `get <name of keys>` | see value of keyexit           |               |

### gobuster


| command                                                           | explanation                                         |               |
| ----------------------------------------------------------------- | --------------------------------------------------- | ------------- |
| `gobuster dir --url HTB  --wordlist directory-list-2.3-small.txt` | simple enumeration for hidden folder in web-content | [[,gobuster]] |

### base64

| command                                   | explanation                                              | more info                                                              | obsidian link                      |
| ----------------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------- |
| ```echo -n "decoded text" \| base64 -D``` | you can decode base64 in the terminal by piping the text | [link](https://easy64.org/knowledge-base/encode-decode-base64-on-mac/) | [[CS picoCTF\|picoCTF]] |
| ```base64 -i icon.svg```                  | also works with other files like png and svg             |                                                                        | [[CS picoCTF\|picoCTF]] |
|                                           |                                                          |                                                                        |                                    |

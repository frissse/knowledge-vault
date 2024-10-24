---
alias: lsof
usage: ls [device]
example: lsof /mnt/cdrom
definition: lists the open files in the system
type: bash-command
subject: monitoring
more-info: "https://www.howtogeek.com/426031/how-to-use-the-linux-lsof-command/#the-lsof-command"
---
 
[[LX command]]

show all listening ports and the service using it
`lsof -nP -iTCP -sTCP:LISTEN`

everything is file in [[LX linux]]

can also be used to check who uses the network

`lsof -i4`

columns
- Command: The name of the command associated with the process that opened the file.
- PID: Process Identification number of the process that opened the file.
- TID: Task (thread) Identification number. A blank column means it is not a task; it is a process.
- User: User ID or name of the user to whom the process belongs, or the user ID or login of the person that owns the directory in `/proc` where `lsof` finds information about the process.
- FD: Shows the file descriptor of the file. File descriptors are described below.
- Type: type of node associated with the file. Note types are described below.
- Device: Contains either the device numbers, separated by commas, for a character special, block special, regular, directory or NFS file, or a kernel reference address that identifies the file. It might also show the base address or device name of a Linux AX.25 socket device.
- Size/Off: Shows the size of the file or the file offset in bytes.
- Node: Shows the node number of a local file, or the inode number of an NFS file in the server host, or internet protocol type. It might display STR for a stream or the IRQ or inode number of a Linux AX.25 socket device.
- Name: Shows the name of the mount point and file system on which the file resides.


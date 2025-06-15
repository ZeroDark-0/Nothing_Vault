---
date: 2025-06-15T21:57
tags: []
---

# <code style="color:red">Linux</code>

| -> Kernel (Core of OS)
| -> Shell (interface between user and OS
| -> File System 


## <code style="color:blue">File & Directory Navigation</code>

| Command    | Description                     |
| ---------- | ------------------------------- |
| `pwd`      | Print current working directory |
| `ls`       | List directory contents         |
| `ls -l`    | Long listing format             |
| `ls -a`    | Show hidden files               |
| `cd <dir>` | Change directory                |
| `cd ..`    | Move up one directory           |
| `cd ~`     | Go to home directory            |

## <code style="color:purple">Viewing & Editing Files</code>
|Command|Description|
|---|---|
|`cat <file>`|Show file content|
|`less <file>`|Scrollable view of file|
|`head <file>`|First 10 lines of a file|
|`tail <file>`|Last 10 lines of a file|
|`nano <file>`|Simple text editor|
|`vim <file>`|Advanced text editor|
## <code style="color:cyan">Permissions & Ownership</code>
|Command|Description|
|---|---|
|`chmod <mode> <file>`|Change file permissions|
|`chown <user>:<group> <file>`|Change file owner|
|`ls -l`|Shows file permissions & owners|
## <code style="color:pink">System Info</code>
|Command|Description|
|---|---|
|`uname -a`|Full system info|
|`top`|Real-time process view|
|`htop`|Better `top` (if installed)|
|`df -h`|Disk usage (human-readable)|
|`du -sh <dir>`|Size of directory|
|`free -h`|RAM info|
|`whoami`|Show current user|
|`id`|Show user ID and group info|

## <code style="color:yellow">Searching</code>
|Command|Description|
|---|---|
|`find <dir> -name <file>`|Find file by name|
|`grep <pattern> <file>`|Search text in a file|
|`grep -r <pattern> <dir>`|Recursive search|

## <code style ="color:green">Sudo & Root</code>

|Command|Description|
|---|---|
|`sudo <command>`|Run command as root|
|`su`|Switch to root user|
|`exit`|Exit current session or user|

---


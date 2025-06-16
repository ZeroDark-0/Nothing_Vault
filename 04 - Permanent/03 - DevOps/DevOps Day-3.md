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

1. Greet a User by Name
Description: Take a name as an argument and greet the user.


#!/bin/bash
echo "Hello, $1! Welcome to EC2."
Run: ./greet.sh Alice

 2. Add Two Numbers
Description: Accept two numbers as arguments and print their sum.


#!/bin/bash
sum=$(( $1 + $2 ))
echo "Sum: $sum"
Run: ./add.sh 5 7

3. Check if File Exists
Description: Ask for a filename and check if it exists.


#!/bin/bash
read -p "Enter filename: " file
if [ -f "$file" ]; then
  echo "File exists."
else
  echo "File not found."
fi
Run: ./filecheck.sh

 4. Count Lines in a File
Description: Accept a filename and print the line count.

#!/bin/bash
lines=$(wc -l < "$1")
echo "Line count: $lines"
Run: ./countlines.sh file.txt

 5. Print All Arguments
Description: Print every argument passed to the script.

#!/bin/bash
echo "You entered $# arguments:"
for arg in "$@"; do
  echo "$arg"
done
Run: ./args.sh one two three

6. Simple Calculator
Description: Take two numbers and an operator (+ - * /), then compute the result.

#!/bin/bash
case $2 in
  +) echo "$(($1 + $3))" ;;
  -) echo "$(($1 - $3))" ;;
  \*) echo "$(($1 * $3))" ;;
  /) echo "$(($1 / $3))" ;;
  *) echo "Unknown operator" ;;
esac
Run: ./calc.sh 5 + 3

7. Loop Through Numbers 1–5
Description: Use a loop to print numbers from 1 to 5.


#!/bin/bash
for i in {1..5}; do
  echo "Number: $i"
done
Run: ./loop.sh

 8. Create a Backup Copy of a File
Description: Copy a file and add .bak to its name.


#!/bin/bash
cp "$1" "$1.bak"
echo "Backup created: $1.bak"
Run: ./backup.sh test.txt

 9. Check if User is Root
Description: Print a message if the script is run as root or not.

#!/bin/bash
if [ "$UID" -eq 0 ]; then
  echo "Running as root"
else
  echo "Not root"
fi
Run: ./checkroot.sh

 10. Disk Usage Alert
Description: Warn if disk usage goes above 80%


#!/bin/bash
usage=$(df / | grep / | awk '{ print $5 }' | sed 's/%//')
if [ "$usage" -gt 80 ]; then
  echo "Warning: Disk usage is over 80%!"
else
  echo "Disk usage is OK: ${usage}%"
fi
Run: ./diskalert.sh
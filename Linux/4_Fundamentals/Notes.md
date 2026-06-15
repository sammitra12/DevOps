I've rewritten and organized your notes into a cleaner training-document format:

# Linux Commands and File Management Notes

## Command Syntax

Most Linux commands follow this structure:

```bash
command [options] [arguments]
```

Example:

```bash
ls -l /home
```

* `ls` → command
* `-l` → option
* `/home` → argument

---

# File Permissions

Linux controls file access through three permission types:

| Permission | Meaning |
| ---------- | ------- |
| `r`        | Read    |
| `w`        | Write   |
| `x`        | Execute |

Permissions can be assigned at three levels:

| Symbol | Description              |
| ------ | ------------------------ |
| `u`    | User (owner of the file) |
| `g`    | Group                    |
| `o`    | Others (everyone else)   |

Example:

```text
-rwxrwxrwx
 ||| ||| |||
  u   g   o
```

### Changing Permissions with chmod

The `chmod` command is used to modify file or directory permissions.

Examples:

```bash
chmod g-w jerry
```

Remove write permission from the group.

```bash
chmod u+rw jerry
```

Add read and write permissions for the owner.

---

# File Ownership

Linux files have both an owner and a group owner.

### Commands

```bash
chown
```

Changes file ownership.

```bash
chgrp
```

Changes group ownership.

Examples (run as root):

```bash
chown root filename
```

Change file owner to root.

```bash
chgrp root filename
```

Change file group to root.

---

# Access Control Lists (ACL)

ACLs provide more granular permissions than standard Linux permissions.

### Add permissions for a user

```bash
setfacl -m u:user:rwx /path/to/file
```

### Add permissions for a group

```bash
setfacl -m g:group:rw /path/to/file
```

### Set default ACLs (inheritance)

```bash
setfacl -dm "entry" /path/to/directory
```

### Remove ACL for a specific user

```bash
setfacl -x u:user /path/to/file
```

### Remove all ACL entries

```bash
setfacl -b /path/to/file
```

### View ACL entries

```bash
getfacl filename
```

---

# Getting Help

### Quick description

```bash
whatis command
```

### Built-in help

```bash
command --help
```

### Manual pages

```bash
man command
```

Example:

```bash
man chmod
```

---

# Input and Output Redirection

### Overwrite output

```bash
command > file
```

### Append output

```bash
command >> file
```

---

# Pipes (|)

A pipe sends the output of one command directly to another command.

Syntax:

```bash
command1 | command2
```

Example:

```bash
cat file.txt | grep error
```

---

# Running Multiple Commands

Use a semicolon (`;`) to execute multiple commands sequentially.

```bash
pwd; ls; date
```

---

# Copy Files from Windows to Linux VM

When connected to a Linux VM via SSH, use SCP (Secure Copy) to transfer files.

Example:

```bash
scp C:\Users\YourName\Documents\test.txt username@VM_IP:/home/username/
```

---

# File Maintenance Commands

## grep

Searches text line by line and displays matching lines.

Syntax:

```bash
grep keyword filename
```

Common options:

```bash
-i
```

Case-insensitive search.

```bash
-c
```

Display count of matching lines.

```bash
-n
```

Display matching lines with line numbers.

```bash
-v
```

Display lines that do NOT match.

Example:

```bash
grep -i linux notes.txt
```

---

## egrep

Used to search for multiple patterns.

Example:

```bash
egrep -i "keyword1|keyword2" filename
```

---

# sort and uniq

## sort

Sorts lines alphabetically.

```bash
sort filename
```

Options:

```bash
sort -r filename
```

Reverse order.

```bash
sort -k2 filename
```

Sort by second column.

---

## uniq

Removes duplicate adjacent lines.

```bash
uniq filename
```

Common usage:

```bash
sort filename | uniq
```

Sort first, then remove duplicates.

```bash
sort filename | uniq -c
```

Display occurrence count.

```bash
sort filename | uniq -d
```

Display only duplicated lines.

---

# wc (Word Count)

Displays line count, word count, and byte count.

```bash
wc filename
```

Common options:

```bash
wc -l filename
```

Number of lines.

```bash
wc -w filename
```

Number of words.

```bash
wc -b filename
```

Number of bytes.

Count matching lines:

```bash
grep keyword filename | wc -l
```

---

# Compression and Archiving

## TAR Archive

A `.tar` file combines multiple files into a single archive but does not compress them.

### Create Archive

```bash
tar cvf archive.tar directory/
```

### Extract Archive

```bash
tar xvf archive.tar
```

### TAR Options

| Option | Description                   |
| ------ | ----------------------------- |
| `c`    | Create a new archive          |
| `x`    | Extract files from an archive |
| `v`    | Verbose mode                  |
| `f`    | Specify archive filename      |

---

## GZIP Compression

Compress a TAR archive:

```bash
gzip archive.tar
```

Result:

```text
archive.tar.gz
```

### Decompress

```bash
gzip -d archive.tar.gz
```

or

```bash
gunzip archive.tar.gz
```

This restores the original `.tar` file.

---

# Useful Reminder

Whenever you need help with a command:

```bash
man command_name
```

Example:

```bash
man grep
```

This version is formatted for a Linux training course, README, or study notes.

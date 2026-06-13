
# Module 2 - Linux Installation and Basic Commands

## Network Configuration Commands

### Display Network Information

```bash
ifconfig
```

```bash
ip addr
```

---

## SSH (Secure Shell)

Connect to a remote Linux machine:

```bash
ssh -l <username> <ip_address>
```

Example:

```bash
ssh -l student 192.168.1.10
```

---

## Linux Command Prompt Structure

Example Prompt:

```bash
[root@MyFirstLinuxVM ~]$
```

### Components

| Part           | Description       |
| -------------- | ----------------- |
| root           | Username          |
| MyFirstLinuxVM | Hostname          |
| ~              | Current Directory |
| $ / #          | Prompt Symbol     |

Format:

```text
username@hostname
```

---

## Password Management

Change user password:

```bash
passwd
```

---

## Linux File Systems

Common Linux File Systems:

* ext3
* ext4
* xfs

Windows File Systems:

* NTFS
* FAT

---

## File Management

### Create a File

```bash
touch file.txt
```

### Edit/Create File using VI Editor

```bash
vi file.txt
```

### Copy a File

```bash
cp source_file destination_file
```

---

## Directory Management

### Create Directory

```bash
mkdir myfolder
```

### List Files and Directories

```bash
ls -lr
```

### Copy Directory

```bash
cp -R <source_dir> <destination_dir>
```

Example:

```bash
cp -R project backup_project
```

---

## Finding Files and Directories

### Using find Command

```bash
find . -name <file_name>
```

Example:

```bash
find . -name notes.txt
```

### Using locate Command

```bash
locate notes.txt
```

---

## Switching Users

### Switch to Root User

```bash
su -
```

### Switch to Another User

```bash
su - <username>
```

Example:

```bash
su - student
```

---

## Update Locate Database

The `locate` command uses a database to search files quickly.

Update the database:

```bash
updatedb
```

---

## Wildcards in Linux

| Wildcard | Description                          |
| -------- | ------------------------------------ |
| *        | Matches zero or more characters      |
| ?        | Matches a single character           |
| []       | Matches a range or set of characters |
| {}       | Brace expansion                      |

Examples:

```bash
ls *.txt
```

```bash
ls file?.txt
```

```bash
ls file[1-5].txt
```

```bash
mkdir project{1,2,3}
```

---

## Inode

### What is an Inode?

An inode is a data structure that stores metadata about a file.

It contains information such as:

* File size
* Ownership
* Permissions
* Timestamps
* Location of file data on disk

Think of an inode as a pointer or unique number assigned to a file on the hard disk.

View inode numbers:

```bash
ls -i
```

---

## Links in Linux

### Hard Link

Creates another file entry pointing to the same inode.

```bash
ln original.txt hardlink.txt
```

Characteristics:

* Shares the same inode number
* Cannot span across file systems
* Works only for files

### Soft Link (Symbolic Link)

Creates a shortcut pointing to the original file.

```bash
ln -s original.txt softlink.txt
```

Characteristics:

* Has a different inode
* Can span across file systems
* Can link files and directories

View links:

```bash
ls -li
```

---


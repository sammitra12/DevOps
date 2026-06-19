Here's a cleaned-up, organized, and corrected version of your notes that can be used as Linux Administration study material.

# Linux Administration Notes

# VI Editor

The `vi` editor is used to create and edit text files.

### Common Commands

| Command      | Description                        |
| ------------ | ---------------------------------- |
| `u`          | Undo last change                   |
| `dd`         | Delete current line                |
| `x`          | Delete character under cursor      |
| `o`          | Open a new line below current line |
| `Shift + ZZ` | Save and exit                      |

### Search

Press `Esc` and type:

```bash
/keyword
```

Press `n` to move to the next occurrence.

> Note: Most VI commands work only after pressing `Esc` to enter Command Mode.

---

# Sed Command

`sed` (Stream Editor) is used to search, replace, insert, and delete text within files.

### Replace Text

```bash
sed -i 's/oldtext/newtext/g' filename
```

Example:

```bash
sed -i 's/linux/unix/g' notes.txt
```

If `newtext` is empty, the matching text is removed.

### Delete Lines Containing a Word

```bash
sed -i '/word/d' filename
```

### Remove Empty Lines

```bash
sed -i '/^$/d' filename
```

### Delete Specific Line

```bash
sed -i '5d' filename
```

Deletes line 5.

### Replace Tabs with Spaces

```bash
sed 's/\t/ /g' filename
```

### Display Specific Lines

```bash
sed -n '12,18p' filename
```

Displays lines 12 through 18.

---

# User and Group Management

### Commands

```bash
useradd
groupadd
userdel
groupdel
usermod
```

### Important Files

| File          | Purpose                                            |
| ------------- | -------------------------------------------------- |
| `/etc/passwd` | User account information                           |
| `/etc/group`  | Group information                                  |
| `/etc/shadow` | Encrypted passwords and password-aging information |

### Create User

```bash
useradd username
```

Verify:

```bash
ls -ltr /home
```

### Create Group

```bash
groupadd groupname
```

Verify:

```bash
grep groupname /etc/group
```

### Add User to Group

```bash
usermod -G groupname username
```

### Change Group Ownership

```bash
chgrp -R groupname /home/user1 /home/user2
```

---

# Understanding /etc/passwd

Example:

```text
amar:x:1001:1001::/home/amar:/bin/bash
```

Fields:

```text
username:password:UID:GID:comment:home:shell
```

| Field      | Meaning                          |
| ---------- | -------------------------------- |
| amar       | Username                         |
| x          | Password stored in `/etc/shadow` |
| 1001       | User ID (UID)                    |
| 1001       | Group ID (GID)                   |
| /home/amar | Home directory                   |
| /bin/bash  | Login shell                      |

---

# Understanding /etc/shadow

Example:

```text
amar:!!:20620:0:99999:7:::
```

`!!` means:

```text
No password has been set yet.
```

Set a password:

```bash
passwd username
```

After setting a password, `!!` is replaced with a password hash.

---

# Corporate User Creation Example

```bash
useradd \
-g developers \
-s /bin/bash \
-c "Application Developer" \
-m \
-d /home/john \
john
```

Options:

| Option | Description             |
| ------ | ----------------------- |
| `-g`   | Primary group           |
| `-s`   | Login shell             |
| `-c`   | Comment/description     |
| `-m`   | Create home directory   |
| `-d`   | Home directory location |

---

# Password Aging

View password policies:

```bash
cat /etc/login.defs
```

Manage password aging:

```bash
chage [options] username
```

Common options:

| Option | Meaning                 |
| ------ | ----------------------- |
| `-m`   | Minimum password age    |
| `-M`   | Maximum password age    |
| `-W`   | Warning days            |
| `-E`   | Account expiration date |
| `-I`   | Inactive period         |

---

# User Monitoring

### Current Logged-In Users

```bash
who
```

### Login History

```bash
last
```

### List Logged-In Usernames

```bash
users
```

### Broadcast Message

```bash
wall
```

Type message and press:

```text
Ctrl + D
```

to send.

### Send Message to One User

```bash
write username
```

---

# Processes, Services and Jobs

## Definitions

### Application / Service

A program running on the system.

### Process

An instance of a running application.

### Daemon

A background process that continuously runs and waits for requests.

Examples:

```text
sshd
crond
httpd
```

### Thread

A lightweight execution unit inside a process.

### Job

A scheduled task or background task.

---

# Process Monitoring

## ps

Displays running processes.

```bash
ps
```

Fields:

| Field | Meaning           |
| ----- | ----------------- |
| PID   | Process ID        |
| TTY   | Terminal          |
| TIME  | CPU time consumed |
| CMD   | Command name      |

---

# Service Management

## systemctl

Manage system services.

### Start Service

```bash
systemctl start service.service
```

### Stop Service

```bash
systemctl stop service.service
```

### Check Status

```bash
systemctl status service.service
```

### Enable Service at Boot

```bash
systemctl enable service.service
```

### Restart Service

```bash
systemctl restart service.service
```

### Reload Configuration

```bash
systemctl reload service.service
```

### List Units

```bash
systemctl list-units --all
```

---

## Service Unit Files

Location:

```bash
/etc/systemd/system/
```

Example:

```bash
/etc/systemd/system/myapp.service
```

---

# System Control Commands

```bash
systemctl poweroff
systemctl halt
systemctl reboot
```

---

# Top Command

Displays real-time system performance and processes.

```bash
top
```

Important columns:

| Column | Meaning           |
| ------ | ----------------- |
| PID    | Process ID        |
| USER   | Process owner     |
| PR     | Priority          |
| NI     | Nice value        |
| VIRT   | Virtual memory    |
| RES    | Physical RAM used |
| SHR    | Shared memory     |
| S      | Process state     |
| %CPU   | CPU usage         |
| %MEM   | Memory usage      |
| TIME+  | CPU time used     |

---

# Kill Command

Terminate processes.

```bash
kill PID
```

Examples:

```bash
kill 1234
kill -9 1234
```

### Common Signals

| Signal | Meaning                        |
| ------ | ------------------------------ |
| `-15`  | Graceful termination (default) |
| `-9`   | Force kill                     |

---

# Scheduling Jobs

## Cron

Schedule recurring tasks.

```bash
crontab -e
```

## At

Schedule one-time tasks.

```bash
at
```

---

# Background Processes

### Run in Background

```bash
nohup sleep 75 &
```

### View Jobs

```bash
jobs
```

### Move Job to Background

```bash
bg
```

### Bring Job to Foreground

```bash
fg
```

### Suppress Output

```bash
nohup command > /dev/null 2>&1 &
```

---

# System Monitoring

### Disk Usage

```bash
df -h
```

### Kernel Messages

```bash
dmesg
```

### CPU and I/O Statistics

```bash
iostat
```

### Memory Usage

```bash
free -h
```

### CPU Information

```bash
cat /proc/cpuinfo
```

---

# Log Monitoring

Most logs are stored in:

```bash
/var/log
```

---

# Journalctl

View systemd logs.

### View Logs

```bash
journalctl | less
```

### Last 20 Entries

```bash
journalctl -n 20
```

### Follow Logs Live

```bash
journalctl -f
```

### Current Boot Logs

```bash
journalctl -b
```

### List Previous Boots

```bash
journalctl --list-boots
```

### SSH Service Logs

```bash
journalctl -u sshd
```

### Logs Since a Specific Time

```bash
journalctl --since "2026-06-11 10:00:00"
```

### Error Logs Only

```bash
journalctl -p err
```

---

# SOS Report

Generate a complete system diagnostic report.

```bash
sosreport
```

or

```bash
sos report
```

Useful for troubleshooting and support cases.

---

# Terminal Shortcuts

| Shortcut | Function                            |
| -------- | ----------------------------------- |
| Ctrl + U | Clear line from cursor to beginning |
| Ctrl + C | Stop current command                |
| Ctrl + Z | Suspend current command             |
| Ctrl + D | Exit shell or signal EOF            |

---

# Script Command

Record terminal sessions.

```bash
script logfile.txt
```

Stop recording:

```bash
exit
```

---

# Environment Variables

### View Environment Variables

```bash
env
```

### Display Variable Value

```bash
echo $VARIABLE_NAME
```

### User-Specific Variables

```bash
vi ~/.bashrc
```

### Global Variables

```bash
vi /etc/profile
```

---

# systemctl vs kill

| Feature             | systemctl | kill             |
| ------------------- | --------- | ---------------- |
| Operates On         | Services  | Processes        |
| Uses Service Name   | Yes       | No               |
| Uses PID            | No        | Yes              |
| Graceful Management | Yes       | Limited          |
| Start Service       | Yes       | No               |
| Stop Service        | Yes       | Yes (indirectly) |
| Restart Service     | Yes       | No               |

Example:

```bash
systemctl restart sshd
```

restarts the SSH service properly.

```bash
kill -9 1234
```

forcibly terminates process ID 1234 without allowing cleanup.

**Rule of thumb:** Use `systemctl` for managing services and `kill` for managing individual processes.

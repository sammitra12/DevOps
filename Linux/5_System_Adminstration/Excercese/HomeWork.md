# Linux Administration Practice Lab

## Objective

Practice file editing, user and group management, permissions, system administration, and basic troubleshooting commands.

---

## 1. File Creation and VI Editor Practice

1. Navigate to your home directory and then move to the `superman` directory.
2. Create a new file named `first4movies` using the `vi` editor.
3. Enter content about the first four Superman movies.

   * If you have not watched the movies, enter at least 20 names of family members or friends.
   * The file should contain:

     * At least 20 lines
     * Each line should contain 5–6 words
4. Practice using `vi` by:

   * Navigating through the file
   * Editing existing text
   * Deleting lines
   * Undoing changes
5. Save and exit the file.

---

## 2. Group and User Management

### Create a Group

1. Create a group named `superheros` (if it does not already exist).

### Create User Hulk

1. Create a user named `hulk`.
2. Assign:

   * Primary group: `superheros`
   * User ID (UID): `2000`
3. Set a password for `hulk`.
4. Log in as the `hulk` user.

### File Ownership Practice

1. In Hulk's home directory, create a file named `Skaar`.
2. Change the group ownership of `Skaar` from `superheros` to `root`.

---

## 3. Create Multiple Users and Groups

### Create a Group

1. Create a group named `continents`.

### Create Users

Create the following users and assign them to the `continents` group:

* namerica
* samerica
* asia
* europe
* australia
* africa
* antarctica

### User Setup

1. Set passwords for all users.
2. Switch to each user account using:

```bash
su - username
```

3. Create one file in each user's home directory:

| User       | File Name |
| ---------- | --------- |
| europe     | england   |
| namerica   | usa       |
| asia       | japan     |
| samerica   | brazil    |
| australia  | sydney    |
| africa     | kenya     |
| antarctica | ice       |

---

## 4. Sudo Privileges

1. Add user `namerica` to the `wheel` group.
2. Verify that `namerica` can execute administrative commands using `sudo`.

---

## 5. User and System Information

### Logged-In Users

1. Run the `last` command.
2. Determine the number of unique users who have logged in.

   * Do not count duplicate logins.

### User IDs

1. Run the `id` command for:

   * africa
   * australia

2. Verify their:

   * UID
   * GID
   * Group membership

---

## 6. Date and Time Management

1. Change the system date and time to:

```text
August 22, 1998
1:00 PM
```

2. Verify the change using the appropriate command.

---

## 7. System Information

### Check Uptime

Display the system uptime.

### Calendar

Display the calendar for the year:

```text
1999
```

### Kernel Information

Use the `uname` command to display all available system information.

Identify which field contains the system architecture information.

---

## 8. Disk Usage and File Editing

1. Switch back to your personal user account.
2. Run:

```bash
df -h
```

3. Redirect the output to a file named:

```text
systemdiskinfo
```

4. Open the file using `vi`.
5. Remove the first two lines.
6. Save and exit.

---

## 9. Kernel Message Processing

1. Run:

```bash
dmesg
```

2. Redirect the output to a file named:

```text
dm-file
```

3. Open `dm-file` using `vi`.
4. Remove the last 5–7 lines.
5. Add the following text at the end of the file:

```text
This is the end of the file.
```

6. Save and exit.

---

## 10. System Reboot

1. Reboot the system using the `init` command.

---

## Expected Learning Outcomes

After completing this lab, you should be able to:

* Use the `vi` editor effectively
* Create and manage users and groups
* Modify file ownership and permissions
* Configure sudo access
* Work with system date and time
* Retrieve system information
* Process command output using redirection
* Analyze login history
* Edit system-generated files
* Perform a controlled system reboot

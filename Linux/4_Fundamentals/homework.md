Here's a cleaner and more professional version of your Linux practice exercise:

# Linux Command Practice Lab

## Objective

Practice Linux command syntax, including commands, options, arguments, file management, permissions, ownership, navigation, and text-processing utilities.

---

### 1. File Listing and Organization

1. List all files in your home directory sorted by their last modification time.
2. Move the files `jerry`, `george`, `kramer`, and `puddy` into the `seinfeld` directory.
3. Move the files `homer`, `bart`, `marge`, and `lisa` into the `simpsons` directory.
4. Move the files `clark`, `luther`, and `lois` into the `superman` directory.
5. List the contents of the `seinfeld` directory sorted by the last modification time.

---

### 2. File Creation and Permissions

1. Create two new files in the `seinfeld` directory:

   * `eliane`
   * `newman`
2. Modify the permissions of `eliane` to remove read access for everyone.
3. Modify the permissions of `newman` to add write permission only for the group.

---

### 3. Ownership and File Management

1. Switch to the root user.
2. Navigate to your home directory (for example: `/home/username`).
3. Create two new files in the `superman` directory:

   * `superman`
   * `zad`
4. Change the ownership of `zad` from `root` to your user account.
5. Change the group ownership of `zad` from `root` to your user group.
6. Move the `superman` file to the `/tmp` directory.
7. Delete the `superman` file from `/tmp`.
8. Exit the root account.

---

### 4. Working with File Contents

1. Navigate to the `superman` directory.

2. Add the following line to the `zad` file:

   ```
   zad is a bad character in superman movie
   ```

3. Navigate to the `seinfeld` directory.

4. Create a new file named `seinfeld`.

5. Add the following character names to the file:

   * Jerry Seinfeld
   * George Costanza
   * Eliane Benes
   * Cosmo Kramer
   * David Puddy

---

### 5. Log File Operations

1. Become the root user again.
2. Display the contents of `/var/log/messages` and redirect the output to a file named `mesg-new` in your home directory.
3. Read the `mesg-new` file using:

   * `cat`
   * `more`
   * `less`
4. Extract the first 10 lines of `mesg-new` and save them to a file named `mesg-h10`.
5. Extract the last 20 lines of `mesg-new` and save them to a file named `mesg-t20`.
6. Exit the root account.

---

### 6. Text Processing Practice

1. Navigate to the `seinfeld` directory.

2. Create a file named `seinfeld-characters`.

3. Add the following names, one per line, using the `echo` command:

   * Jerry Seinfeld
   * Cosmo Kramer
   * Eliane Benes
   * George Costanza
   * Newman Mailman
   * Frank Costanza
   * Estelle Costanza
   * Morty Seinfeld
   * Helen Seinfeld
   * Babes Kramer
   * Alton Benes
   * J Peterman
   * George Steinbrenner
   * Uncle Leo
   * David Puddy
   * Justin Pitt
   * Kenny Bania

4. Use the `cut` command to extract the first four characters of each line and save the output to a file named `filters-file`.

5. Use the `awk` command to extract only the second column (last names) and append the output to `filters-file`.

6. Use the `grep` command to find all entries containing `Seinfeld` and save the results to a file named `seinfeld-family`.

7. Practice using the following commands with either existing or new files:

   * `sort`
   * `uniq`
   * `wc`

---

### Expected Learning Outcomes

After completing this lab, you should be comfortable with:

* File and directory management
* Linux command syntax
* File permissions and ownership
* User switching (`su`)
* Input/output redirection
* Viewing and manipulating file contents
* Text processing using `cut`, `awk`, `grep`, `sort`, `uniq`, and `wc`
* Working with system log files

# Linux Basic Commands

This guide introduces essential Linux commands, their manual (man) page references, and practical examples.

---

## 1. `pwd` - Print Working Directory

- **Man Page:** `man pwd`
- **Example:**
    ```bash
    pwd
    ```
    *Displays the current directory path.*

---

## 2. `ls` - List Directory Contents

- **Man Page:** `man ls`
- **Example:**
    ```bash
    ls -l
    ```
    *Lists files and directories with details.*

---

## 3. `cd` - Change Directory

- **Man Page:** `man cd` (built-in, see `help cd`)
- **Example:**
    ```bash
    cd /home/user
    ```
    *Changes to `/home/user` directory.*

---

## 4. `cat` - Concatenate and Display Files

- **Man Page:** `man cat`
- **Example:**
    ```bash
    cat file.txt
    ```
    *Displays contents of `file.txt`.*

---

## 5. `cp` - Copy Files and Directories

- **Man Page:** `man cp`
- **Example:**
    ```bash
    cp source.txt destination.txt
    ```
    *Copies `source.txt` to `destination.txt`.*

---

## 6. `mv` - Move/Rename Files and Directories

- **Man Page:** `man mv`
- **Example:**
    ```bash
    mv oldname.txt newname.txt
    ```
    *Renames `oldname.txt` to `newname.txt`.*

---

## 7. `rm` - Remove Files or Directories

- **Man Page:** `man rm`
- **Example:**
    ```bash
    rm file.txt
    ```
    *Deletes `file.txt`.*

---

## 8. `mkdir` - Make Directories

- **Man Page:** `man mkdir`
- **Example:**
    ```bash
    mkdir new_folder
    ```
    *Creates a directory named `new_folder`.*

---

## 9. `rmdir` - Remove Empty Directories

- **Man Page:** `man rmdir`
- **Example:**
    ```bash
    rmdir old_folder
    ```
    *Removes the empty directory `old_folder`.*

---

## 10. `man` - Manual Pages

- **Man Page:** `man man`
- **Example:**
    ```bash
    man ls
    ```
    *Shows the manual for the `ls` command.*

---

**Tip:** Use `man <command>` to learn more about any command.

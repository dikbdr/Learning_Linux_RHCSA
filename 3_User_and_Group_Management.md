# User and Group Management

## Creating and Managing Users
Managing users is a fundamental task in Linux system administration. Below are the steps to create and manage users:

### Steps:
1. **Create a User**:
    Use the `useradd` command:
    ```bash
    sudo useradd username
    ```
    Example:
    ```bash
    sudo useradd alice
    ```

2. **Set a Password**:
    Use the `passwd` command:
    ```bash
    sudo passwd username
    ```
    Example:
    ```bash
    sudo passwd alice
    ```

3. **Modify User Details**:
    Use the `usermod` command:
    ```bash
    sudo usermod -c "Comment" username
    ```
    Example:
    ```bash
    sudo usermod -c "Alice's account" alice
    ```

4. **Delete a User**:
    Use the `userdel` command:
    ```bash
    sudo userdel username
    ```
    Example:
    ```bash
    sudo userdel alice
    ```

---

## Understanding Groups
Groups allow multiple users to share access to files and directories.

### Steps:
1. **Create a Group**:
    ```bash
    sudo groupadd groupname
    ```
    Example:
    ```bash
    sudo groupadd developers
    ```

2. **Add a User to a Group**:
    ```bash
    sudo usermod -aG groupname username
    ```
    Example:
    ```bash
    sudo usermod -aG developers alice
    ```

3. **View Group Membership**:
    ```bash
    groups username
    ```
    Example:
    ```bash
    groups alice
    ```

---

## File Permissions and Ownership
Linux uses a permission system to control access to files and directories.

### Steps:
1. **View Permissions**:
    ```bash
    ls -l
    ```
    Example Output:
    ```
    -rw-r--r-- 1 alice developers 1024 Oct 10 12:00 file.txt
    ```

2. **Change Ownership**:
    ```bash
    sudo chown username:groupname filename
    ```
    Example:
    ```bash
    sudo chown alice:developers file.txt
    ```

3. **Modify Permissions**:
    ```bash
    chmod permissions filename
    ```
    Example:
    ```bash
    chmod 755 file.txt
    ```

---

## Special Permissions (SUID, SGID, Sticky Bit)
Special permissions provide additional control over files and directories.

### Examples:
1. **Set SUID**:
    ```bash
    chmod u+s filename
    ```
    Example:
    ```bash
    chmod u+s /usr/bin/passwd
    ```

2. **Set SGID**:
    ```bash
    chmod g+s directory
    ```
    Example:
    ```bash
    chmod g+s /shared
    ```

3. **Set Sticky Bit**:
    ```bash
    chmod +t directory
    ```
    Example:
    ```bash
    chmod +t /tmp
    ```

---

### Diagram Example:
Below is a simple representation of file permissions:

```
-rwxr-xr-- 1 alice developers 1024 Oct 10 12:00 file.txt
|---|---|---|
|   |   |   |
|   |   |   +-- Other Permissions
|   |   +------ Group Permissions
|   +---------- Owner Permissions
+-------------- File Type
```

This breakdown helps understand how permissions are structured in Linux.
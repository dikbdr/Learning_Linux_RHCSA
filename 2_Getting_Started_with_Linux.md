# Getting Started with Linux

## Table of Contents
- [Installing Linux (VirtualBox/VMware Setup)](#installing-linux-virtualboxvmware-setup)
- [Basic Linux Commands](#basic-linux-commands)
- [Understanding the Linux File System Hierarchy](#understanding-the-linux-file-system-hierarchy)
- [Navigating the Command Line](#navigating-the-command-line)

---

## Installing Linux (VirtualBox/VMware Setup)
Learn how to set up a Linux environment using VirtualBox or VMware. This section will guide you through downloading an ISO, creating a virtual machine, and installing Linux.

### Steps:
1. **Download VirtualBox or VMware**:
   - Visit the official website of [VirtualBox](https://www.virtualbox.org/) or [VMware](https://www.vmware.com/) and download the software for your operating system.

2. **Download a Linux ISO**:
   - Choose a Linux distribution (e.g., Ubuntu, CentOS, Fedora) and download the ISO file from the official website.

3. **Create a Virtual Machine**:
   - Open VirtualBox or VMware.
   - Click on "New" to create a new virtual machine.
   - Assign a name, select the operating system type (Linux), and choose the version (e.g., Ubuntu 64-bit).

4. **Allocate Resources**:
   - Assign memory (RAM) and CPU cores to the virtual machine.
   - Create a virtual hard disk and allocate storage space.

5. **Attach the ISO**:
   - Go to the virtual machine settings and attach the downloaded Linux ISO as a bootable disk.

6. **Start the Virtual Machine**:
   - Boot the virtual machine and follow the on-screen instructions to install Linux.

---

## Basic Linux Commands
Familiarize yourself with essential Linux commands:

| Command | Description                          | Example Usage                     |
|---------|--------------------------------------|-----------------------------------|
| `ls`    | List directory contents             | `ls`                             |
| `cd`    | Change directory                    | `cd /path/to/directory`          |
| `pwd`   | Print working directory             | `pwd`                            |
| `mkdir` | Create directories                  | `mkdir new_directory`            |
| `rm`    | Remove files or directories         | `rm file_name` or `rm -r folder` |

---

## Understanding the Linux File System Hierarchy
Explore the structure of the Linux file system, including:

| Directory | Description                                      |
|-----------|--------------------------------------------------|
| `/`       | Root directory, the top-level directory in Linux |
| `/home`   | User home directories (e.g., `/home/user`)       |
| `/etc`    | Configuration files for the system and apps      |
| `/var`    | Variable data files like logs and caches         |
| `/usr`    | User programs and data                          |

---

## Navigating the Command Line
Master navigation in the Linux command line:

### Tips:
- **Tab Auto-Completion**:
  - Press `Tab` to auto-complete file or directory names.
- **Command History**:
  - Use the `history` command to view previously executed commands.
  - Press the `Up` and `Down` arrow keys to scroll through the history.
- **Keyboard Shortcuts**:
  - `Ctrl+C`: Terminates the current process.
  - `Ctrl+R`: Searches the command history in reverse.

---


## Package Management

### Understanding Package Managers (YUM, DNF, RPM)
Package managers are tools that simplify the process of installing, updating, and managing software on Linux systems. Common package managers include:
- **YUM (Yellowdog Updater, Modified)**: Used in older versions of RHEL-based distributions.
- **DNF (Dandified YUM)**: A modern replacement for YUM, offering better performance and dependency resolution.
- **RPM (Red Hat Package Manager)**: A low-level tool for managing `.rpm` packages.

#### Example:
To query an installed package using RPM:
```bash
rpm -q bash
```

### Installing, Updating, and Removing Software
Package managers allow you to install, update, or remove software efficiently.

#### Installing Software:
Using DNF:
```bash
sudo dnf install httpd
```

#### Updating Software:
To update all packages:
```bash
sudo dnf update
```

#### Removing Software:
To remove a package:
```bash
sudo dnf remove httpd
```

### Managing Repositories
Repositories are collections of software packages. You can enable, disable, or add repositories to manage available software.

#### Example:
To list enabled repositories:
```bash
sudo dnf repolist
```

#### Adding a Repository:
Create a `.repo` file in `/etc/yum.repos.d/`:
```bash
sudo nano /etc/yum.repos.d/custom.repo
```
Add the following content:
```ini
[custom-repo]
name=Custom Repository
baseurl=http://example.com/repo/
enabled=1
gpgcheck=1
```

### Diagram
Below is a simple diagram showing the relationship between package managers and repositories:

```
+-------------------+
|   Package Manager |
| (YUM, DNF, RPM)   |
+-------------------+
         |
         v
+-------------------+
|   Repositories    |
| (Online/Offline)  |
+-------------------+
         |
         v
+-------------------+
| Software Packages |
+-------------------+
```
```
```

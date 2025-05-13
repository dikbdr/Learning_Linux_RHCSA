# System Monitoring and Performance

## 1. Monitoring System Resources

### 1.1 `free` - Memory Usage

**Command:**  
```bash
free -h
```
- `-h`: Human-readable format.

**Sample Output:**
```
              total        used        free      shared  buff/cache   available
Mem:           7.7G        2.1G        3.2G        210M        2.4G        5.1G
Swap:          2.0G          0B        2.0G
```

**Diagram:**
```
+-------------------+
|   Memory Usage    |
+-------------------+
| Used   | 2.1G     |
| Free   | 3.2G     |
| Cache  | 2.4G     |
+-------------------+
```

---

### 1.2 `vmstat` - System Performance

**Command:**  
```bash
vmstat 2 5
```
- `2`: Interval (seconds)
- `5`: Number of reports

**Sample Output:**
```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 329600  12300 245000    0    0     1     2   10   20  2  1 97  0  0
```

---

### 1.3 `iostat` - CPU and Disk I/O

**Install:**
- **Ubuntu:** `sudo apt install sysstat`
- **CentOS:** `sudo yum install sysstat`

**Command:**  
```bash
iostat -xz 2 3
```
- `-x`: Extended stats
- `-z`: Suppress zero lines

**Sample Output:**
```
Device            r/s     w/s   rkB/s   wkB/s  %util
sda              0.50    1.00    5.00   10.00   1.00
```

---

## 2. Log Management

### 2.1 `journalctl` - Systemd Logs

**View all logs:**  
```bash
journalctl
```
**View logs for a service:**  
```bash
journalctl -u sshd
```
**Follow logs (like tail):**  
```bash
journalctl -f
```

---

### 2.2 `/var/log` Directory

- **Ubuntu/CentOS:** System logs are stored in `/var/log/`
- **Examples:**
  - `/var/log/messages` (CentOS)
  - `/var/log/syslog` (Ubuntu)
  - `/var/log/auth.log` (Ubuntu)

**View logs:**  
```bash
less /var/log/syslog      # Ubuntu
less /var/log/messages    # CentOS
```

---

## 3. Troubleshooting Common Issues

### 3.1 High CPU/Memory Usage

**Check top processes:**  
```bash
top
```
or  
```bash
htop   # Install with 'sudo apt/yum install htop'
```

### 3.2 Disk Space Issues

**Check disk usage:**  
```bash
df -h
```
**Check directory sizes:**  
```bash
du -sh /var/*
```

### 3.3 Service Failures

**Check service status:**  
```bash
systemctl status nginx
```
**View logs:**  
```bash
journalctl -u nginx
```

---

## Summary Table: Commands by Distribution

| Task                | Ubuntu Command                | CentOS Command                |
|---------------------|------------------------------|-------------------------------|
| Memory              | `free -h`                    | `free -h`                     |
| System Performance  | `vmstat`                     | `vmstat`                      |
| Disk I/O            | `iostat` (install sysstat)   | `iostat` (install sysstat)    |
| Logs                | `/var/log/syslog`            | `/var/log/messages`           |
| Systemd Logs        | `journalctl`                 | `journalctl`                  |
| Top Processes       | `top`, `htop`                | `top`, `htop`                 |

---

## Diagrams

**System Monitoring Overview:**

```
+-------------------+
|   System Health   |
+-------------------+
| CPU   | Memory    |
| Disk  | Network   |
| Logs  | Services  |
+-------------------+
```

---

**Tip:** Always check the man pages (`man <command>`) for more options and details.

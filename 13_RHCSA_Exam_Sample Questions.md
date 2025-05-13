# RHCSA Exam Sample Questions

Below are 50 sample questions for RHCSA exam preparation, each with explanations and solutions.

---

### 1. How do you display the current runlevel?
**Solution:**  
```bash
runlevel
```
**Explanation:**  
The `runlevel` command shows the previous and current runlevel.

---

### 2. How do you change the hostname to `server1` permanently?
**Solution:**  
```bash
hostnamectl set-hostname server1
```
**Explanation:**  
`hostnamectl` is used to set the system hostname.

---

### 3. How do you list all active services?
**Solution:**  
```bash
systemctl list-units --type=service --state=active
```
**Explanation:**  
Lists all active services managed by `systemd`.

---

### 4. How do you create a new user called `john`?
**Solution:**  
```bash
useradd john
```
**Explanation:**  
`useradd` creates a new user.

---

### 5. How do you set a password for user `john`?
**Solution:**  
```bash
passwd john
```
**Explanation:**  
`passwd` sets or changes a user's password.

---

### 6. How do you lock a user account?
**Solution:**  
```bash
passwd -l username
```
**Explanation:**  
The `-l` option locks the user account.

---

### 7. How do you unlock a user account?
**Solution:**  
```bash
passwd -u username
```
**Explanation:**  
The `-u` option unlocks the user account.

---

### 8. How do you create a group called `developers`?
**Solution:**  
```bash
groupadd developers
```
**Explanation:**  
`groupadd` creates a new group.

---

### 9. How do you add user `john` to group `developers`?
**Solution:**  
```bash
usermod -aG developers john
```
**Explanation:**  
`-aG` appends the user to the group.

---

### 10. How do you display all groups a user belongs to?
**Solution:**  
```bash
groups username
```
**Explanation:**  
Shows all groups for a user.

---

### 11. How do you create a 1GB file called `file.img`?
**Solution:**  
```bash
dd if=/dev/zero of=file.img bs=1M count=1024
```
**Explanation:**  
`dd` creates a file of specified size.

---

### 12. How do you mount an ISO file to `/mnt/iso`?
**Solution:**  
```bash
mount -o loop file.iso /mnt/iso
```
**Explanation:**  
Mounts ISO using loop device.

---

### 13. How do you display disk usage of `/home`?
**Solution:**  
```bash
du -sh /home
```
**Explanation:**  
`du -sh` shows summary in human-readable format.

---

### 14. How do you display free and used memory?
**Solution:**  
```bash
free -h
```
**Explanation:**  
`free -h` shows memory usage in human-readable format.

---

### 15. How do you display all block devices?
**Solution:**  
```bash
lsblk
```
**Explanation:**  
`lsblk` lists block devices.

---

### 16. How do you create a new partition on `/dev/sdb`?
**Solution:**  
```bash
fdisk /dev/sdb
```
**Explanation:**  
`fdisk` is used for partitioning disks.

---

### 17. How do you format `/dev/sdb1` with ext4?
**Solution:**  
```bash
mkfs.ext4 /dev/sdb1
```
**Explanation:**  
`mkfs.ext4` creates an ext4 filesystem.

---

### 18. How do you mount `/dev/sdb1` to `/mnt/data`?
**Solution:**  
```bash
mount /dev/sdb1 /mnt/data
```
**Explanation:**  
Mounts the partition to the directory.

---

### 19. How do you make the mount persistent after reboot?
**Solution:**  
Add to `/etc/fstab`:
```
/dev/sdb1  /mnt/data  ext4  defaults  0 0
```
**Explanation:**  
`/etc/fstab` is used for persistent mounts.

---

### 20. How do you display SELinux status?
**Solution:**  
```bash
sestatus
```
**Explanation:**  
`sestatus` shows SELinux status.

---

### 21. How do you set SELinux to permissive mode temporarily?
**Solution:**  
```bash
setenforce 0
```
**Explanation:**  
`setenforce 0` sets SELinux to permissive.

---

### 22. How do you set SELinux to enforcing mode?
**Solution:**  
```bash
setenforce 1
```
**Explanation:**  
`setenforce 1` sets SELinux to enforcing.

---

### 23. How do you change SELinux mode permanently?
**Solution:**  
Edit `/etc/selinux/config` and set:
```
SELINUX=enforcing
```
**Explanation:**  
This file controls SELinux mode at boot.

---

### 24. How do you list all SELinux contexts for files in `/var/www`?
**Solution:**  
```bash
ls -Z /var/www
```
**Explanation:**  
`-Z` shows SELinux context.

---

### 25. How do you change the SELinux context of a file?
**Solution:**  
```bash
chcon -t httpd_sys_content_t /var/www/html/index.html
```
**Explanation:**  
`chcon` changes SELinux context.

---

### 26. How do you restore default SELinux contexts?
**Solution:**  
```bash
restorecon -Rv /var/www
```
**Explanation:**  
`restorecon` restores default contexts.

---

### 27. How do you display firewall rules?
**Solution:**  
```bash
firewall-cmd --list-all
```
**Explanation:**  
Shows current firewall rules.

---

### 28. How do you open port 80 permanently in firewalld?
**Solution:**  
```bash
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload
```
**Explanation:**  
Adds and reloads firewall rules.

---

### 29. How do you check if a service is enabled at boot?
**Solution:**  
```bash
systemctl is-enabled servicename
```
**Explanation:**  
Checks if service starts at boot.

---

### 30. How do you enable a service at boot?
**Solution:**  
```bash
systemctl enable servicename
```
**Explanation:**  
Enables service at boot.

---

### 31. How do you disable a service at boot?
**Solution:**  
```bash
systemctl disable servicename
```
**Explanation:**  
Disables service at boot.

---

### 32. How do you start and stop a service?
**Solution:**  
```bash
systemctl start servicename
systemctl stop servicename
```
**Explanation:**  
Starts and stops a service.

---

### 33. How do you check the status of a service?
**Solution:**  
```bash
systemctl status servicename
```
**Explanation:**  
Shows service status.

---

### 34. How do you schedule a cron job to run every day at 2am?
**Solution:**  
Edit crontab:
```
0 2 * * * /path/to/command
```
**Explanation:**  
Cron syntax for daily at 2am.

---

### 35. How do you list all cron jobs for the current user?
**Solution:**  
```bash
crontab -l
```
**Explanation:**  
Lists user's cron jobs.

---

### 36. How do you add a new cron job?
**Solution:**  
```bash
crontab -e
```
**Explanation:**  
Edits user's crontab.

---

### 37. How do you display all running processes?
**Solution:**  
```bash
ps aux
```
**Explanation:**  
Shows all running processes.

---

### 38. How do you kill a process by PID?
**Solution:**  
```bash
kill PID
```
**Explanation:**  
Kills process with given PID.

---

### 39. How do you kill all processes by name?
**Solution:**  
```bash
pkill processname
```
**Explanation:**  
Kills all processes with the name.

---

### 40. How do you display the last 100 lines of a log file?
**Solution:**  
```bash
tail -n 100 /var/log/messages
```
**Explanation:**  
Shows last 100 lines.

---

### 41. How do you search for a string in a file?
**Solution:**  
```bash
grep "string" filename
```
**Explanation:**  
Searches for string in file.

---

### 42. How do you recursively search for a string in a directory?
**Solution:**  
```bash
grep -r "string" /path/to/dir
```
**Explanation:**  
Recursively searches for string.

---

### 43. How do you display the IP address of the system?
**Solution:**  
```bash
ip addr show
```
**Explanation:**  
Shows network interfaces and IPs.

---

### 44. How do you configure a static IP address?
**Solution:**  
Edit `/etc/sysconfig/network-scripts/ifcfg-eth0` and set:
```
BOOTPROTO=static
IPADDR=192.168.1.100
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
```
**Explanation:**  
Configures static IP.

---

### 45. How do you restart the network service?
**Solution:**  
```bash
systemctl restart network
```
**Explanation:**  
Restarts network service.

---

### 46. How do you display the routing table?
**Solution:**  
```bash
ip route
```
**Explanation:**  
Shows routing table.

---

### 47. How do you add a new route?
**Solution:**  
```bash
ip route add 192.168.2.0/24 via 192.168.1.1
```
**Explanation:**  
Adds a static route.

---

### 48. How do you check disk space usage?
**Solution:**  
```bash
df -h
```
**Explanation:**  
Shows disk usage in human-readable format.

---

### 49. How do you compress a file using gzip?
**Solution:**  
```bash
gzip filename
```
**Explanation:**  
Compresses file with gzip.

---

### 50. How do you extract a tar.gz archive?
**Solution:**  
```bash
tar -xzvf archive.tar.gz
```
**Explanation:**  
Extracts tar.gz archive.

---

**Tip:** Practice these commands and understand their options for the RHCSA exam.
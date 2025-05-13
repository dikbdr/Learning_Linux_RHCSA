# 10. Security and SELinux

## 1. Understanding Firewalls

### firewalld (CentOS/RHEL)

**Step 1:** Check firewalld status
```bash
sudo systemctl status firewalld
```

**Step 2:** Start/Enable firewalld
```bash
sudo systemctl start firewalld
sudo systemctl enable firewalld
```

**Step 3:** Allow HTTP service
```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

**Step 4:** List active rules
```bash
sudo firewall-cmd --list-all
```

![firewalld example](https://raw.githubusercontent.com/linuxtechi/screenshots/main/firewalld/firewalld-list-all.png)

---

### iptables (Ubuntu)

**Step 1:** Check iptables rules
```bash
sudo iptables -L
```

**Step 2:** Allow SSH (port 22)
```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

**Step 3:** Save rules
```bash
sudo iptables-save | sudo tee /etc/iptables/rules.v4
```

![iptables example](https://assets.digitalocean.com/articles/iptables/iptables-list.png)

---

## 2. Configuring SELinux (CentOS/RHEL)

**Step 1:** Check SELinux status
```bash
sestatus
```

**Step 2:** Change SELinux mode (edit `/etc/selinux/config`)
```bash
sudo vi /etc/selinux/config
# Set SELINUX=enforcing or SELINUX=permissive or SELINUX=disabled
```

**Step 3:** Apply changes (reboot required for mode change)
```bash
sudo reboot
```

**Step 4:** Manage SELinux booleans
```bash
sudo getsebool -a
sudo setsebool httpd_can_network_connect on
```

![SELinux status](https://access.redhat.com/sites/default/files/attachments/selinux-status.png)

> **Note:** Ubuntu uses AppArmor instead of SELinux.

---

## 3. Managing SSH Security

**Step 1:** Edit SSH config
```bash
sudo vi /etc/ssh/sshd_config
# Example: Change default port
Port 2222
# Disable root login
PermitRootLogin no
```

**Step 2:** Restart SSH service
```bash
sudo systemctl restart sshd    # CentOS/RHEL
sudo systemctl restart ssh     # Ubuntu
```

**Step 3:** Use SSH key authentication
```bash
ssh-keygen
ssh-copy-id user@server
```

![SSH config example](https://www.cyberciti.biz/media/new/faq/2017/10/ssh-sshd_config-file.png)

---

## 4. User Authentication and Password Policies

### Ubuntu & CentOS

**Step 1:** Set password aging policies
```bash
sudo chage -l username
sudo chage -M 90 -m 7 -W 14 username
```

**Step 2:** Enforce password complexity (edit `/etc/login.defs`)
```bash
sudo vi /etc/login.defs
# Example: Set PASS_MIN_LEN 8
```

**Step 3:** Use PAM for advanced policies (edit `/etc/pam.d/common-password` or `/etc/pam.d/system-auth`)
```bash
# Example for Ubuntu (common-password)
password requisite pam_pwquality.so retry=3 minlen=8
```

![Password policy example](https://www.tecmint.com/wp-content/uploads/2017/09/Set-Password-Expiry-in-Linux.png)

---

## Summary Table

| Feature         | Ubuntu (AppArmor) | CentOS (SELinux) |
|-----------------|-------------------|------------------|
| Firewall        | iptables/ufw      | firewalld        |
| SELinux/AppArmor| AppArmor          | SELinux          |
| SSH Config      | /etc/ssh/sshd_config | /etc/ssh/sshd_config |
| Password Policy | PAM, login.defs   | PAM, login.defs  |

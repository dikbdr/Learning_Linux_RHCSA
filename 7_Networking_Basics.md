
## Networking Basics

### Understanding IP Addressing and Subnetting

1.  **IP Addressing**:

    *   An IP address is a unique identifier for a device on a network.
    *   IPv4 Example: `192.168.1.1`
    *   IPv6 Example: `2001:db8:85a3::8a2e:370:7334`

2.  **Subnetting**:

    *   Divides a network into smaller sub-networks, improving efficiency and security.
    *   Example: `192.168.1.0/24` (Subnet mask: 255.255.255.0)

    *   **Calculating Subnets**:
        *   Use tools like `ipcalc`.
        *   Ubuntu: `sudo apt install ipcalc`
        *   CentOS: `sudo yum install ipcalc`
        *   Example Usage: `ipcalc 192.168.1.0/24`

    *   **Diagram**:

        ```
        [Network: 192.168.1.0/24]
        |-- [Subnet 1: 192.168.1.0/25] (192.168.1.0 - 192.168.1.127)
        |   |-- Hosts: 192.168.1.1 - 192.168.1.126
        |-- [Subnet 2: 192.168.1.128/25] (192.168.1.128 - 192.168.1.255)
        |   |-- Hosts: 192.168.1.129 - 192.168.1.254
        ```

---

### Configuring Network Interfaces

1.  **Ubuntu (Netplan)**:

    *   Netplan uses YAML configuration files.
    *   Edit `/etc/netplan/*.yaml` (filename may vary).
    *   Example:

        ```yaml
        network:
          version: 2
          renderer: networkd
          ethernets:
            eth0:
              dhcp4: no
              addresses: [192.168.1.100/24]
              gateway4: 192.168.1.1
              nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
        ```

    *   Apply changes: `sudo netplan apply`

2.  **CentOS (ifcfg)**:

    *   Configuration files are in `/etc/sysconfig/network-scripts/`.
    *   Edit `ifcfg-eth0` (or appropriate interface name).
    *   Example:

        ```
        TYPE=Ethernet
        NAME=eth0
        DEVICE=eth0
        ONBOOT=yes
        BOOTPROTO=none
        IPADDR=192.168.1.100
        NETMASK=255.255.255.0
        GATEWAY=192.168.1.1
        DNS1=8.8.8.8
        DNS2=8.8.4.4
        ```

    *   Restart network: `sudo systemctl restart network`

---

### Basic Networking Commands

1.  **Ping**:

    *   Tests network connectivity.
    *   Syntax: `ping [options] destination`
    *   Example: `ping google.com`

2.  **Netstat (Deprecated, use `ss`)**:

    *   Displays network connections, routing tables, interface statistics.
    *   Syntax: `netstat [options]`
    *   Example: `netstat -tuln` (shows listening TCP and UDP ports)

3.  **SS**:

    *   `ss` is a modern replacement for `netstat`.
    *   Syntax: `ss [options]`
    *   Example: `ss -tuln` (shows listening TCP and UDP ports)

4.  **Traceroute**:

    *   Traces the route packets take to a destination.
    *   Syntax: `traceroute [options] destination`
    *   Example: `traceroute google.com`

5.  **IP**:

    *   A powerful tool for displaying and manipulating network interfaces, routing, and tunnels.
    *   Syntax: `ip [OPTIONS] OBJECT {COMMAND | help}`
    *   Examples:
        *   `ip addr show`: Show IP addresses.
        *   `ip route show`: Show routing table.
        *   `ip link set eth0 up`: Enable interface eth0.

---

### SSH and Remote Access

1.  **SSH**:

    *   Securely connects to a remote system.
    *   Syntax: `ssh [user@]hostname`
    *   Example: `ssh user@192.168.1.100`

2.  **Generate SSH Key**:

    *   Creates a public/private key pair for passwordless login.
    *   Command: `ssh-keygen -t rsa -b 2048`

3.  **Copy SSH Key to Remote Host**:

    *   Copies the public key to the remote host's `authorized_keys` file.
    *   Command: `ssh-copy-id user@192.168.1.100`

---

### Additional Networking Commands

1.  **Curl**:

    *   Transfers data from or to a server.
    *   Example: `curl http://example.com` (fetches the content of the webpage)

2.  **Wget**:

    *   Downloads files from the web.
    *   Example: `wget http://example.com/file.zip`

3.  **Dig**:

    *   Queries DNS name servers for information about host addresses, mail exchanges, etc.
    *   Example: `dig google.com`

4.  **Nslookup**:

    *   Queries DNS servers to find IP addresses or perform reverse DNS lookups.
    *   Example: `nslookup google.com`

---

### Network Troubleshooting

1.  **Ubuntu**:

    *   Check interface status: `ip addr`
    *   Restart Network Manager: `sudo systemctl restart NetworkManager`

2.  **CentOS**:

    *   Check interface status: `nmcli dev status`
    *   Restart network: `sudo systemctl restart network`

---

### Assigning Private IP

1.  **Ubuntu (Netplan)**:

    *   Modify the `/etc/netplan/*.yaml` file as shown in the "Configuring Network Interfaces" section.  Ensure the `dhcp4` is set to `no` and provide static IP details.

2.  **CentOS (ifcfg)**:

    *   Modify the `ifcfg-eth0` file (or the relevant interface file) as shown in the "Configuring Network Interfaces" section.  Ensure `BOOTPROTO` is set to `none` and provide static IP details.

---

### Advanced Networking Commands

1.  **Tcpdump**:

    *   A powerful packet analyzer; captures network traffic.
    *   Example: `sudo tcpdump -i eth0 -n -s 0 port 80` (captures HTTP traffic on interface eth0)

2.  **Iptables (Legacy, consider using nftables)**:

    *   A user-space application program that allows you to configure the Linux kernel firewall.
    *   Example: `sudo iptables -L` (lists current firewall rules)

3.  **Nftables**:

    *   The modern replacement for iptables.  Provides a more efficient and flexible firewall framework.
    *   Example: `sudo nft list ruleset` (lists current firewall rules)

4.  **Iperf/Iperf3**:

    *   A tool for measuring network bandwidth performance.
    *   Server: `iperf3 -s`
    *   Client: `iperf3 -c <server_ip>`

5.  **MTR (My Traceroute)**:

    *   Combines `ping` and `traceroute` to provide a dynamic network diagnostic tool.
    *   Example: `mtr google.com`
```

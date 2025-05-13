## Storage Management

### 1. Understanding Partitions and File Systems

**Partitions** divide a physical disk into isolated sections, each functioning as an independent disk. **File systems** (e.g., ext4, xfs, btrfs, vfat) define how data is organized and managed on these partitions.

**Key Concepts:**
- **MBR vs GPT:** MBR (Master Boot Record) supports up to 2TB disks and 4 primary partitions. GPT (GUID Partition Table) supports larger disks and more partitions.
- **Types of partitions:** Primary, extended, and logical.

**Useful Commands:**
```bash
lsblk -f                # Show block devices with file system info
blkid                   # Display block device attributes
parted /dev/sda print   # Show partition table (supports GPT)
fdisk -l /dev/sda       # List partitions (MBR/GPT)
```

**Diagram:**
```
+-------------------------------+
|         Physical Disk         |
+-------------------------------+
| /dev/sda1 | /dev/sda2 | ...   |
+-----------+-----------+-------+
|  ext4     |   xfs     | ...   |
+-------------------------------+
```

---

### 2. Mounting and Unmounting File Systems

**Mounting** attaches a file system to a directory tree. **Unmounting** detaches it.

**Advanced Concepts:**
- **/etc/fstab:** Persistent mount configuration.
- **Mount options:** (e.g., `noatime`, `ro`, `defaults`)
- **Bind mounts:** Mount a directory to another location.

**Commands:**
```bash
mount /dev/sda1 /mnt
umount /mnt

mount -o ro /dev/sda2 /mnt/read_only      # Mount as read-only
mount --bind /data /mnt/data              # Bind mount

cat /etc/mtab                             # Show currently mounted filesystems
cat /proc/mounts                          # Kernel mount info
```

**/etc/fstab Example:**
```
UUID=xxxx-xxxx   /data   xfs   defaults   0 2
```

---

### 3. Disk Management Commands

- `fdisk`, `parted`, `gdisk`: Partitioning tools (MBR/GPT).
- `lsblk`, `blkid`: List block devices and attributes.
- `df`, `du`: Disk usage.
- `findmnt`: Show mount points.
- `tune2fs`, `xfs_admin`: Tune/ext info.
- `resize2fs`, `xfs_growfs`: Resize file systems.
- `mkfs.*`: Create file systems.

**Examples:**
```bash
fdisk /dev/sdb                   # Interactive partitioning (MBR)
parted /dev/sdb                  # Interactive partitioning (GPT)
mkfs.ext4 /dev/sdb1              # Create ext4 filesystem
mkfs.xfs /dev/sdb2               # Create xfs filesystem

tune2fs -l /dev/sda1             # Show ext2/3/4 superblock info
xfs_admin -l /dev/sda2           # Show xfs label info

resize2fs /dev/sda1 20G          # Resize ext4 filesystem
xfs_growfs /mnt                  # Grow mounted xfs filesystem

findmnt                          # List all mount points
lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT
```

---

### 4. Logical Volume Management (LVM)

LVM abstracts physical storage, allowing flexible allocation and resizing.

**Key Concepts:**
- **Physical Volume (PV):** Disk or partition initialized for LVM.
- **Volume Group (VG):** Pool of PVs.
- **Logical Volume (LV):** Resizable "virtual partition" from VG.

**Advanced Features:**
- **Snapshots:** Point-in-time copies of LVs.
- **Thin provisioning:** Allocate space on demand.
- **LV resizing:** Online and offline.

**Diagram:**
```
+-------------------+
| Physical Volumes  |
| /dev/sdb1, sdc1   |
+---------+---------+
          |
     Volume Group (VG)
          |
   +------+------+------+
   |      |      |      |
  LV1    LV2   Snap   Thin
```

**Commands:**
```bash
pvcreate /dev/sdb1 /dev/sdc1
vgcreate vg0 /dev/sdb1 /dev/sdc1
lvcreate -L 10G -n lv_home vg0
lvcreate -l 100%FREE -n lv_data vg0
lvextend -L +5G /dev/vg0/lv_home
lvresize -r -L 15G /dev/vg0/lv_home    # Resize and resize FS
lvcreate -s -n lv_home_snap -L 1G /dev/vg0/lv_home   # Snapshot

mkfs.ext4 /dev/vg0/lv_home
mount /dev/vg0/lv_home /mnt
```

---

### 5. Advanced Storage Management Topics

#### a. RAID (Redundant Array of Independent Disks)
- **Software RAID:** Managed by `mdadm`.
- **Levels:** RAID 0 (striping), RAID 1 (mirroring), RAID 5/6 (parity).

**Example:**
```bash
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
cat /proc/mdstat
```

#### b. Filesystem Checking and Repair
- `fsck`, `e2fsck`, `xfs_repair`: Check and repair filesystems.

**Example:**
```bash
fsck /dev/sda1
xfs_repair /dev/sda2
```

#### c. Quotas
- Manage user/group disk usage.

**Example:**
```bash
edquota -u username
quotaon /home
repquota -a
```

#### d. Encryption
- **LUKS/dm-crypt:** Encrypt block devices.

**Example:**
```bash
cryptsetup luksFormat /dev/sdb1
cryptsetup luksOpen /dev/sdb1 secure_disk
mkfs.ext4 /dev/mapper/secure_disk
```

---

### 6. Useful Tips

- Always backup data before modifying partitions or filesystems.
- Use `lsblk`, `blkid`, and `findmnt` for quick storage overview.
- Monitor disk health with `smartctl` (from `smartmontools`).

**Example:**
```bash
smartctl -a /dev/sda
```
---
title: "TW 32 bit  has disappeared from own grub menu"
date: 2024-02-14
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-02-14
It happened after ```
zypper dup && reboot
``` Tuesday. Only Memtest remains in TW grub menu.

Multiboot with Debian 12.

/boot is on separate partition because Debian's grub can't access btrfs.

```
# cat /etc/fstab
UUID=SDA6_UUID  /                    btrfs  defaults                      0  0
UUID=SDA6_UUID  /var                 btrfs  subvol=/@/var                 0  0
UUID=SDA6_UUID  /usr/local           btrfs  subvol=/@/usr/local           0  0
UUID=SDA6_UUID  /tmp                 btrfs  subvol=/@/tmp                 0  0
UUID=SDA6_UUID  /srv                 btrfs  subvol=/@/srv                 0  0
UUID=SDA6_UUID  /root                btrfs  subvol=/@/root                0  0
UUID=SDA6_UUID  /opt                 btrfs  subvol=/@/opt                 0  0
UUID=SDA6_UUID  /home                btrfs  subvol=/@/home                0  0
UUID=SDA7_UUID  /boot/grub2  ext4   defaults  0  0
UUID=SDA6_UUID  /.snapshots          btrfs  subvol=/@/.snapshots          0  0
```

```
# mount | egrep -v "cgroup|rpc|tmpfs|^sys|on /dev|on /proc|on /sys|on /var" | sort 
/dev/sda6 on /home type btrfs (rw,relatime,space_cache,subvolid=264,subvol=/@/home)
/dev/sda6 on /opt type btrfs (rw,relatime,space_cache,subvolid=263,subvol=/@/opt)
/dev/sda6 on /root type btrfs (rw,relatime,space_cache,subvolid=262,subvol=/@/root)
/dev/sda6 on /.snapshots type btrfs (rw,relatime,space_cache,subvolid=266,subvol=/@/.snapshots)
/dev/sda6 on /srv type btrfs (rw,relatime,space_cache,subvolid=261,subvol=/@/srv)
/dev/sda6 on /tmp type btrfs (rw,relatime,space_cache,subvolid=260,subvol=/@/tmp)
/dev/sda6 on / type btrfs (rw,relatime,space_cache,subvolid=267,subvol=/@/.snapshots/1/snapshot)
/dev/sda6 on /usr/local type btrfs (rw,relatime,space_cache,subvolid=259,subvol=/@/usr/local)
/dev/sda7 on /boot/grub2 type ext4 (rw,relatime)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=100)
```

I've tried from TW grub command line:
```

set root=(hd0,6)
linux (hd0,7)/boot/vmlinuz-6.5.4-1-pae root=/dev/sda6
initrd (hd0,7)/boot/initrd-6.5.4-1-pae 
boot

```

but 
```

You are in emergency mode. After logging in, type "journalctl -xb" to view system logs, "systemctl reboot" to reboot, or "exit" to continue bootup.
Give root password for maintenance
(or press Control-D to continue)
Reloading system manager configuration.
Starting default.target.
You are in emergency mode. After logging in, type "journalctl -xb" to  view system logs, "systemctl reboot" to reboot, or "exit" to continue  bootup.
Give root password for maintenance
(or press Control-D to continue)

```

```
journalctl -xb
mount: /boot/grub2: unknown filesystem type 'ext4'.
...
boot-grub2.mount: Failed with result 'exit-code'.
Failed to mount /boot/grub2.


```

Any idea please ?

---

### Post by maketopsite on 2024-04-01
Solved after booting TW iso, chrooting and
```
zypper in kernel-pae
```

---


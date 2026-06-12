---
title: "libdl.so.2 ELf wrong header"
date: 2009-06-09
forum: x86 64-bit Users
---

### Post by drahko on 2009-06-09
i get a can not load libdl.so.2 ELf wrong header when i try to boot up 9.04 
 
would anyone beable to help me out here i was trying to duel boot it with vista and now i get this error if some one can just help me get it working again been nice i gota alota info i need to save on it

---

### Post by drahko on 2009-06-11
anyone?

---

### Post by ethoxyethaan on 2009-06-11
if possible try to boot with a live cd, mount your Ubuntu root partition on /ubuntu/

then type this:

file /ubuntu/lib/libdl-2.9.so
file /ubuntu/lib/libdl.so.2

it should display this:

nick@Debian:~$ file /lib/libdl-2.9.so
/lib/libdl-2.9.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
nick@Debian:~$ file /lib/libdl.so.2 
/lib/libdl.so.2: symbolic link to `libdl-2.9.so'
nick@Debian:~$ 

If NOT the file is missing or possibly corrupt.

---

### Post by drahko on 2009-06-11
ubuntu@ubuntu:~$ file /ubuntu/lib/libdl-2.9.so
/ubuntu/lib/libdl-2.9.so: ERROR: cannot open `/ubuntu/lib/libdl-2.9.so' (No such file or directory)
ubuntu@ubuntu:~$ file /ubuntu/lib/libdl.so.2
/ubuntu/lib/libdl.so.2: ERROR: cannot open `/ubuntu/lib/libdl.so.2' (No such file or directory)
ubuntu@ubuntu:~$ sudo apt-get install freedom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freedom
ubuntu@ubuntu:~$

---

### Post by drahko on 2009-06-11
howdo i mount it /ubuntu/ ? ? ?

---

### Post by Yellow Pasque on 2009-06-11
These files are part of the libc6 package. If you can boot to recovery mode, and drop to the root terminal (with networking):
```
sudo apt-get --reinstall install libc6
```

---

### Post by drahko on 2009-06-11
idk how to boot in recovery just pops up and stat that and mail loop terminated

---

### Post by Yellow Pasque on 2009-06-11
What? [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by ethoxyethaan on 2009-06-11
**drahko**, ofcaurse the file is not found if you did not Mount the partition in /ubuntu/ ...
, you should never execute bash commands without knowing what your doing.


sudo fdisk -l
(find the right linux partition)

my case: /dev/sda1

sudo mkdir /ubuntu/
sudo mount /dev/sda1 /ubuntu/

Then check if the files are installed...


if you can't get in recovery mode try this:

Boot from live CD,
open terminal:


sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdaX /mnt/root

NOTE: /dev/sdaX is the partition you have ubuntu installed on find it with sudo fdisk -l

sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo apt-get --reinstall install libc6

---

### Post by drahko on 2009-06-11
ok thanks and what if i deleted the linux swap on acident

---

### Post by drahko on 2009-06-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08bb771d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       12584   101072947+  83  Linux
/dev/sda2           12585       19458    55215104    7  HPFS/NTFS
/dev/sda3           19459       29219    78405232+   7  HPFS/NTFS
/dev/sda4           29220       30401     9494415   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /ubuntu/
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /ubuntu/
ubuntu@ubuntu:~$ file /ubuntu/lib/libdl-2.9.so
/ubuntu/lib/libdl-2.9.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), for GNU/Linux 2.6.15, dynamically linked (uses shared libs), stripped
ubuntu@ubuntu:~$ file /ubuntu/lib/libdl.so.2
/ubuntu/lib/libdl.so.2: symbolic link to `libdl-2.9.so'
ubuntu@ubuntu:~$

---

### Post by drahko on 2009-06-11
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
/bin/bash: error while loading shared libraries: libdl.so.2: wrong ELF class: ELFCLASS64

---

### Post by drahko on 2009-06-13
bump

---


---
title: "grub1.5 error 17"
date: 2008-06-15
forum: x86 64-bit Users
---

### Post by jon64 on 2008-06-15
This is my situation, every time i boot up my linux machine it halts at the grub bootloader. I receive an error 17 right after the "GRUB Loading stage1.5."

Before this happened i was dual booting with Windows server 2003 and ubuntu and it was working fine. Then i wanted to try out Kubuntu to see how it was like and right after i rebooted the computer i received the error 17 message. 

So after i received the message i ran the live cd and typed sfdisk -l and this is wat came up:
root@ubuntu:/home/ubuntu# sfdisk -l

Disk /dev/sda: 91201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  89698   89699- 720507186   83  Linux
/dev/sda2      89699   91200    1502   12064815    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      89699+  91200    1502-  12064783+  82  Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  38911   38912- 312560608+   7  HPFS/NTFS
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty


I can still get to my Windows Server 2003 OS but i want to get my ubuntu OS back or at least get files that i need from the ubuntu hard disk from my Windows Server 2003 hard disk.

I just tried using the Live CD to run "sudo grub" and "find /boot/grub/stage1" and when i typed in find /boot/grub/stage1 i received "Error 15: File not found"

I don't know what to try anymore =/ please help!

---

### Post by logos34 on 2008-06-15
[Double Post]

---

### Post by Sef on 2008-06-15
Locked. [Double Post]("http://ubuntuforums.org/showthread.php?t=830362").  Please note that double posting can get one an infraction.  In the future, please do not double post.  Thank you.

---


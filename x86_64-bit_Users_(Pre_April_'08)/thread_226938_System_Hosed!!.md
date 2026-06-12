---
title: "System Hosed??!!"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by sadhaka on 2006-07-31
I've been using Dapper Drake 6.06 for Amd64 for a while now, and after some weeks of tweaking have been well-satisfied with it. This morning, though, when I turned on the HP Pavilion a1230n Ubuntu is installed on, the boot-up failed with the current kernel, 2.6.15-26-amd64-generic, and with ALL of the back-up kernels I have. The messages go by too fast for me to read, and there appears to be no dmesg or log file to refer to, so all I'm left with is this tail-end of diagnostics:

mount: Mounting /dev/sda3 on /root failed: no such device
begin: Running /scripts/local-bottom...
Done.
Done.
begin: Running /scripts/init-bottom...
mount: Mounting /sys on /root/sys failed: no such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01(Debian1:1.01-4ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job control turned off

<and then a couple of lines of some normal-seeming junk about USB devices...>

Then abruptly there's just a # command prompt, and I have access to about 60 commands, many of which I've never heard of or don't know how to use.

I tried using the Ubuntu Live CD, and got that to work after some fussing. Fdisk and fsck suggest that my SATA drive, where / and /boot etc. reside, seems to be ok, but when I tell fdisk to look at the PATA drive, where /home lives, or used to live, it doesn't see any partition at all. All of this hardware, by the way, is pretty new.

I am completely stumped. The grub setup looks ok, so I have no idea what to do next. If anyone can see a way to avoid starting from scratch again, I would appreciate the help. I'm wondering if some malware has erased my PATA drive, or something like that... Is that possible? Oh, lordy...

---

### Post by juicemansam on 2006-08-01
Well, since I didn't catch the '/root' part before typing, I'd just boot up with a live-cd, and check /etc/fstab (see below as well). But I'll leave what I've typed:

I'd start by checking the cables, then the BIOS, then boot up to a live-cd. In the live CD, I'd fdisk -l all the hard drives, and check that all partitions that are supposed to be there, are. Then I'd mount each partition, checking that everything is intact and the way it should be. Next I'd check /etc/fstab file and the /boot/grub/menu.lst (where ever they may be) for consistency with regards to drive/parition calling (taking into consideration naming styles). I'd pay special attention to /etc/fstab in your case, since you posted '/root' as the root directory, which is an incorrect location for sys and proc.

---

### Post by sadhaka on 2006-08-01
Thank you for the tips, which I will try now. BTW, is there any way to catch the boot-up messages before they scroll up off the screen, given that the boot sequence won't complete?

>< Denis

---


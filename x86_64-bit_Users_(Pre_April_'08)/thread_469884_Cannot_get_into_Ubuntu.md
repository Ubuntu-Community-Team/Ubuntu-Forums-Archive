---
title: "Cannot get into Ubuntu"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by orthodoc on 2007-06-10
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/7957](https://answers.launchpad.net/ubuntu/+question/7957) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Everything was going on fine until last night. When i attempted to switch on the PC in the morning it would not start. It did kick off, the Grub options showed up and i chose ubuntu, then the ubuntu splash screen showed up. After loading up the screen flashed for a while and then goes black with a twirling icon showing that its busy. Nothing comes up however long I let it stay. The max I have let it stay like this is about 45 min. So I thought maybe its to do with the xserver problem, maybe because i have proprietary drivers installed for nvidia. i did a quick reconfigure and reboot, but the problem persisted. This time however the Nvidia splash came up so it was not the graphics issue.
Somewhere along in the ubuntu forums i came across the file check suggestion and i did a file check on all the Linux partitions. All of them came clean except the swap drive. How do I correct the swap partition without loosing any data?

when i run the list command:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot Start End Blocks Id System
/dev/sda1 * 63 29990897 14995417+ 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 29990960 398283479 184146260 5 Extended
/dev/sda5 29990961 225022454 97515747 7 HPFS/NTFS
/dev/sda6 225022518 229215419 2096451 82 Linux swap / Solaris
/dev/sda7 229215483 260670689 15727603+ 83 Linux
/dev/sda8 260670753 365526944 52428096 83 Linux
/dev/sda9 365527008 398283479 16378236 83 Linux

And,
ubuntu@ubuntu:~$ sudo fsck -p /dev/sda6
fsck 1.39 (29-May-2006)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6

By this time you will understand that the file system is different and not ext2 or ext3. I think this is because I had used Automatix to recognize the NTFS partitions. Maybe they messed it up. I don't know for sure. By the way I have win xp on sda1 and a windows partition on sda5.

But I want my ubuntu back. How do I solve this problem??

I am using ubuntu feisty fawn the x86_64 version on a pc set to dual boot with win xp using GRUB. The other kernel images would not help me boot as well.

---

### Post by steveneddy on 2007-06-10
I assume that you udated the kernel this weekend?

Why don't you try booting onto a previous kernel from Grub?

---

### Post by orthodoc on 2007-06-10
> **steveneddy said:**
> I assume that you udated the kernel this weekend?

Why don't you try booting onto a previous kernel from Grub?

You are right! I must have updated into the new kernel. I remember having done that. I did choose the previous kernel image from the grub menu. but it does not help. The only thing I can do is log into the recovery mode, which, of course is command line and I am afraid that is not my cup of tea. At the moment I am using the live cd mode to access the net.

What else could I do??

---

### Post by orthodoc on 2007-06-11
Just bumping the thread.

Someone please help! I don't want to really do a reinstall.

---


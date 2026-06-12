---
title: "EXT4-fs: group descriptors corrupted: Need to FSCK but cannot."
date: 2009-07-01
forum: x86 64-bit Users
---

### Post by enyboricua on 2009-07-01
Hello,
 
I really hope someone can help me out with this!  I have been searching for hours but cannot find much information about this.  I have the latest release (Jaunty 64-bit).  I had a completely working system with no problems for weeks when I had a power outage. The system is currently booting me into 'initramfs" which I am completely lost in.  Anyway I suspect it is because I am getting the following error "EXT4-fs: group descriptors corrupted:"  From what I have read I shoud be able to run "fsck" and this could probably fix it.  However, as I'm sure you all know this utility does not exist in initramfs.  I have tried everything I know to try and boot into single user mode to no avail.  I even tried to use the install cd with "recover a broken system" but when I get to the open a shell prompt itg says "no shell found in /target"  It feels this should be easy to fix but since I am a newb I am lost!   Please advise..
 
J

---

### Post by jocko on 2009-07-02
Boot from a live cd and run fsck.
I think the command:
```
sudo fsck -fpC 0 /dev/[COLOR=Red]sda1[/COLOR]
```
should do it (substitute [COLOR=Red]sda1[/COLOR] in the command for the partition you have trouble with).

---

### Post by enyboricua on 2009-07-02
Thanks for the response.

I made a live cd and successfully booted into ubuntu.  I tried the command above but it seems to assume it is for a reiserfs filesystem.  I tried to run "fsck.ext4 -fpc /dev/sda1" but it responds with:

fsck.ext4: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

any ideas?

---

### Post by enyboricua on 2009-07-02
Actually,  it worked!  I realized I was trying to fsck the wrong partition!  Thanks so much!!!

---


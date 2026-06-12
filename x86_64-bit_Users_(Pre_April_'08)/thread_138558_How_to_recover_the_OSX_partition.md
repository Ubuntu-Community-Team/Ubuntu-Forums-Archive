---
title: "How to recover the OSX partition?"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by alegomes on 2006-03-02
Hi all!

After a forced shutdown, my MacOS X filesystem (HFS or HFS+? I don't know) corrupted. I've already tried the Apple Disk Utility application, but with no success (see my post at Apple forum below). Is there any way to restore/read my data from Ubuntu? I've already tried to mount OSX partiton, but I got:

```
ubuntu@ubuntu:~$ sudo mount -t **hfsplus** /dev/hda3 /mnt
mount: Not a directory

ubuntu@ubuntu:~$ sudo mount -t **hfs** /dev/hda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Peopel asked me to use Prosoft Data Rescue [1] and Alsoft Disk Warrior [2] to backup the OSX data and recovery the damaged partition, respectively, but I'd rather using free software. Do you know any?  

[1] [http://www.prosofteng.com/](http://www.prosofteng.com/)
[2] [http://www.alsoft.com/](http://www.alsoft.com/)

thanks!!!!!
Ale!

> **Message posted at Apple Forums**
[http://discussions.apple.com/thread.jspa?threadID=382310&tstart=0](http://discussions.apple.com/thread.jspa?threadID=382310&tstart=0)

I was playing with Netbeans and when debugging a plugin I was programming, things got frozen. So, I shutted the computer down and, when restarting, I got a question icon bliking inside a folder icon on the screen, in the boot time. Then, I restarted again the computer and it didn't came up anymore.

Now, if I try to boot from the hard drive, not even the
Apple's logo is show. At its place, it's showed a "cut circle".

Disk utility can't verify or repair the hard disk. It shows the message "Verify and Repair disk 'disk0s3'. Checking HFS Plus volume. Catalog file entry not found for extent. Vloume chech failed. Error: The underlying task reported failure on exit. 1 HFS volume checked. 1 volume ould no be repaired because of an error."

If I try to reinstall the OS, the installer doesn't show me any option at "Select Destination" phase.

Is it a phisical problem or there's some to solve that with software?

Thank you all.
Alexandre Gomes 

---

### Post by linear on 2006-03-02
In order to try anything, you need to first create a mount point:
[LEFT]```
sudo mkdir /media/mac
```[/LEFT]
Once that's done, you can try mounting the volume:
```
sudo mount -t hfsplus -o "ro" /dev/hda3 /media/mac
```
Chances of recovery? Don't know. :(

---

### Post by ssam on 2006-03-02
i think you'd do much better with one of the non free mac os x utilities. the linux world does not use hfs much and so i dont think the tools are great. if you want your data back then you will probably have to buy software.

the one thing you might want to do from linux is to use dd to create an exact image of the partition. you'll need as much free disk space as the paretitions size. maybe its a good time to buy a big firewire disk, which you can use for back up. i have a lacie 80gig and 300gig and they work great in macosx and ubuntu.

ps: it would be great if someone could tell me that i am wrong and that fsck is a master of hfs recovery, but i doubt it.

---

### Post by alegomes on 2006-03-02
Yes, the mount point is there....

```

ubuntu@ubuntu:~$ ls /media/
osx
ubuntu@ubuntu:~$ sudo mount -t hfsplus -o "ro" /dev/hda3 /media/osx/
mount: Not a directory
ubuntu@ubuntu:~$
```

---

### Post by jdp on 2006-03-03
You may not have to specify the filesystem type. Try: **sudo mount -o "ro" /dev/hda3 /media/osx/**

---

### Post by astx813 on 2008-03-19
> **alegomes said:**
> I've already tried to mount OSX partiton, but I got:

```
ubuntu@ubuntu:~$ sudo mount -t **hfsplus** /dev/hda3 /mnt
mount: Not a directory

```

Did you have any luck getting past this?  I'm running into the same problem myself.

---


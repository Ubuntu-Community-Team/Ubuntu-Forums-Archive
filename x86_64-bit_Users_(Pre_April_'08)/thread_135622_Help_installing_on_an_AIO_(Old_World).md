---
title: "Help installing on an AIO (Old World)"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by smileyme on 2006-02-24
I am new to linux, but have mananged to install on a PC. I like linux, but prefer Mac hardware over PC. I have an old AIO doing nothing, and thought it would be cool to have linux on it. I have a lot of hardware I can use to upgrade it, and would like to hack the video. 

First, I would like to figure out how to install linux. I have been trying for about a week, and have worked through some issues. I read through many posts, and have followed "zcat's howto". However, I am stuck at the reboot stage. I have some screen problems and can't read everything, so I will type a "?" where unsure.  I'm not going to type in the entire boot message, but this is how it ends:

> [.251.6371971] device-mapper: 4.4.0-i?ctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
    No volume groups found
/scripts/local-top/evms: /sbin/evms_activate:not found
Done.
ALERT! does not exist. Dropping to a shell!

BusyBox v1.00-pre10 (Debian-20040623-ubuntu22) built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't addess tty; job control turned off


I mistakenly placed my first post in the kubuntu PPC forum, but have worked though that issue.

[http://ubuntuforums.org/showthread.php?t=134606]("http://ubuntuforums.org/showthread.php?t=134606")

I really would like to see this thing work

Rick :)

---

### Post by jdp on 2006-02-24
The AIO G3 is the Beige G3 in a different case.  The mobos are identical.
[http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)

---

### Post by smileyme on 2006-02-25
Well I've tried every angle, and no joy.

Although, I'm beginning to understand what some of the command lines actually mean. Good leaning experience. I guess there are quite a few different ways to get to the same end, and both sets of directions I have followed show this. In some instances, I can see how one command accomplishes the same thing as another.

Following these last directions, I get to the point of switching terminals. "mkdir /target/mnt/hfs" seems to work fine, but "mount /dev/sda6 hfs -t hfs #" fails to mount.

I was trying this time on a SCSI drive, but will try again on the ATA drive.

Does it matter what the OS 9 partition is named?

Rick :)

---

### Post by jdp on 2006-02-26
You have a small misunderstanding on what is put in for the actual command.  Generally **#** signals the start of a comment, and doesn't need to be included.  So, the command you should use is:
**mount /dev/sda6 /target/mnt/hfs -t hfs**

I had some mistakes in my initial post.  Read the entire thread to see the updates.

However, if you are using 5.10, you use:
**mount /dev/sda6 /target/mnt/hfs**
Because 5.10 seems to be able to mount with the correct file system without being explicitly told what it is.

If you read further posts in my Applefritter thread, I have a specific post on installing 5.10.  There are specific changes needed between 5.04 and 5.10 to be successful.  This may be one of the reasons you are seeing various command sto do the same thing.  Slightly different commands are needed for different changes in the newer releases.

Also, it depends on how your disk is partitioned.  It may not be on **sda6**, but could be something in the range of **5, 6, 7, 8, 9** or even higher.  It may also not be **sda** at all.  Depending on how many drives you have installed, and which you are using, it could be **sdb, sdc, sdd**.  There are many variables that might change your your particular machine that won't be the same as anybody elses install. :)

---

### Post by smileyme on 2006-02-26
I was wondering about the "#" at the end of the command, and in fact, the first time I tried it, I left it off. I have two HDDs, one SCSI, one ATA. When I try to install on the SCSI, the installer tells me the hfs partition is sda6; and when I try it on the ATA drive, the installer says its hdc6.

This last time, installing on the ATA drive, I got to the point of "Option + F2", but only got a black screen. The only F key that would provide anything other than a black screen was the F1 key, and that just brought me back to the installer.

I'm about to try it again.

Rick :)

PS: Is there a way to blank the failed ubunto partitions without reformatting the entire drive and reinstalling OS 9. I have two drives so I can copy one to the other which only takes about 5 minutes, but its still getting old.

---

### Post by jdp on 2006-02-26
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960) has instructions for resizing the Mac OS partition with **parted** on the installer CD.  You can use parted to remove partitions, or use the partition editor that comes up during the install.  It should also ask if you want to use the existing Linux partitions for the install.  Just don't wipe the entire disk.

---

### Post by smileyme on 2006-02-27
Well, I'm typing this from my AIO running 5.1.0.

I had to figure out what machine specific changes need to be made to your instructions, like your instructions say to copy the initrd.gz, but this didn't work, so I copied the initrd.img, and that did.

I have some issues with sound and video. I read somewhere about sound being muted, and will have to look into that. The video is no better than 60 Hz, and the desktop is off set. I don't remember if I ever needed to set the display in Mac OS, but there doesn't seem to be any physical means.

At least its running Linux.

I think I'll make a list of questions I have, and post what I can't figure out on my own.

I really appreciate the help.

Rick :)

---


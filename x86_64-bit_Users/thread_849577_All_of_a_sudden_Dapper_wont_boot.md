---
title: "All of a sudden Dapper wont boot"
date: 2008-07-04
forum: x86 64-bit Users
---

### Post by Linuxer on 2008-07-04
I have been using Dapper LTS for the past three years and couldn't be happier.  It has been extremely stable.  When I went to boot this morning, it get to the progress bar and gives the message "loading file system" and then dumps me out to # prompt.  

I couldn't copy and paste the error messages, but here are some of them:

couldn't find /dev/hdb1
couldn't find /root
couldn't find /etc/fastb

I have 2 physical hard drives in my system.  I have windows 2000 on the first drive and Ubuntu on the second drive.  I use Grub.

Did my Ubuntu drive die? What tool can I use to diagnose and possible fix the problem?  I have Knoppix live cd if that would help.  

Thanks in advance.

---

### Post by werries on 2008-07-04
i really suggest booting any livecd and saving your files to a different system. always the first recovery step.

Also try viewing the folder and make sure those folders are there.

---

### Post by radopenev on 2008-07-05
I think you have GRUB problem.
Maybe this helps you...
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
Good luck!

---

### Post by nikgare on 2008-07-05
You could try selecting another Ubuntu kernel via the grub menu at boot up to see if that helps.

---

### Post by Linuxer on 2008-07-06
I just booted from a Knoppix live cd and tried to read my linux drive.  I got the following message:

>>Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,<<


If drive itself is physically okay, how do I repair "superblock"

Thanks in advance.

---

### Post by radopenev on 2008-07-07
Try this:
[http://wiki.clug.org.za/wiki/RAID-1_in_a_hurry_with_grub_and_mdadm]("http://wiki.clug.org.za/wiki/RAID-1_in_a_hurry_with_grub_and_mdadm")
Good luck!

---


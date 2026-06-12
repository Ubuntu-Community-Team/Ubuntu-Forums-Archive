---
title: "Grub/Boot problem &quot;Error 15- File not found&quot;"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by painterh on 2008-10-16
Hey there all;
I have got a real pickle here.  I have a dual-boot system using 2 separate hard drives.  I have Win XP on one, and Ultimate Edition 1.8x64 (Hardy 8.04 Hardy) on the other.  I just installed an update in Hardy and it noted in panel that a restart was required.  The updates included the latest nvidia driver, and a kernel update from 2.6.24-19 to 2.6.24-21.  I restarted and everything seemed as normal, so I proceeded to make a few changes using startup manager such as the bootsplash image and resolution of boot splash image.  It seemed to hang for a while during application of changes.  I don't know why but I thought it was completely hung, and restarted.  Upon restart I got to the grub screen and found the choices were Ubuntu 8.04 2.6.24-16-generic, Ubuntu 8.04 2.6.24-16-generic recovery mode, memtest, Other OS, and my Win XP install.  There wasn't even a mention of the updated kernel 2.6.24-21.  I selected the first Ubuntu install, but instead of loading I got a black screen with a grub message "Error 15, File not found".  I have tried SuperGrub disk, but was uable to (or didn't how) to fix the problem.  I seldom use Windows any more, and I have most of my improtant files on Ubuntu partition.  I have installed Ext2 IFS in Windows, which allows me to read and write to my Linux drive from Windows but this seemed to be of no value as Windows does have any programs to edit files the way gedit does.  I also tried booting a live cd and could read my Menu.1st file but didn't have permission to make any changes.  Does anyone have some ideas how to restore my 2.6.24-21.  Right now I am relegated back to Windows.  Anybody, Please!

---

### Post by dabl on 2008-10-16
You need to fix Grub.

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by painterh on 2008-10-16
dabl;
Thanks for the reply.  I will carefully go through the post " fixing grub".  I will probably give it a try late today, as I am off to Engineering class.  If I run into any problems using the guide I'll go through the thread and try to find the answer.  Again, thanks for the link.  Hopefully I can sort it from there.

---

### Post by painterh on 2008-10-19
Thanks for the input. I finally found the answer I needed, by going to the SuperGrub page and carefully reading instructions. It was not nearly as cryptic as I was making it out to be. I merely selected the erroneous menu.lst entry by putting in the info for the current kernel and location (typing it in the same order as the other entries, saving it and voila'. Amazing what you can co when you read directions. Thanks again

---


---
title: "OSX+Ubuntu file transfer"
date: 2006-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flipper on 2006-02-21
Hi, i currently have Ubuntu and OSX tiger in my ibook, how can i share files between the partitions?

---

### Post by stuporglue on 2006-02-21
Here's a couple options...

1) Mount the OSX partition in Linux and access the files. Ubuntu supports mounting the hfsplus partition type used by OSX> 

2) Mount the linux partition (ext2 or ext3 only!) on OSX and access the files.
[https://sourceforge.net/project/showfiles.php?group_id=64713&release_id=394817](https://sourceforge.net/project/showfiles.php?group_id=64713&release_id=394817) 

3) Use MOL and set up a network drive to copy files between them. 
[http://maconlinux.org](http://maconlinux.org) -- it seems down at the moment, but that might be my school's network...
[http://72.14.207.104/search?q=cache:wPEW-a_VGIcJ:www.maconlinux.org/+maconlinux&hl=en&gl=us&ct=clnk&cd=1&client=firefox](http://72.14.207.104/search?q=cache:wPEW-a_VGIcJ:www.maconlinux.org/+maconlinux&hl=en&gl=us&ct=clnk&cd=1&client=firefox)

#1 I've never had any trouble with

#2 is somewhat risky. I ended up with a corrupt ext3 partition once because OSX didn't always cleanly unmount the drive. 

#3 won't work from OSX, but can be usefull from Linux.

---

### Post by Flipper on 2006-02-22
tks for your reply :)
can you help me with option nº 1? 
as for the 3rd , my ibook is only a 366mhz, can it handle the MOL ok?

i found this link, to make the 1st option you sugested 

[mount]("http://jclark.org/weblog/Miscellany/ubuntumount.html")

do you think it should work?

---

### Post by jdp on 2006-02-22
MOL runs at nearly native speeds.  I've run it before on a 266MHz Beige G3 , and as long as you have  plenty of RAM to prevent swapping it'll run OK.  The realyl nice thing about MOL is that it can act like a NewWorld machine, even if it's run on an OldWorld.  Thus, I could boot OS X or Linux inside MOL directly from a partition, instead of needing BootX.  Of course I still needed BootX to get the host Linux install booted...

---

### Post by Flipper on 2006-02-23
So, if i have osx installed in one partition, i can boot it within MOL? :) sweet, i'll have to try that later.

ps: i have solved the hfs+ mount problem :)

---

### Post by engla on 2006-02-23
As for trying mol, I recommend you to not use any Ubuntu packages. You have to compile the kernel module yourself anyway. I tried the route of using the repositoriy packages to install and then the package for the kernel module source.. wouldn't work.

However, pulling the full source for everything and building it together seems to have worked great, I have mol running pretty nicely. I usually just use ssh to transfer files now.

---

### Post by Flipper on 2006-02-23
tks, i'll compile the kernel then :)
As for the file transfer, i mount the OSX hfs+ partition, and everything works great :)

---

### Post by jdp on 2006-02-24
The repository packages in Dapper are supposed to solve the kernel module problems.  I read the report here on the forum, but I don't remember if it's available as a backport yet.

---

### Post by engla on 2006-02-24
[QUOTE=Flipper]tks, i'll compile the kernel then :)
As for the file transfer, i mount the OSX hfs+ partition, and everything works great :)[/QUOTE]
Hey oops, I made a typo. I don't think you need to compile the kernel, just the **kernel module** that mol requires.

---


---
title: "ntfs-3g in fiesty"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by r_rehashed on 2007-04-25
The ntfs-3g packages in Ubuntu's repos. are a bit old compared to the current stable version.

Previously, [this thread]("http://ubuntuforums.org/showthread.php?t=217009") had given some Universe repos. for Dapper and Edgy. Any such repos. for Feisty?

Just want to be as safe as possible with ntfs. :)

---

### Post by xopher on 2007-04-25
The version that is currently in the Feisty repos is 1.328:

> STABLE Version 1.328 (March 28, 2007) -- [Release Notes]("http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/132")

    * change: document and release version update to stable status 


And there has only been one stable release after this. You should know the release-policy of Ubuntu, which is not to update but security issues, and perhaps some trivial usability issues.

The update might become available through a backport later though.

The drivers have been thoroughly tested and are sure to be safe, so I wouldn't worry about that.

---

### Post by Churnd on 2007-04-25
It's already in the repos for Feisty... just enable Universe and Multiverse.  There's even a configuration utility:

[LIST]
[*]Click Applications
[*]Click Add/Remove
[*]Show:  All available applications
[*]Search for NTFS
[*]Install the NTFS Configuration Tool, which also installs ntfs-3g
[/LIST]

The rest is self explanatory. :)

---

### Post by djmaxmalta on 2007-06-09
:popcorn: hmmm sounds easy but actually no! my version is 0.5.5 which i install from add/remove! and how may i get the new stable relase and that  this version i have disable my read/write aswll and that i can't mount the partions!



> **Churnd said:**
> It's already in the repos for Feisty... just enable Universe and Multiverse.  There's even a configuration utility:

[LIST]
[*]Click Applications
[*]Click Add/Remove
[*]Show:  All available applications
[*]Search for NTFS
[*]Install the NTFS Configuration Tool, which also installs ntfs-3g
[/LIST]

The rest is self explanatory. :)

---

### Post by gotmonkey on 2007-06-09
Thanks for the heads up! It was quite simple. 

Searched for ntfs, installed ntfs-config (pulled the ntfs-3g as dependancy). Opened the config applet, select enable write support for external drives. click boom bang.. all worked

plugged usb ntfs drive in and started copying files to the drive.

largo vive la fuente abierta (long live open-source)

---

### Post by saxonjf on 2007-06-10
I got it to work, but after the applet was installed, I had to restart Feisty.  Not a big deal, and I am thrilled I can write to my Windoze partition now.  Thanks.

Why on earth are they not allowing write to ntfs straightway?

---


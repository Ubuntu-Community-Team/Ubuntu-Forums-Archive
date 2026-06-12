---
title: "Not so Dual booting"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by Mr.Useless on 2008-06-27
Ok so i have ubuntu 32 bit i really like it, i just formatted my HDD with windows on it to dual boot ubuntu 64 and 32

Reason:
Testing 64 to see if all the apps i want run almost flawlessly on 64 if so then doing a complete switchover and having linux64bit on my main HDD and xp pro on my IDE HDD (What 32 bit is currently installed on)

So i installed it all it which was fine it gave me the option to import these settings from this account which i thought was handy. But when i came to booting up GRUB loaded and it only shows my 32bit installation the recovery mode and memtest. im SURE of this because when i goto Computer, my main HDD (which is 160gb) is called 158.5gb Media, and my Original instal is Called Filesystem

Is what im doing not meant to be done? has GRUB installed improperly on ,my other drive, i even made the boot order so my 160gb drive was loaded first, but it takes me to the 32bit one. It also says on the GRUB menu, Ubuntu 8.04.1, Ubuntu 8.04.1 (recovery mode), Ubuntu 8.04.1 Memtestx86

Then under other installations:
Windows 95/98/2000/ME/XP
Which is definatly NOT installed anymore, could it just be that i need to update my Grub orr...???

Anyone got a solution, and if it means flattening my 32 bit install well...i wont be best pleased :D

Thanks

Ryan

Oh, if i goto the GRUB manual loader, what is the command line to load the 64bit one? if there is one?

[http://codepad.org/b7NnZP0V](http://codepad.org/b7NnZP0V)

---

### Post by russlar on 2008-06-27
take a look at /boot/grub/menu.lst

I can't tell from your post, but it sounds like you might have installed 64 bit on top of your 32 bit, on the same hard drive.

---

### Post by Mr.Useless on 2008-06-27
[http://www.picoodle.com/view.php?img=/4/6/27/f_SATAHDD64m_9e779d2.png&srv=img33](http://www.picoodle.com/view.php?img=/4/6/27/f_SATAHDD64m_9e779d2.png&srv=img33)

160gb HDD

[http://www.picoodle.com/view.php?img=/4/6/27/f_IDEHDD32m_416f6e3.png&srv=img27](http://www.picoodle.com/view.php?img=/4/6/27/f_IDEHDD32m_416f6e3.png&srv=img27)

120GB HDD

Sure looks like different hd, im looking into the menu.lst now ill see if i can work with my mate to merge them somehow, but any help is appreciated

Ryan

---

### Post by mitchell19 on 2008-06-27
Mr.Useless, tell us what yout /boot/grub/menu.lst is like.

just start a terminal and type "cat /boot/grub/menu.lst", and paste it here so that we can help you.

---

### Post by Mr.Useless on 2008-06-27
Ok i managed to get it to work after numerous installs, i just unplugged my other HDD installed it, then booted up, turned off plugged my other one back in and now it always boots the 64 without the grub menu, im having trouble formatting my other drive now, ill see where to make a post about that though, thanks btw :D

Mr.Useless

---


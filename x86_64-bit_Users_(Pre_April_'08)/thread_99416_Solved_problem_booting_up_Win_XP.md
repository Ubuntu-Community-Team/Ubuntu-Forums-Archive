---
title: "Solved problem booting up Win XP"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Liudwik on 2005-12-05
Well, I was using Win XP untill I decided to intall Ubuntu. From WinXP prepared new partinions for Ubuntu (Partition Magic), and succesfully installed Ubuntu. Everything was ok, until i decided to launch WinXp (via Grub) again. During WinXP start ups my PC hanged every time and the following error was displayed: Stop: c000021a... After that the only possible action to do was - phisically restart PC.  As far as I'm very and very newbie to Linux I tryed reinstalling both WinXP and Ubuntu but it didn't solve my problem.  

I have single HDD
My WinXP was installed on the hd0,0; and Ubuntu was installed on hd0,5. During Ubuntu installation Grub was installed in to MBR

The solution was:
1. used this helpfull guide and configured Grub's menu.lst

[http://www.ubuntuforums.org/showthread.php?t=84904&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=84904&highlight=grub)

2. run Grub in Terminal and used command "unhide (hd0,0)". Maybe for your case it could be appropriate partition with your Win on NTFS 

* grub
* unhide (hd0,0)

as far as i understand the partition hd0,0 was hidden by Grub during its instalation or by default configuration. And that was the problem for WinXP to start corectly.

So, that's the way I solved my problem. And I'll be glad if this guide wi'll be usefull for such newbie as I am (using Linux for a one week, but going to stay here for all the time:))

---

### Post by nalmeth on 2005-12-06
Glad you were able to solve your own problem. Good stuff.
Just for general discussion, isn't it possible to have the ubuntu installer resize the partitions if you have windows or other dist installed, and then to have it included in the grub menu?
Would this have worked better or worse for liudwik?
Is it dangerous to do this? I'm running straight ubuntu right now, so not a worry for me, but I am wondering anyway.

---


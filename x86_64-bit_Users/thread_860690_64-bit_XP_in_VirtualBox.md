---
title: "64-bit XP in VirtualBox"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by hansmax on 2008-07-15
I would like to install Hardy Heron in VirtualBox on my WinXP (64-bit) system.  I have downloaded the 64-bit version of Hardy Heron.  I would like to install it from my hard disk using Wubi.  When I look at supported host operating systems (in the VirtualBox user manual), I see Windows XP (32 bit).  I also see Vista (32 and 64 bit).  Does this mean that I should under no circumstances attempt to install Hardy Heron in VirtualBox on my 64 bit WindXP system, or is this merely an oversight on the part of the writers of the manual.  I'm fairly new to Linux, although I had the previous version of Ubuntu running in a dual-boot on this machine, but removed it because I had not done an adequate job of pre-indoctrinating my wife to the idea.  I'm just trying to break my Bill Gates addiction one step at a time.  I have seen the future of Microsoft, and it is not pretty.  Any input would be appreciated.

---

### Post by cjm5229 on 2008-07-15
If you install it using Wubi you don't need Virtual Box. It makes a file in Windows with an ext3 filesystem and installs it to that file. It can be uninstalled from Windows just like any other program. You can install it in Virtualbox like you would install it into a partition, but it won't work as well as it does from Wubi. Wubi uses your machine hardware including memory and Graphics cards, where as Virtual box is using emulated hardware and shares memory.

---

### Post by Dizzle7677 on 2008-07-15
I don't see why you couldn't since it works with Ubuntu Edgy...
[http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png]("http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png")

---

### Post by hansmax on 2008-07-15
Thanks to both of you for responding quickly, and thanks for the headsup on the Wubi installer, cjm5229.  It should save me some wasted effort.

---

### Post by stmiller on 2008-07-15
Slightly OT but FYI: Virtualbox cannot do 64bit guests. Though VMware can...

---

### Post by hansmax on 2008-07-16
Thanks, stmiller.  That was the answer I needed.  I won't attempt to install in VirtualBox.

---


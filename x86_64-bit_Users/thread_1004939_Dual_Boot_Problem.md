---
title: "Dual Boot Problem"
date: 2008-12-07
forum: x86 64-bit Users
---

### Post by Tacofish on 2008-12-07
Hello! I have a pretty large problem in my opinion. I got so tired of Vista that I decided to get rid of it entirely and install ubuntu 64 bit instead! However, I'm a gamer and have had a few technical problems on my Dell XPS with Ubuntu. Really, I don't know how to use terminal and the coding in general confuses me since I only know basic HTML and JAVA. Anyway, I found a Windows XP disc laying around my old computer so I decided to try and use that instead! However, when I put in my Ubuntu boot CD to try and repartition my hard drive, I couldn't even get it to start up. I'm trying to use the Autorun prompt but it won't let me, and when I click on umenu.exe the menu comes put but after I click on demo and full installation and then restart now, nothing happens? also, I can't install the XP CD because it's not partitioned (or something to that effect). Can anyone help me out? I'm really confused and feel like a fish out of water now that I can't play games anymore :(. Any help at all would be greatly appreciated :D

---

### Post by RansomStark on 2008-12-07
Its usually easier to install windows first, then install ubuntu after as it can auto re-partition the drive and setup the bootloader so you can access both operating systems from a menu at bootup.

---

### Post by falcon61102 on 2008-12-07
When you say you couldn't even get the LiveCD to start up, is that when you restarted your system?  If your BIOS isn't set to read from the CD drive first then you need to press a key to load the Device Boot Menu (should be F12 for you).  About half way through the BIOS hit that a couple times, just to make sure it registers and then it should bring you to a Device Boot Menu.  Make sure your LiveCD is in the drive and then select CDROM.  This should get you into the LiveCD.

As RansomStark said, it's much easier to start with Windows and install Ubuntu behind that because Windows has some dependancy issues.  If Windows isn't installed on the first partition of the first drive it tends to have errors and since your Ubuntu partition is current in that location, you can do a couple things.  
First: Resize and Move Ubuntu partition to create space for Windows at the beginning of the drive.
Second: Backup Ubuntu and start fresh with Windows and then reinstall Ubuntu after.
Third: Attempt to install Windows behind Ubuntu and do the many work arounds to get it working.

While the first option is easy to complete, it takes a long time because of the process of moving the Ubuntu partition.  It is probably quicker to back up your Ubuntu files and do a fresh install.

Let us know which route and if you need any help going that way.

---

### Post by Tacofish on 2008-12-07
Thanks for the F12 thing :D! That helped immensly, but now I loaded up the live CD and before I get a chance to see it load something called "Busybox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)" loads...and I have a long list of commands to choose from? Is this a bug? Am I not doing something right?

And I think what I want to do is get rid of ubuntu entirely and get XP instead. It's not that I don't like ubuntu, I just don't understand it and it's not right for me :P.

---

### Post by falcon61102 on 2008-12-07
Are they commands printed on the screen or errors?  List the last few lines so we get an idea of what you are looking at.

---

### Post by Tacofish on 2008-12-07
They're commands listed on the screen, probably not an error... I'll need to go back to it to look at it again.

---


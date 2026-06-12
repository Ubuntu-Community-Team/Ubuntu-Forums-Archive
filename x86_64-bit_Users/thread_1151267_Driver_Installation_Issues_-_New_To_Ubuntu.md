---
title: "Driver Installation Issues - New To Ubuntu"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by TheRy1985 on 2009-05-06
First time Linux user here, just swapped out XP x64 for Ubuntu x64 and looking foward to a non Windows system. That being said this is a whole new world for me.

My problem is I have two NVIDIA 9600 GT's and I want to enable SLI. I downloaded the Geforce 9 Series Linux x64 drivers from nvidia.com and try to open from the desktop and I get:
**Could not open the file /home/nforce/Desktop/NVI...-Linux-x86_64-180.51-pkg2.run**[B].
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/B] 

Tryed sh NVIDIA-Linux-x86_64-180.51-pkg2.run from the terminal as nvidia directions say:
[B]nforce@nforce-desktop:~$ sh NVIDIA-Linux-x86-180.51-pkg1.run
sh: Can't open NVIDIA-Linux-x86-180.51-pkg1.run([/B]All Previous methods tryed with 32 and 64 bit versions**)**

Am I going about this the wrong way? I also need to install my Creative SB X-Fi Extreme Gamer Sound drivers etc.. but no sense going any further untill I can get vid drivers in. Any Help is appreciated as I did some searching but found nothing directly related to my situation.

System Specs:
Ubuntu 9.04 x64 (Desktop Edition)
AMD Athlon x2 6400+ @ 3.2
ASUS M2N-SLI Deluxe
2x2GB Patriot Viper DDR2-900
BFG/Galaxy NVIDIA 9600 GT OC's
Creative X-Fi Extreme Gamer Sound
Some other irrelevant goodies

Chipset drivers... I dont think I need to install them since network worked right out the gate but not sure. Hope not as ASUS hasn't released a 64-bit version for linux. Yay or Nay? :confused:

---

### Post by TheRy1985 on 2009-05-06
Update: Went to properties on NVIDIA-Linux-x86_64-180.51-pkg2.run and set to allow executing file as a program. Then I Launch in terminal and get "  ERROR: nvidia-installer must be run as root". Looks like I need to switch to root some how from desktop. Can some shed some light on this?

EDIT: Ok still searching around and found su in terminal should switch me to root but there is a password on it I didnt get a chance to set? Only password I have set to this time I have tryed and is wrong.. confused

EDIT: Creative Drivers are installed following a post I found here, still no luck with video though. On IRC now

---

### Post by esdaniel on 2009-05-06
You might find it helpful to use the IRC channel as well for real time support if this is new territory for you, it will save you the long intermittent periods of frustration punctuated by groaning while you learn the Ubuntu way:
[http://www.ubuntu.com/support/community/chatirc]("http://www.ubuntu.com/support/community/chatircTo")

To learn more about what *sudo* is check out:
[http://en.wikipedia.org/wiki/Sudo]("http://en.wikipedia.org/wiki/Sudohth")

hth.

---

### Post by TheRy1985 on 2009-05-06
> **esdaniel said:**
> You might find it helpful to use the IRC channel as well for real time support if this is new territory for you, it will save you the long intermittent periods of frustration punctuated by groaning while you learn the Ubuntu way:
[http://www.ubuntu.com/support/community/chatirc]("http://www.ubuntu.com/support/community/chatircTo")

To learn more about what *sudo* is check out:
[http://en.wikipedia.org/wiki/Sudo]("http://en.wikipedia.org/wiki/Sudohth")

hth.

Thanks for the reply, on IRC now but no one seems to interested lol. I guess im going to try and take a peek at the creative driver tutorial and modify for nvidias? Out of ideas

---

### Post by esdaniel on 2009-05-06
This might cheer you up:
[http://www.darraghverschoyle.com/2009/03/enabling-sli-on-ubuntu-810/](http://www.darraghverschoyle.com/2009/03/enabling-sli-on-ubuntu-810/)

---


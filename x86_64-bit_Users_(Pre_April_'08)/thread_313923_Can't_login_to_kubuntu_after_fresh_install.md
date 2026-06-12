---
title: "Can't login to kubuntu after fresh install"
date: 2006-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoiZ22 on 2006-12-06
Hi guys, I'm new in the forums and new to Linux.
I installed Kubuntu 6.10 alternate version i386 on my laptop and works just fine, now I'm trying to install the 64bit version on my machine.

So here goes my problem, I've done a fresh install on my machine twice already and keep getting the same problem, the installation process goes nice and smooth, no hassles there. But, once the install is completed and I reboot my system, to login to my freshly installed **Kubuntu 6.10 alternate version x86_64bit** (which I downloaded off the net and ran a check for erros of the CD prior to installation, which said that the CD has no errors) I keep getting asked for a login and password, but when I enter my username and password that I setup during the installation, the login and password lines change to **noiz@Xtreme:~$** (NoiZ being my username and Xtreme being the name of my box or hostname if you will) I enter my login and password again and nothing happens.
So here I am wondering if anyone can help me out with this one, cuz I can't login into my Kubuntu.

Here are the specs of my machine:

Intel Pentium Extreme Edition Dual Core 3.2 Ghz
[ASUS P5WD2 Premium Motherboard]("http://www.asus.com/products4.aspx?l1=3&l2=11&l3=184&model=493&modelmenu=1")
4 Gb Apacer DDR2 RAM
256 Mb PCI-E ATI RADEON X850 XT Platinum
1 x 80 Gb SATA WesterDigital RAPTOR
2 x 250 Gb SATA WesterDigital Caviar
1 x 320 Gb SATAII WesterDigital Caviar

Sound and Ethernet built in the Mobo.

Thanks in advance for your help.

Cheers

NoiZ

PS: I'm also running WinXp x64 on the same system

---

### Post by klayn on 2006-12-06
I'm a newbie myself, but try typing either ```
X
``` or ```
kdm
``` and see what kind of an error (if any) it gives you and post it so people can help diagnose the problem better...

---

### Post by NoiZ22 on 2006-12-06
K, when I type "x" I get:

noiz@Xtreme:~$ x
-bash: x: command not found

so then I tried "kdm" and the result:

noiz@Xtreme:~$ kdm
Only root wants to run kdm

I also tried "X" and it comes up with

X Window system Version 7.1.1
Release Date: 12May 2006
X Protocol Version 11, Revision 0, Release 7.1.1.
Build Operating System: Linux 2.6.15.7 x86_64
Current Operating System: Linux .....
Build Date ....
Module Loader Present
Markers: .........
(==) Log file: "/var/log/Xorg.0.log" ....
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screen found
noiz@Xtreme:~$

Could this have something to do with my monitor, I'm using a Dell 24 inch LCD.

---

### Post by NoiZ22 on 2006-12-06
Well after searching on the net I found out that it was the ATI driver so I ran this command ***sudo apt-get install xorg-driver-fglrx*** and it worked, I'm logged in now.

:D

---


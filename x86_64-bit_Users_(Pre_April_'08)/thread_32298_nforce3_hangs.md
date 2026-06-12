---
title: "nforce3 hangs"
date: 2005-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rush_ad on 2005-05-06
so as the title says, my computer just hangs randomly.

i can start it up and everything and then after sometime (not more than 10mins) it just hangs. everything stops responding and then i have use restart button to start windows.

i have tried installing 64-bit ubuntu and kubuntu and both hang. i also tried booting with 32-bit kubuntu disk and even that hangs. so i didnt install 32-bit on hard drive. i suppose it will hang too.

i thought it was hard drive problem at first, so i took out the drives and booted with live cd. even that hung. so i suppose its a hardware problem. also tried booting with noapci, noapic and all other combinations. nothing seems to work. all those configurations hang.

and as to my surprise, gentoo works fine. no problem and no need to use noapic whatever options. everything but gentoo doesnt work. i tried suse 9.2 and 9.3 but they do not work at all. same problem as ubuntu. only gentoo and windows work.

here is my hardware
amd64
nforce3 gigabyte ga-k8ns motherboard
3x256 mb ram
radeon rage 128 32mb

so please let me know how i can fix my problem. i really want to use ubuntu and not gentoo or windows. gentoo is good but too much configurations. ubuntu just works.

someone please make thiis work for me. tired of windows. i am open to any suggestions. used gentoo for a year so i am not that bad at following directions.

thanks in advance.

---

### Post by sgbooth on 2005-05-09
This is a common problem with Nvidia drivers.  It took me a while, but I found that the problem also exists for ati drivers.  See the following post for fixing it:

[http://ubuntuforums.org/showthread.php?t=24703&highlight=freeze](http://ubuntuforums.org/showthread.php?t=24703&highlight=freeze)

---

### Post by arx-lupus on 2005-05-09
I had much the same problem on an Asus Nforce3 motherboard - and disabling all USB (apparently USB2 is the problem) on the motherboard solved the problem.

I have not had a problem with the nforce drivers installed as standard (the reverse engineered ones)

---

### Post by rush_ad on 2005-05-09
[QUOTE=sgbooth]This is a common problem with Nvidia drivers.  It took me a while, but I found that the problem also exists for ati drivers.  See the following post for fixing it:

[http://ubuntuforums.org/showthread.php?t=24703&highlight=freeze](http://ubuntuforums.org/showthread.php?t=24703&highlight=freeze)[/QUOTE]
 i have a different problem. my computer just freezes. everything stops working. music stops (speakers start make wierd noise) no internet or anything. 

and i dont have a nvidia video card.

---

### Post by rush_ad on 2005-05-09
[QUOTE=arx-lupus]I had much the same problem on an Asus Nforce3 motherboard - and disabling all USB (apparently USB2 is the problem) on the motherboard solved the problem.

I have not had a problem with the nforce drivers installed as standard (the reverse engineered ones)[/QUOTE]
 so i have to disable all USB from bios?? then how would i be able to use my USB dvd-rw, and other accessories?

those USB things worked when i was using gentoo.

---

### Post by sgbooth on 2005-05-10
[QUOTE=rush_ad]i have a different problem. my computer just freezes. everything stops working. music stops (speakers start make wierd noise) no internet or anything. 

and i dont have a nvidia video card.[/QUOTE]


No, you misread my post.  The problem also occurs on ATI video cards. Here is the solution:  

[INDENT]sudo nano /etc/X11/xorg.conf[/INDENT]

Look for  [COLOR=DarkGreen]Section "Device"[/COLOR] and insert

[INDENT]Option "RenderAccel" "false"[/INDENT]

Logout and restart X.

---

### Post by datajack on 2005-05-13
[QUOTE=rush_ad]so i have to disable all USB from bios?? then how would i be able to use my USB dvd-rw, and other accessories?

those USB things worked when i was using gentoo.[/QUOTE]


I have this problem with Ubuntu, it also occured with Fedora Core 2. However, it *does not* occur with Mandrake 10.1 - which I want to migrate from.

I have tried with the nv video driver, and the vesa driver. Ihave also disabled USB on my system, yet it still locks up randomly.

I think I will give Gentoo a try this weekend, but I would prefer to get Ubuntu up and running, as that is what I use on my laptop.

---

### Post by HellSpawn on 2005-05-18
Hi!!

I have the same Mobo, and I think, the same problem

Gigabyte GA-K8NS (Socket 754) nForce3
AMD Athlon 64 3000+
2x512Mb  DDR400
IDE HD 80 Gb
Sata HD 80 Gb
IDE DVD Burner
IDE DVD Driver

I have tryed Fedora Core 3 64 bits and Ubuntu 64 generic, both with the same result, after random time and random software usage, the PC completly freezes, no ping, no ssh, no mouse, no Num Lock....

With 32 bits, I didn't have any problems till yesterday after using some USB device the PC freezed  :neutral: 

But I knowest something...
Yesterday, after freezed I had tu turn off the PC with the case Power button and the Keyboard lights kept on until I turn of my PS with it's own on/off switch, and the other night after freezed useing Ubuntu 64, my USB optical mouse kept it's light on after turning off PC with the Power case button...  :-| 

So... I don't know what's wrong, PS, MB, CPU???.... 
What kind of test can I run?? with what software?? memtest86+ doesn't report any issues... I don't get any log about problems on the systems logs.

Thanx for any help

---


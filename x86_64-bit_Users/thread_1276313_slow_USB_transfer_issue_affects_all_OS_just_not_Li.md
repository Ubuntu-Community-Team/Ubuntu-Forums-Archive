---
title: "slow USB transfer issue affects all OS just not Linux"
date: 2009-09-26
forum: x86 64-bit Users
---

### Post by Arup on 2009-09-26
Since people in this forum have been claiming about slow USB transfer issue being particular to Linux, Ubuntu in general, here are some of the snippets from several Windows forum and you can see even Windows 7 suffers from the same issue.

[http://www.sevenforums.com/performance-maintenance/22350-slow-usb-transfer.html](http://www.sevenforums.com/performance-maintenance/22350-slow-usb-transfer.html)

[http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/60a7b507-9bda-4e66-8693-b85498cd860c](http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/60a7b507-9bda-4e66-8693-b85498cd860c)

[http://forums.windrivers.com/showthread.php?t=63440](http://forums.windrivers.com/showthread.php?t=63440)

As you can see this is a very old and annoying issue affecting both Windows and Linux with certain hardware. So please don't go out crucifying Linux or Ubuntu on this and then make posts like, " I am going back to Windows 7 as its faster " etc.

This issue needs to be worked out from either end. I have had slow transfers with USB using Windows XPx64 and the beta copy of 7 and I get the same issue on some of my PCs with Ubuntu and Fedora.

---

### Post by Arup on 2009-09-27
:D:D:D

I was expecting response to this thread since its parallel to the slow USB transfer under Jaunty thread. I can't post there since its full of people who have outright declared this problem to be a Linux issue and blamed the developers and even dragged Linus into this. One of them even goes on to claim that Windows 7 has no such issues when the very links posted here show otherwise. Now this is not a solution to this problem but at least its indicative of the universal nature of this issue and just not limited to Linux.

I just can't figure out characters who would come here and claim to be disgruntled Ubuntu users and blame all on Ubuntu and Linux and then harp on the virtues of Windows. Folks, Linux and Ubuntu are free offering and a volunteer effort, no $$$$ is charged for its use and having said that, for a volunteer effort in which you pay no money, its well supported and has fewer issues than even the paid OS out there. Bickering will get you nowhere. This is a firmware/brand/bios specific issue affecting all OS and just not Linux/Ubuntu.

---

### Post by darco on 2009-09-27
Dude, give it a rest....didnt the admins lock the previous thread because of your "holier-than -thou" attitude in your responses? Its not like YOU invented Linux or something, or did you?

darco

---

### Post by QIII on 2009-09-27
On a technical note about USB hard drives, after some research...

The problems in both Vista and Linux seem to have to do with the amount of current drawn through the USB bus to spin up the platters inside the USB enclosure when the enclosure is powered by the USB.  This results in an incorrect report back to the OS with regard to the available transfer speed.  That incorrect value (which turns out to be the USB 1 or, if you are lucky, the USB 1.1 transfer rate.)  is used by the OS and you are stuck with it.

A possible solution on all OSs is to use two USB cables if your hardware supports that.  The other is to simply use an external power supply.

---

### Post by jflaker on 2009-09-27
> **QIII said:**
> On a technical note about USB hard drives, after some research...

The problems in both Vista and Linux seem to have to do with the amount of current drawn through the USB bus to spin up the platters inside the USB enclosure when the enclosure is powered by the USB.  This results in an incorrect report back to the OS with regard to the available transfer speed.  That incorrect value (which turns out to be the USB 1 or, if you are lucky, the USB 1.1 transfer rate.)  is used by the OS and you are stuck with it.

A possible solution on all OSs is to use two USB cables if your hardware supports that.  The other is to simply use an external power supply.

Buy a powered USB hub....plug into your hub then you'll have little if any current draw from the system's USB port....Problem solved.

When using my laptop's USB from the laptop, I get SLOW-ER transfer rates...when I am using the USB from the docking station's USB port (basically a powered USB), I have decent, dare I say, faster than normal transfer rates

---

### Post by QIII on 2009-09-27
> **jflaker said:**
> Buy a powered USB hub....plug into your hub then you'll have little if any current draw from the system's USB port....Problem solved.

When using my laptop's USB from the laptop, I get SLOW-ER transfer rates...when I am using the USB from the docking station's USB port (basically a powered USB), I have decent, dare I say, faster than normal transfer rates

Agreed.

The problem is the current draw.  Get it from a source other than the USB bus, however you do it, and you are golden.

Powered USB hubs are inexpensive.

---

### Post by Arup on 2009-09-27
The current draw issue is pertinent, also some boards have the situation of over current. I have seen lower end Intel boards fry USB components with regularity but never suffered from slow USB transfer issue. Well at least we are heading in the right direction. Powered USB hubs is a good suggestion, they are also quite useful and make using and plugging USB components far more easier.

@ darco

Would you rather be bashing Linux and Ubuntu and threatning to go back to Windows? This issue is univeral to all OS, just not Linux. Are you represnting Windows or on Gates' payroll? Holier than thou, its like you are trying to shelter Windows when all we are trying to do is to find a viable solution instead of cursing the OS. So if you don't have a solution, at least don't be a Windoze troll.

---

### Post by Arup on 2009-09-29
Just got update from one of the forum members, he bought himself a powered USB hub and his transfer rates went up big time. Seems like we all owe it to QIII for posting a viable solution to this issue.

---

### Post by Nick Brohman on 2009-09-29
> **Arup said:**
> Just got update from one of the forum members, he bought himself a powered USB hub and his transfer rates went up big time. Seems like we all owe it to QIII for posting a viable solution to this issue.

Hello, I could be that member & I will say that a powered USB hub helps in other ways as well.
My experience is limited to Linux & I started with a bare box ( I actually had Windows on my original Celeron for about 3 weeks & that was a year too long for me).
I have a Canon Powershot 470 & often take a thousand photos in the largest format available & that takes a while to download. 
This pm I took 143 @ 1600 X ... & barely had time to blink, they were loaded so fast.
These last few hours I have scanned about 150 photos with my HP 5200 using a rear USB port & the job took a little over 4 hours, the rate of data transfer has improved enough to make a chore a pleasant task.
My hub is a Logitech Premium 4-Port USB Hub for Notebooks.
It is inexpensive & very convenient. I thank Arup & QIII for this help in improving my abilities....I say [COLOR=Red]convenient[/COLOR] as it [COLOR=Red]does not require power[/COLOR] to work as it is for notebooks but[COLOR=DarkOliveGreen][COLOR=DarkGreen] when powered ....... [/COLOR]
[/COLOR] 
Nicko:):guitar:

---

### Post by QIII on 2009-09-29
> **Arup said:**
> Just got update from one of the forum members, he bought himself a powered USB hub and his transfer rates went up big time. Seems like we all owe it to QIII for posting a viable solution to this issue.

Google is a dangerous thing...  ;)

---

### Post by jerrrys on 2009-09-29
not bashing my only os, but...

i run 8.04.03 and like it.  there is about a 40% loss in usb transfer rate which i have learned to live with since my usb transfers are small.

on the other hand, i also run 8.04.01 on one drive and the xfer rate is always 100%.

so there's not going to be one good answer to this...

---

### Post by Arup on 2009-09-29
> **QIII said:**
> Google is a dangerous thing...  ;)

Indeed but the credit goes to you for googling and posting it.:)

---

### Post by ykpaiha on 2009-10-01
For my point of view 
I don't have any problem as such with Win 7 and hackintosh on the same machine.
But with Linux (despite the use of mandriva, k,x,u, buntu,fedora or else) any disk access or disk manipulation ie copy, delete, move, zip, unip etc etc cost 100% cpu usage .
I could not find any reasonable answer yet.

---


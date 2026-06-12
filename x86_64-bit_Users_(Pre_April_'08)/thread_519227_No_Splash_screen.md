---
title: "No Splash screen"
date: 2007-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Phalax on 2007-08-06
Here is my problem I am dual booting Windows XP and Ubuntu 64bit 7.04 Fiesty. This happens both when I use the live cd and when I finally have Ubuntu install. Every time I boot into Ubuntu it does not show the splash screen it is just a Blank screen and after a minute of waiting it goes to the login screen. On my first install after updating everything I went to system -> administrator -> restricted drivers -> and there was this nvidia driver not enabled so I enabled it restarted and then Ubuntu would not boot up. I waited for like 30 minutes, but nothing happened it was just a blank screen. I reinstalled Ubuntu and updated everything and so far everything is all good except there is no Ubuntu logo when booting up it is just a blank screen and after a minute of waiting it finally goes to the login screen. I tried updating my nVidia drivers...but for us noobs to linux :) It is sooooo difficult, but I'll figure that part out later.

I was wondering why is there no boot up screen, how would you solve it and is my nvidia drivers playing a role in this problem?

And if this helps heres my system specs.

AMD 64 Athlon X2 4600
Asus M2N- SLI Deluxe
2GB dual channel DDR2 800
1GB DDR2 667
Nvidia 8800GTS 320mb
and a 320 GB HDD

was going to originally get Vista, but I lost faith in Windows thats why I'm sticking with XP for now till I learn more about Linux and the commands.

Thank you guys

---

### Post by dn* on 2007-08-07
I have the same issue with my 8600GT.

---

### Post by Phalax on 2007-08-07
Well after hours of messing around with the system I finally found out how to fix this problem.
For the video card drivers I used a tool called Envy which is AMAZING!! Installed the correct drivers with me doing no work "Which doesn't help me learn I know I know, but little steps for now"

All I did to get my boot screen to work is

open the terminal type sudo gedit /boot/grub/menu.lst
and I guess for KDE its "kate" instead of "gedit"

scroll down to this line:

## ## End Default Options ##
defoptions=vga=771
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a5a01099-9975-4f24-b6fe-ce4b906c7e75 ro quiet splash **vga=792 **
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Just added vga=792 after that line up there "Kernel" (In bold letters)

the defoptions=vga=771 I honestly have no clue why I added that in lol so I dunno. :)

I take no credit in this for I spent hours on google.com I give full credit to the many guides out there. I have learned my lesson google rules!!!! and Linux! :) Search first then ask a question.

---


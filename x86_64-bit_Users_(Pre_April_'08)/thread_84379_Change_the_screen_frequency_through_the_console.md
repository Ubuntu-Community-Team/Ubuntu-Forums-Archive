---
title: "Change the screen frequency through the console"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Big Venus on 2005-10-30
How do you change the screen frequency (60,70,75,85... Hz) on your computer if you can't get it to change through the graphical interface Screen Resolution window? I just installed Ubuntu 5.10 and it sent my computer back to 60Hz and now I can get it to change the screen resolution frequency through the GUI... Any help is greatly appreciated by both me and my eyes. CRTs running at 60Hz hurts...

---

### Post by mr.p on 2005-10-31
I want to know how to do this also. :)

---

### Post by queenorych on 2005-10-31
see /etc/X11/xorg.conf.  check for the man page, or google for xorg.conf there are pleanty of guides.  Also something like X --reconfigure I think did somehting.  Probably better for ubuntu would be dpkg-reconfigure Xorg(not sure exacly what the package is called).

To see what the package is called run apt-cache search Xorg.

---

### Post by paddyg on 2005-10-31
that's right:

```
sudo gedit /etc/X11/xorg.conf
```

in the Section "Monitor" just set HorizSync and VertRefresh values according to monitor specifications

---

### Post by Jorge Siqueira on 2005-10-31
If I want to specify the frequency. let's say 75 MHz, setting the Hsinc and Vrefresh is not good enougth.

Do you know how can I specify it?

I'm using 2 computers with the same monitor (KVM switch) and both machines are using the same resolution and frequency, them my monitor can't save the configuration.

Thank you!

---

### Post by Big Venus on 2005-11-01
I tried all of those things including "sudo dpkg-reconfigure xserver-zorg". Well that said that it helped but the monitor said that it was still 60Hz on all of those including that method.

---

### Post by rplantz on 2005-11-01
I'm not sure why you cannot use System->Preferences->Screen Resolution

Of course, it won't work if you have not properly configured xorg.conf. I first did that:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

Note that I got the numbers "30-95" and "50-150" from the manual for my monitor.

You can set up the proper resolutions, according to your monitor manual, at the same time.

Then I restarted my computer to ensure that X restarts.

When I went to System->Preferences->Screen Resolution I discovered that the restart took care of everything. The screen is refreshing at the highest resolution and highest rate allowed at that resolution, according to my monitor manual.

Bob

---

### Post by Big Venus on 2005-11-01
I am dual booting and it messed up windows as well. Before I installed ubuntu 5.10, windows could recognized that my monitors max resolution was 1280x1024 @ 60Hz now it thinks that it can go as high as 2000x2000 something... I know its not the hardware because I am using the ATI 9550 graphics card and tried it with VIA integrate graphics and with a NVidia Geforce4 MX graphics card.

---

### Post by Jorge Siqueira on 2005-11-04
We can't use manufacturer defaults, because we want freedow to set wherever frequency we want, doesn't matter if the manufacturer says that the best is 60MHz, I want to use 75 MHz.

Thank you !:cool:

---

### Post by BoyOfDestiny on 2005-11-04
I just googled since I'm not at my laptop:

Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841

Don't you have a modeline in your xorg.conf?

change @60 to @85 if your monitor can take it.

p.s do not copy this modeline.

---

### Post by LitnuX on 2005-11-05
?

---

### Post by LitnuX on 2005-11-05
When i was using Slackware 10.2. I used a simple program called  XorgCFG
You just need to enter your monitors parameters and it does everything from there.

---

### Post by BoyOfDestiny on 2005-11-06
[QUOTE=Big Venus]I tried all of those things including "sudo dpkg-reconfigure xserver-zorg". Well that said that it helped but the monitor said that it was still 60Hz on all of those including that method.[/QUOTE]

Please post your xorg.conf. I just installed ubuntu64 and my monitor was at 60 hz... After adding the horizontal and vertical stuff, I'm at 1600 x 1200 with 85hz now.

---

### Post by Big Venus on 2005-11-09
I am still having problems with k/ubuntu trying to get connected with the internet. I am currently using fedora and the everything works (Microsoft Windows XP) to get on the net. I'll post the Xorg.conf file when I can transfer it to Windows or Fedora. For right now, I am also having problems booting up k/ubuntu.

---


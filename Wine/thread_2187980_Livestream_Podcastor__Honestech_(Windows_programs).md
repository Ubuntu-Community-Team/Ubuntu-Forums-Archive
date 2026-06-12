---
title: "Livestream Podcastor / Honestech (Windows programs)"
date: 2013-11-14
forum: Wine
---

### Post by pomai on 2013-11-14
First I have no idea how ubuntu works, all I have heard is that it is a small platform OS and that is what I am looking for.  Here is my challenge:  I have a Toshiba Satellite L355, 2.8 gig ram, 154.4 gig hard drive.  with a genuine intel CPU 585@2.16GHz,  OS type is 32 bit.  I just installed ubuntu v.13.04 32 bit on it, I have not added any other programs or even any data, it should be a clean install.  Now here is what I need to know:

I want to run a program called Livestream Podcastor and also a program called honestech vhs to dvd 5.0 deluxe

The program Livestream Podcastor is exactly that, it let's me livestream from my camcorder which is hooked up to the honestech box which is hooked up to a firewire connection in the express slot of the laptop.   Now what I need to know is do I need to have any other add on's to make this work?  I am pretty sure that the livestream podcastor is based on adobe flash.

I have the express card plugged in but not sure the computer see's it or not and have no idea how to check.  At this time I am hunting and pecking just to see how things work, now in windows you have windows explorer where you can see all your drives and files, I haven't even found this yet in ubuntu, I wanted to see like the properties of c drive to see how much space I have but still haven't found that yet.  

Any way any help would be most appreciated.

---

### Post by snafu006 on 2013-11-14
> I want to run a program called Livestream Podcastor and also a program called honestech vhs to dvd 5.0 deluxe

Ok so Both of the programs are For Windows so you will need a Linux program called WINE ( or PlayONLINUX ).

open your software center and search PLAYONLINUX install, open and let Playonlinux update and it will also download WINE for you as well.

After the little update click install search for the windows program you want. If it is not listed then down on the bottem left. Click install a non listed program.

> I wanted to see like the properties of c drive to see how much space I have but still haven't found that yet

I think Nautilus ( the name of the file manage ) removed that featur and alot other usefull features.

So the only way to know is a terminal command or just right click you home folder and go to properties.

---

### Post by Bucky Ball on 2013-11-15
Just a tip: You greatly improve your chaces of getting support if you use descriptive thread titles. Generic titles like 'Need help' or 'Problems' tell nothing. 99% of the posters here need help or have a problem. 

Also, Ubuntu is NOT Windows. Wine for Windows problems, sure. But there is NO guarantee they are going to run in Wine. Go here and look them up:

[http://www.winehq.org/](http://www.winehq.org/)

DO NOT install Wine before you have found out whether they will run successfully. You will be wasting your time and bloating your system for no reason. You would do much better to research open-source alternatives to the Win programs you want to use.

snafu006: Not good advice to install Wine and Playonlinux with no idea as to whether these programs will run using them. ;)

* Note: I looked them up myself. Livestream Podcaster doesn't work:

[http://www.winehq.org/pipermail/wine-bugs/2010-October/252038.html](http://www.winehq.org/pipermail/wine-bugs/2010-October/252038.html)

There is not any result for the other, untested. So snafu006, you have basically told the OP to install a bunch (lot) of unnecessary software for no reason. Once you install Wine it is virtually impossible to completely purge from the system. So OP, don't go there.

@ pomai, If you really need these apps and there is no open-source alternative I suggest you set up a dual-boot or stick with Windows. Read this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

PS: There are plenty of ways to podcast already in Linux. Not sure about the other.

---

### Post by snafu006 on 2013-11-15
> **Bucky Ball said:**
> Just a tip: You greatly improve your chaces of getting support if you use descriptive thread titles. Generic titles like 'Need help' or 'Problems' tell nothing. 99% of the posters here need help or have a problem. 

Also, Ubuntu is NOT Windows. Wine for Windows problems, sure. But there is NO guarantee they are going to run in Wine. Go here and look them up:

[http://www.winehq.org/](http://www.winehq.org/)

DO NOT install Wine before you have found out whether they will run successfully. You will be wasting your time and bloating your system for no reason. You would do much better to research open-source alternatives to the Win programs you want to use.

snafu006: Not good advice to install Wine and Playonlinux with no idea as to whether these programs will run using them. ;)

* Note: I looked them up myself. Livestream Podcaster doesn't work:

[http://www.winehq.org/pipermail/wine-bugs/2010-October/252038.html](http://www.winehq.org/pipermail/wine-bugs/2010-October/252038.html)

There is not any result for the other, untested. So snafu006, you have basically told the OP to install a bunch (lot) of unnecessary software for no reason. Once you install Wine it is virtually impossible to completely purge from the system. So OP, don't go there.

@ pomai, If you really need these apps and there is no open-source alternative I suggest you set up a dual-boot or stick with Windows. Read this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

PS: There are plenty of ways to podcast already in Linux. Not sure about the other.

ok how is it unnecessary software first he ask how it install them. he got an answer. And your answer it just going to get the dude to run back to windows. Oh and also wine Fix over 10,000 bugs so he should try this fist.

---

### Post by snafu006 on 2013-11-15
Just because it not on wineHQ dose not mean its not going to work PFFFF!!!!

---

### Post by deadflowr on 2013-11-15
> [COLOR=#000000]So the only way to know is a terminal command or just right click you home folder and go to properties.[/COLOR]

That isn't very helpful.
But this might be
You can find the current status of the connected drives; or as the are actually known, partitions, by opening the program "system monitor" and clicking the tab "file systems".
You can also find out through the terminal using a simple command like
```
df -h
```
The partition you want to look at, would be the one marked with /.
Normally it'll be /dev/sda1.

As for the camcorder, I am not sure, but I guess what you want to do is stream through a vhs device, is that right?
If so, [VLC]("http://www.videolan.org/vlc/index.html") might work.
VLC is in the Ubuntu Software Center, so don't worry about looking around the internet for it, install it from USC, it'll make life easier in the long run.

Edit and Added: Ubuntu is an alternative, fully functional, operating system and as such, some programs which run great in Windows and Mac don't work well on it.
Since it is alternative to the normal, your best bet is to look toward alternative methods and programs.

---

### Post by QIII on 2013-11-15
> **snafu006 said:**
> And your answer it just going to get the dude to run back to windows.

Is there something wrong with Windows if that is the OS that will work for what the OP wants to do?  The OP is free to use whatever OS he chooses if it suits his needs.

---

### Post by Mark Phelps on 2013-11-15
I agree with Bucky Ball regarding Wine and the apps the OP wants to run.  

Checking the WineHQ site is always the first thing to do BEFORE struggling with Wine or POL.

Ans, it's very likely that neither app is going to work for the OP.

---

### Post by Bucky Ball on 2013-11-15
> **pomai said:**
>  I wanted to see like the properties of c drive to see how much space I have but still haven't found that yet.  


Open Gparted and that will show all drives, size, how much space used and available.

---


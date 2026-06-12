---
title: "ubuntu live CD boots successully to ........ a BLANK screen"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tenmoi on 2008-01-07
Please help! 

First my specs:
Main : Gigabyte GA M61P- S3
CPU: AMD athlon 64 x2 4000+
Ram: Twinmos 1024 x2
ASUS DVD drive (SATA)
hdd: Western SATA2 160 gigs
monitor: 8 year old viewsonic 14'

Problems:

the gutsy gibbon ubuntu live CD seems to boot successfully because I can hear the usual welcome sound. But I am always presented with a blank screen. I do a crt+shift+backspace and after a while hear the welcome sound again but still the blank screen. I do a crt+shift+f1 and can get to the console where I can work with no hassle whatsoever. But what I want is the graphical screen. 

this is really strange.

Many thanks.

P.S:

I  had same problems with ubuntu gutsy gibbon 32 bit live CD.
I have no problems with windows both 64bit and 32 bit.

I can boot with no problems using kubuntu 7.04:(

---

### Post by chammy on 2008-01-07
What video card is in your machine? I remember booting to blank screens on some earlier live discs with my geforce 8, but that bug's been squashed by now.

---

### Post by khensucat on 2008-01-07
Have you tried booting into "Safe Mode"?

---

### Post by Borbus on 2008-01-07
You forgot to list your graphics card. Even the newest live CD has a problem with my 8800GT. To get around it just for the installation, press F6 for extra options, delete the last two options.. (which are slash, and something else which I can't remember), and choose to boot into safe graphics mode.

---

### Post by njparton on 2008-01-07
Select safe graphics installation, press F6 and remove "quiet" and "splash" from the command line that pops up. Then press enter to start...

---

### Post by Borbus on 2008-01-07
That's it, "silent"... Actually you have to do it in the order I said, though. Selecting Safe Graphics Installation will immediately start the live cd without letting you change options.

---

### Post by njparton on 2008-01-07
Press the down key once, press F6, edit, THEN press enter :)

---

### Post by tenmoi on 2008-01-07
Wow! thanx !

in fact, it is an onboard geforce 6100.

And to njparton, you wrote: "Press the down key once, press F6, edit, THEN press enter "
I am sorry. I do not quite get you there: When do I press the key, and what am I supposed to edit? Thanx anyway.

P.S

And I did try the safe graphics mode. in short I have tried all options to no avail.

---

### Post by njparton on 2008-01-07
At the installation screen where you have the options for how to install (orange text on black screen with ubuntu logo at top) press the down arrow on your keyboard once to highlight safe graphics installation **(DON'T PRESS ENTER YET!!)**, press F6 and a command line will pop up at the botton of the screen.  Delete the words "quiet" and "splash" from this line, then press enter to install.

A lot of nvidia cards seem to have recently "lost the ability" to display the ubuntu splash screen which is why you're ending up at a black screen.

---

### Post by njparton on 2008-01-07
PS after doing the F6 bit and before you press enter, you could also press F4 and select the appropriate resolution for your screen.

If you can't follow the above or it doesn't work, download and try the alternate CD installation instead.

---

### Post by tenmoi on 2008-01-08
Many thanks to all of you.

Still, I haven't been able to make it boot properly. I'll try the alternate CD, perhaps.:guitar:

---

### Post by tenmoi on 2008-01-10
Hummmmm I have tried the ALTERNATE CD to no avail. Installation got stuck first time at 34%, second at 29 percent. 
The first time the machine had a network cable plugged in. The second time I removed it, suspecting that it might have been the culprit. But as I have told you. 

However, I won't be discouraged. I will wait till the next release. Now, perhaps, I should try fedora 8. 
................................................................................................................................................

:) JUST CANN'T LIVE WITHOUT LINUX

---

### Post by tylerspaska on 2008-01-10
i had this same problem with an ati graphics card. when you hear the boot sound go to the console and enter

```
sudo dpkg-reconfigure xserver-xorg
```

you can choose your graphics driver. i had to choose vesa instead of ati (maybe someone can correct me on this, but vesa seems to be a generic driver that 'works' but doesn't make the most of your graphics card). then you can fiddle with some of the other options. save the changes and use ctrl+alt+backspace to reset.

---

### Post by captaink on 2008-01-10
FYI, on my old GeForce 4 MX, I had the same problem with kubuntu and ubuntu 6.10 when dual-booting (!). When with a clean disk, no prob (!!).
I was always fixing the problem by installing with Alternate CD, then booting into recovery mode and installing Nvidia Restricted Drivers. And voila, using ubuntu, no probs.

Haven't tried editing the boot line, may be interesting...

---

### Post by tenmoi on 2008-01-30
Finally solved this problem. I used the Alternate CD and  added the following line to the boot line: 

install hw-detect/start_pcmcia=false.

And I learned this after two weeks!?

---


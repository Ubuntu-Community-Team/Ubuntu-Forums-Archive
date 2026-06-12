---
title: "firefox + maps.google = freeze"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by ZjosH on 2008-07-25
Hello,

I'm kinda new to linux, and I'm having the following issue with my ubuntu x64 8.04 installation. 

When I go to maps.google.com or maps.google.nl and zoom in 2 clicks, my whole system freezes. There is nothing I can do to get it unfreezed except for the reset button. I've done the following things to fix it, but they didn't work obviously.

Install Flash Block in firefox... Nothing.
Update Ubuntu to its latest version... Nothing.
Update Firefox to 3.0.1... Nothing

I left an mp3 running while I froze up the system, and it repeated like 200ms of the song constantly. 

And, my hardware is as follows,
Intel Q9450
Gigabyte EP35-DS3 
XFX Nvidia 9600GT XXX edition, Compiz fusion runs after I installed the restricted driver, freezes occured with and without compiz fusion and the driver. 
Linksys wireless network card, worked out of the box. Used on a WPA encrypted network. 

Hope you guys can help me with this :)

---

### Post by Sef on 2008-07-26
How much ram do you have?

---

### Post by ZjosH on 2008-07-27
I have 4 gig of ram... There is no problem with the pc itself, it runs fine with windows x64 installed.

---

### Post by ZjosH on 2008-07-29
I guess no one can help me with this strange problem. Is better to go to x86, maybe that doesnt have the freezing stuff?

---

### Post by schmitty2005 on 2008-07-29
I am having a very similar problem.  Firefox does a soft reboot into the login screen when certain web pages are accessed.  I did not have this problem with the 7.10 Ubuntu 32-bit version.  

I am running 64-bit now and it is a problem with 8.04 Ubuntu.

If I find a solution, I will post it here.   As of yet, it seems that nobody knows.  

It is problably a plug-in (java, flash, something) and firefox that is the cause.  I have not used a different browser to see if that fixes the problem.

Anyways, I remeber having Ubuntu 7.04 64 bit, having problems with it, and installing 7.04 32 bit and the problems disappeared.  

So, I think installing the 32 bit version will solve your problem.

---

### Post by ZjosH on 2008-07-30
My system wont soft reboot... I need to press the hard reset button. I think i will install the x86 version on my computer, and live with less memory.

---

### Post by philinux on 2008-07-30
> **ZjosH said:**
> My system wont soft reboot... I need to press the hard reset button. I think i will install the x86 version on my computer, and live with less memory.

I have no problems with those websites with my setup and running the cube.

One tip - to restart a frozen system use this.
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

To sort out FF try safe mode from a terminal to see if it's an addon that causing the problem.

```
firefox -safe-mode
```

Report back.

---

### Post by ZjosH on 2008-07-30
Ive yust installed the x86 version of ubuntu, and tried to go to the maps.google website... it failed, now im gonna try the things said above. Ill report back :)

Whats the cube btw?

Here I am again. The safe mode does help a bit, it didn't freeze in the first place, I could scroll all the way down to my home. But then I made some heavy movements with the scroll wheel, and the computer froze again. Then I tried to do the "raising elephants is so utterly boring" stuff... witch, after 1 minute didn't have any effect... I cant even toggle the lights on my keyboard with caps or numlock. Should that be possible, I have a Logitech Ultra X premium attached with usb.

Hmmm... this is kinda strange... It freezes every time, but when it freezes seems to depend on the size of the screen. If I use firefox windowed, it freezes later then when I use it full screen ( 1680 x 1050 ). At this time I don't have a video card driver installed, and thereby compiz fusion isn't enabled. My video card (9600gt) requires a special installation sequence, couse it isn't recognised by the standard drivers. Hope this helps you guys out!

---

### Post by philinux on 2008-07-30
The cube is the 3d cube you can use with compiz for switching desktops.

The reisub thing is best done by holding down the alt and printscreen buttons with your little fingers at the same time as typing r e i s u b
dont worry if the screen goes black just type it all in.

This sounds like a graphics card problem.

How are you installing the driver? Did you try the sites before you installed the driver?

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> The cube is the 3d cube you can use with compiz for switching desktops.

The reisub thing is best done by holding down the alt and printscreen buttons with your little fingers at the same time as typing r e i s u b
dont worry if the screen goes black just type it all in.

This sounds like a graphics card problem.

How are you installing the driver? Did you try the sites before you installed the driver?

The REISUB doesn't do anything, I hold down the right alt and printscreen button (the left alt is pretty unreachable), and type reisub, lowercase. Nothing goes black, there is just nothing happening. I don't see the hdd led flashing, nothing. 

At this moment there is no driver installed, The last time I installed the driver I did it according to some website. Where you needed to get the driver from nvidia and do some tricks in a terminal... The website I used seems to be offline, [http://www.adamspotton.com/node/1](http://www.adamspotton.com/node/1) The tutorial there worked for me, and got the driver installed. I couldn't see it in the restricted driver manager, but it worked, couse I could run compiz fusion with all great nice effects. The graphics card does run fine in windows, I've played numerous games of Supreme commander with it, and never failed on me.

---

### Post by philinux on 2008-07-30
It has to be the left alt key. use both little fingers.

Could be flash or java then me thinks.

Ok, what flash and java versions have you installed?

Did you install ubuntu-restricted-extras?

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> It has to be the left alt key. use both little fingers.

Could be flash or java then me thinks.

Ok, what flash and java versions have you installed?

Did you install ubuntu-restricted-extras?

I yust tried with the right alt, Didnt work eighter. I have no clue how to find out what versions of flash and java I'm using, and I will check if I installed the restricted extras after I've eaten... Ill report in a bit :)

---

### Post by philinux on 2008-07-30
> **ZjosH said:**
> I yust tried with the right alt, Didnt work eighter. I have no clue how to find out what versions of flash and java I'm using, and I will check if I installed the restricted extras after I've eaten... Ill report in a bit :)

Has to be the LEFT alt key the right one is Alt Gr not the same thing.

In firefox Tools>Addon >plugins tab. Maximise the window take a screenshot and post it here.

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> Has to be the LEFT alt key the right one is Alt Gr not the same thing.

In firefox Tools>Addon >plugins tab. Maximise the window take a screenshot and post it here.

By right alt I meant the good one, so the left one... srry for the confusion. Even when I press the left alt and print screen button, and the sequence, it doesn't work... I don't see anything happening. 

The ubuntu-restricted-extras are not installed.

I took a screen shot of the required tab, its in the attachments.

---

### Post by philinux on 2008-07-30
Ok so no flash/java installed and you're getting hard freezes.

It's hard but you have to hold those keys down while you type the reisub.

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> Ok so no flash/java installed and you're getting hard freezes.

It's hard but you have to hold those keys down while you type the reisub.

Yea, I did... I've tried multiple times now. I can browse these forums without problems tho. Any Ideas left about what is wrong? I can always post other files you guys might need.

---

### Post by philinux on 2008-07-30
This is a completely fresh install right. Have you home on it's own partition or did you install to whole disk thereby creating a new home with no user data or old config files?

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> This is a completely fresh install right. Have you home on it's own partition or did you install to whole disk thereby creating a new home with no user data or old config files?

It is installed on a Windows harddisk with wubi. It created its own virtual drive by creating a big 8 gig file. The Windows harddisk is formatted NTFS and there should be no old config or data files. The only files which are old can be reached through the host folder. I can reach the files of my windows installation through that. 

Previously I had it installed on another harddisk, but that made no difference, and I want it to be a pure data drive.

---

### Post by philinux on 2008-07-30
Ok i think wubi might be the problem. Cant think what else it could be.

Download and burn a livecd. [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Run the live cd, this does not install just lets you test.

Then try firefox from the live cd.

I'd make a post in here [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

Or click the report button on your first post and ask the mods to move it to the wubi forum.

---

### Post by ZjosH on 2008-07-30
> **philinux said:**
> Ok i think wubi might be the problem. Cant think what else it could be.

Download and burn a livecd. [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Run the live cd, this does not install just lets you test.

Then try firefox from the live cd.

I'd make a post in here [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

Or click the report button on your first post and ask the mods to move it to the wubi forum.

Ok, thanks for the help, I will try the stuff you just said.

---

### Post by ZjosH on 2008-07-31
I have tried to run the live CD, and then go to maps.google.com, and the computer still froze. I have absolutely no clue what so ever what is wrong. I will post my full hardware specs, so you guys can see what im working with.

Gigabyte EP35-DS3
Intel Q9450
Kingston Value Ram 2x2 Gigabyte
XFX 9600GT XXX edition
320 Gig Samsung Spinpoint T166 Harddrive (sata)
750 Gig Samsung Spinpoint F1 Harddrive (sata)
Samsung Sata DVD rewriter
Linksys WMP54G
USB Logitech Ultra X Premium
USB Logitech MX518
Samsung SyncMaster 226BW

This sums it up realy. The Linksys is connected with a WPA encrypted network.

---

### Post by ZjosH on 2008-08-01
I have some progress...

I'm posting this from the 8.10 live cd :-D and it doesn't have problems with maps.google.com or .nl... I've zoomed all the way in and out, I can see the lawn of my house and it still didn't crash! Now, the 8.10 release... its more unstable I guess.. becouse its still a beta... but It seems to be more stable on my computer. Can I use this, or should I try and figure out what is wrong with 8.04.1?

I've tried to install 8.10 Alpha 3 with Wubi, and it fails. It say's invalid disk when I mount it in windows, and when I run the wubi application on the cd and it installs the 8.04 editon in some weird way :S

---

### Post by kwlyon on 2008-09-22
Here's a strange one:  I'm a windows xp pro user who has been experiencing this exact problem for many months now.  To wit: From fire fox (previous version or most recent version), go to google maps and being to use the mouse wheel to zoom in & out, and get a total freeze every time.  By "freeze" I mean that the screens (I have 2) remain as is, but there is nothing I can do other than hold down my power button or pull the power cord to reset the pc. 

I know nothing about ubuntu, so I don't know how to duplicate your apparent fix on my pc, but if you have any ideas as to what the cause or solution might be, I'd sure like to hear them!\

Ken
[email]ken@lyonhouse.us[/email]

---


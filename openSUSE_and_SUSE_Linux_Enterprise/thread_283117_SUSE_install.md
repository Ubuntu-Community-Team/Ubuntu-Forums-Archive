---
title: "SUSE install"
date: 2006-10-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by drifterx on 2006-10-23
I am currently using Ubuntu, but I would like to install SUSE linux on my laptop. I can seem to figure out how to run the CD in Ubuntu or boot from the CD. If any can help me to try and install it, any information would be helpful.

---

### Post by Kateikyoushi on 2006-10-23
When the laptop starts press F2, F12 or delete to enter bios there change the boot order to boot first from the cd drive.
Next time you start it with the cd in the drive it should boot suse.
In case the disc is burned correctly.

---

### Post by taurus on 2006-10-23
If you want to install SUSE on your laptop, just download the OpenSUSE, [http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org), burn it, and boot from it.  Then, just follow the instructions on the screen.  It's as easy as 1-2-3!  ;) 

And by the way, I will move this over to OpenSUSE section since it's an SUSE question...

---

### Post by drifterx on 2006-10-23
I have the CD's for OpenSUSE, I just don't understand how to boot from the CD (note: I'm not using windows, I don't have windows on this laptop, I'm trying to install from Ubuntu), I dont see the BIOS option, I tried F2, F12, and delete at startup and nothing came up, the only menu I see is before Ubuntu loads, Grub loads and it gives me the option to press Esc before startup, and it takes me to a menu allowing me to choose a list of Ubuntu's to boot from, and to change various other things, but no boot options. I will continue trying, and thank you for moving my thread to the correct forum, and any other help will be appreciated.

---

### Post by taurus on 2006-10-23
What brand and model is your laptop?  Sometimes, you have to press the "del" key to get into your bios.  If you have a manual, look for it; otherwise, you can search about BIOS on the manufacture's site.

---

### Post by drifterx on 2006-10-23
Nevermind I got it to work. But now when I'm at the installation at the section of "Installation Settings" under "Software" there is an error.
 
No catalog found at 'cd:///?devices%3d%2fdev%2fhdc' 

ERROR: No proposal.

I can assume there is a problem with a disk and I can burn my own (I borrowed them from a friend) but I don't want to waste time when there is possibly another solution. I'll start the DL of OpenSUSE anyway just to make sure.

---

### Post by mmmichael on 2006-10-23
I recently picked up an old toshiba laptop. On this model, holding down "esc" while the machine powers on gets you into bios setup, where you can change the boot order. Might as well give it a try...

---

### Post by drifterx on 2006-10-24
I have gotten SUSE install, but during the initial installation, the system reboots after the first CD, saying it is done with the basic installation. I am able to update disc 2 and 3 afterwards, but there is a problem. SUSE is installed but since it reboots prior to the installation of Disc 1, I am not able to create a computer account, and I have not been able to get to the "configuration" section. Is there any thing wrong? Is there a default username for SUSE? Any help would be appreciated.

---

### Post by funkyade on 2006-10-24
I tried SUSE on a older laptop a while ago - just so I could have an rpm based distro somewhere and ran into similar bugs. It seems to come and go, I did get it installed in the end but I had to download the development version net install (the mini CD version)... You will need an internet connection available for the laptop if you go down this route.

---

### Post by drifterx on 2006-10-24
So how did it work in the end? When you mean the mini-CD version you mean the 1 CD version? I want SUSE on my laptop permanently, and I don't think it works permanently. I also would like the full KDE experience, and add other stuff so the 5 Disc version (I assume) is better for me.

---

### Post by funkyade on 2006-10-24
> **drifterx said:**
> So how did it work in the end? When you mean the mini-CD version you mean the 1 CD version? I want SUSE on my laptop permanently, and I don't think it works permanently. I also would like the full KDE experience, and add other stuff so the 5 Disc version (I assume) is better for me.

The net install version is the same as the full install. It just uses the internet YAST repositories to download the packages it needs during the install, that way you don't need to have five CDs. The installation will be as permanent as you like.

It is easier, imho, to use a net based install as when a new version comes out you only need to download and burn a small CD image of about 100Mb instead of several Gb of isos... You can then choose exactly the packages (eg KDE) you want without having a load of other junk installed along with it (SUSE is notorious for that, btw...)

** You need to find out the IP address of a SUSE mirror BEFORE you commence with the install as you will not be able to install without it. **

hth

---

### Post by ice60 on 2006-10-24
hi, the remastered suse cds/dvd came out recently, maybe it would be better to install that??

you can find out where to get them at freenode #suse :)

---

### Post by drifterx on 2006-10-25
I finally got it working, thnaks for all of your help. There is still a problem. I was doing something that eventually required me to do a console login, and now when I restart my computer it takes me to the console and I never get to the desktop or anything, I'm stuck at the console, I've logged in but don't know the command to get to the desktop.

---

### Post by igknighted on 2006-10-27
```
startx
```
 or
```
init 5
```
Either one of these should do the trick, if xserver crashes you probably have a problem with xorg.conf.  If you used the 10.2 beta I know they use X.org 7.2 and the current graphics drivers wont accept this, for 10.1 it could be any number of things, you'd have to give more details.

---


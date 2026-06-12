---
title: "How-To Install Guild Wars on Ubuntu 8.04"
date: 2008-06-15
forum: Wine
---

### Post by Kidfork on 2008-06-15
Installing Guild Wars on Ubuntu Linux 8.04 Hardy Heron
Introduction
This guide will show you how i installed Guild Wars on Ubuntu. Now im not going to sit here and explain all the boring stuff about it. Im just going to show you! The reason im doing this is because i noticed when people try to install Guild Wars from the disc it will load to 100% then just hang.

How-to-install

OK the first thing we need to do is install Wine.

sudo apt-get install wine

Ok after we have installed wine we must conigure it, type :

winecfg

Set the windows version to 98 (Alot of people have said guild wars works best on 98, its owrks fine on XP or 2000 for me, just dont put it on Vista.

Ok close the Wine Configuration. Now we need to install a front-end for guild wars that will make it easier for You to install Guild Wars and generaly all games on Ubuntu.

System>Administrator>Synaptic Package Manager

In search type
"Playonlinux"

Install that now in command line run:

sudo apt-get install playonlinux

Before we start installing the Actual game we need to make sure our drivers are correct. Now if u have an external video card NO DOUBT you need to do this. But its best if you do it anyways. I have an external one and one built into the motherboard, it used the motherboard one which was only 16MB and no doubt this game didn't work right. So to fix this little annoying problem you must do this.

Goto
System>Administration>Hardware Drivers.
Make sure the graphics card u want is checked and the status is "IN USE"

Ok so now that the graphics card is configured for sure we need to set our graphics to Extra. So:

Right click on desktop>Change desktop backround>Visual Effects
Now set it to "EXTRA" now when you do this the computer will freeze for about 5-10seconds then everythign should go back to normal.

After thats finished we need to get the download client. Type these commands in order:

wget [http://www.guildwars.com/downloads/gwsetup.zip](http://www.guildwars.com/downloads/gwsetup.zip)

unzip gwsetup.zip

wine GwSetup.exe

From there just run the installation and guild wars should start up right after it automaticly! It should create a Desktop Icon. But if it doesn't its located in
Applications>WINE>Programs>Guild Wars

Thanks for reading, if theres any problems just post a comment and ill answer A.S.A.P

---

### Post by cogadh on 2008-06-15
2 questions:
Why did you install PlayOnLinux if you don't actually use it for the install?
Why did you enable extra desktop effects (that actually degrades gaming performance, especially with Wine)?

EDIT - Plus one minor comment. While you definitely do need to install the restricted drivers for your video card, the "on-board video card conflicts with an off-board video card" problem would be a non-issue from the start if you just disable the on-board device in your BIOS.

EDIT 2 - Another minor comment. You didn't specify a Wine version to install. If you take a vanilla Ubuntu installation and run "sudo apt-get install wine", you will get an out of date version of Wine, rather than the latest version of Wine, which currently has a Platinum rating running GW on Hardy. You should still get good results with Hardy's default Wine, but you are likely to get better results with the most current version.

---

### Post by Kidfork on 2008-06-15
I installed playonlinux because when i had a hard time installing Guild Wars i read someone about "Playonlinux" i installed it and Guild Wars installing worked!

---

### Post by cogadh on 2008-06-15
I just noticed something else: 
> sudo wget [http://www.guildwars.com/downloads/gwsetup.zip](http://www.guildwars.com/downloads/gwsetup.zip)
You don't need to use sudo to download the client. In fact, using sudo makes the downloaded file belong to root, instead of your user. It doesn't prevent you from extracting or installing the client, but it does make it a little more difficult to delete the client installer when you don't need it anymore.

Plus, one other thing I should have brought up before, PlayOnLinux is not in the Ubuntu repositories, so just running "sudo apt-get install playonlinux" will not get you anything. If you add the PlayOnLinux repositories to Ubuntu first, then run that command, it will install.

---

### Post by Kidfork on 2008-06-15
> **cogadh said:**
> I just noticed something else: 

You don't need to use sudo to download the client. In fact, using sudo makes the downloaded file belong to root, instead of your user. It doesn't prevent you from extracting or installing the client, but it does make it a little more difficult to delete the client installer when you don't need it anymore.

Plus, one other thing I should have brought up before, PlayOnLinux is not in the Ubuntu repositories, so just running "sudo apt-get install playonlinux" will not get you anything. If you add the PlayOnLinux repositories to Ubuntu first, then run that command, it will install.

Well sudo is super user. I figured it works better, guess not.

---

### Post by cogadh on 2008-06-15
"sudo" is just a command add-on that gives the command root permissions, which you only really need to do system-wide functions, like installing or removing updates, changing the system configuration or modifying system files, mounting and unmounting some drives, etc. For normal user operations, like downloading files or using Wine, sudo is not needed at all and using will often lead to problems.

---

### Post by buntunub on 2008-06-15
Good intentions behind this post. However, the incorrect information in it makes it more of a hazard than a help for newbies. I recommend that if your going to post another guide, make sure that you research all your info first. Good job on the effort. More guides are definitely needed for Linux, but guides that are technically accurate.

---


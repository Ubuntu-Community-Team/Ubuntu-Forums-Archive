---
title: "X problems with Breezy on G3 iMacs"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by rquint on 2005-10-27
After an apparently unsuccessful install of Ubuntu 5.10 on an old G3 iMac (a Blueberry 500 MHz model) I've done some searching of the Ubuntu forums and Google and have discovered that several people have had similar if not exactly the same experience.  There is something wrong with the xorg.conf script and/or a failure to install some needed files (lsmod errors flash by during boot up).  I can eventually back out of gdm and get a terminal in which things seem to work okay, including the the ability to edit xorg.conf.  However I am not knowledgeable enough to know what I should change nor where to find and place the missing files. 

I had a working version of Hoary running on the same machine, but, since it is just for play, I overwrote it with Breezy.  I can go back, install Hoary and do an update rather than a fresh install of Breezy, but that would mean moving the iMac to a location where there is a high speed internet connection rather than its dialup connection.

Anyone have any success with a Breezy install on one of these old iMacs or know what to do?

TIA
Richard Quint

---

### Post by Peter76 on 2005-10-27
try sudo dpkg-reconfigure xserver-xorg, maybe that helps. Good luck

---

### Post by pvz on 2005-10-27
See this thread:
[http://ubuntuforums.org/showthread.php?t=82517](http://ubuntuforums.org/showthread.php?t=82517)

I would give editing refresh rates in xorg.conf a try. On my iMac G3 600
horizontal: 60-6 and vertical: 43-117 did the trick.

---

### Post by rquint on 2005-10-27
Still no joy.  Running dpkg-reconfigure xserver-xorg guided me through an edit of my xorg.conf file, but none of the changes (including just modifying the vertical and horizontal sync settings) I tried worked.  Each time the result was no X server.  The iMac is still okay since I'm writing this using a 5.04 live CD.  

If anyone else has the same problem I'd appreciate hearing from you.  The more of us the more likely someone who knows what to do my be able to figure out what's wrong.

---

### Post by dinoj on 2005-10-28
You can try to edit manualy your xorg.conf file, and put correct refresh rates. 
Also please check about correct driver - I have boot from live 5.10 version, and find that xorg.conf is try to use vesa driver, and manualy I set to use ati. 
Here is my part of my xorg.conf file:
Section "Device"
        Identifier      "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
        Driver          "ati"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "iMac"
        Option          "DPMS"
        HorizSync       60-60
        VertRefresh     75-117
EndSection

The other thing you can try to get xorg.conf from hoary (from live cd or form old instalation) and replace the file from breezy.

---

### Post by rquint on 2005-10-30
Thanks everyone.  I'm afraid the problem is something deeper.  I changed the Horizontal synch and vertical refresh rates and have had no joy.  The rest of xorg.conf looks the same as it did under Hoary. The iMac boots at a normal rate until gdm screen comes up.  I can enter my user name and password but then it's is as if I have entered a time warp.  The Gnome desktop comes up and is working but every thing takes forever, e.g., click on  Applications on the panel and move the cursor down and it can be over a minute until the movement shows on the Desktop.  Everything eventually works but at a less than glacial rate. 

Richard Quint

---

### Post by rquint on 2005-10-30
A bit more info on my problem with installing Breezy on a 500MHz translucent iMac.  Something appears to happened after Hoary's combination of Gnome 2.10 and the 2.6.10 kernel.  I tried installing Fedora Core 4 (it has the 2.6.11 kernel) and had the same problem with the behaviour of Gnome (everything happens in ultra slow motion, tens of minutes in place of seconds).  Reinstalled Hoary and the machine acts normal again.  I can stay with Hoary, but the iMac is just for play with cutting edge stuff and there is something wrong with itand two newer distros.  Anyone have any ideas on how to pin down the problem?  Can it be a particular hardware configuration that has this problem?  There has always been a boot time error message about the ATi video card's signature.

I'll take a look in the non ppc forums to see if this has happened with any PCs too.

---

### Post by bigbadben on 2005-10-30
[QUOTE=rquint](everything happens in ultra slow motion, tens of minutes in place of seconds).  Reinstalled Hoary and the machine acts normal again. [/QUOTE]
  

It wont help!
But same problem here...5.04 works good. but 5.10(kubuntu or ubuntu) is slowmotion...
I did some testing and here are my result.....nothing very spectacular but interessting.


I did a perfect install of kubuntu 5.10 on my imac 500mhz 1 gig sdram.
At login window. everything is in slowmotion(very slow).
Its so slow i cant login.


so! has im new with linux and i did not have success with the (ubuntu or kubuntu) software! I decided to try yellow dog linux(btw it was wort)it always failed to install. any kind of install.
anyway.
Now! to get to the interresting part of it.
on the yellow dog install cd at boot.
You have the choice of install, safe install and (LINUX) and more!
 
So here is the test i did!
I install ubuntu or kubuntu(tried both for test) version 5.10.
Has usual, everything was slow.
So.
I did a startup after my success install of ubutu kubuntu, WITH the yellow dog linux install cd(and pressing c)to make like another install.
at boot:
I put linux to tell the kernel to start linux instead of installing.
Wow!
kubuntu or ubuntu started fast, login fast, and gnome or kde destop came fast. The only problem was the sever wasint running, and no sound support.
Anyway.
I think i had some fun result....
5.10 was not usefull with no server or sound but it was fun to see it work fast..
lol
anyway(again)
i did a complete install with hoary 5.04, and i have no problem at all..
Dont know if all this information will help devloppement for next version.
but ther is something not right with breezy.

---

### Post by rquint on 2005-11-01
OK, I think I have found the cause of the problem, but not the perfect solution. Something has changed in X (or the gcc compiler) that causes problems with using DRI. (There has been traffic on this subject in forums for other distros.)  If I don't load the dri module, gdm and the Gnome desktop come up.  I can't tell if there is any loss of speed from 5.04 since I haven't started using the iMac to do anything.  I also noticed there is a new module GLcore loaded in xorg.conf, but I don't know what that does yet.

---

### Post by yesterdaytoday on 2005-11-05
[QUOTE=rquint]OK, I think I have found the cause of the problem, but not the perfect solution. Something has changed in X (or the gcc compiler) that causes problems with using DRI. (There has been traffic on this subject in forums for other distros.)  If I don't load the dri module, gdm and the Gnome desktop come up.  I can't tell if there is any loss of speed from 5.04 since I haven't started using the iMac to do anything.  I also noticed there is a new module GLcore loaded in xorg.conf, but I don't know what that does yet.[/QUOTE]
I had the same problems loading 5.10 on an Imac G3 400 mhz lime flavored.
everything worked but the display, (xorg) and tweaking did not help. I had tried live ppc and install ppc.  Just a blank screen...But when I rebooted and chose install PPC expert, which I am not, I was not asked any questions regarding the video card or display and it booted right into the login screen no problems. Hope this helps, just remember to write down your identity, your user name and your passwords.

---

### Post by Tunnelrat81 on 2005-11-18
Just wanted to ask if anyone had made any headway on this problem as I seem to be experiencing the same thing as 'rquint' is.  I'm using a G3 powerbook pismo 500 Mhz 128 Mb Ram. The only difference that I can see between what you've described and what i'm experiencing is the lack of success with the hoary live cd also.  I load up the live cd, and everything goes great until the actual gdm loads up and things slow WAY down to a lack of functionality.  I can sometimes get the pull-down menus to show, but can't open anything.  I've gone through the live-expert setup for both the breezy and hoary live cd's with the same result.  Setting up the graphics driver with the appropriate ati drivers etc....doesn't seem to do anything.  After a painfully long gdm loading process, I get the desktop, piece by piece, followed by continued work by my cd drive until minutes later I get error messages about my "WirelessApplet" and "NotificationareaApplet" not being able to open, prompting me to decide whether to delete them from my configuration etc..  I have a working install of OSX running currently that I don't want to alter, so trying a real install is presently out of the question.  I use this computer simply as a portable dvd player and music hub, but would love to make it a mobile workstation for linux as well.  I recently made the switch to ubuntu on my desktop pc with success, so I'm a noob, but understand some of the basics.

Edit: With a bit more patience, I have been able to run functions, but at the same amazingly slow speed.  Being that I'm running with the live cd (how do you get root privileges while running a live cd?) I'm limited in what I can do.

-J

---

### Post by pandan on 2005-12-14
How big is your Linux root partition?

I have a tray loading iMac G3 with 333Mhz and 96MB RAM.
I got ubuntu to install with 'expert' mode only.
I have to choose expert so I can get a root password.  Somehow sudo wasn't working and I have to "su root" to do any of the administration menu stuff.

My linux root partition was 3GB, smaller might be a problem.  I skipped
the install step "copy remaining files to hard disk" and promptly re-inserted the
CD after reboot.

---

### Post by linear on 2005-12-14
[QUOTE=Tunnelrat81]I load up the live cd, and everything goes great until the actual gdm loads up and things slow WAY down to a lack of functionality.  I can sometimes get the pull-down menus to show, but can't open anything.[/QUOTE]
Have you tried disabling DRI in xorg.conf?

---


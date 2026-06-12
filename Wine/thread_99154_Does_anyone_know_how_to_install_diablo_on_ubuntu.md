---
title: "Does anyone know how to install diablo on ubuntu?"
date: 2005-12-05
forum: Wine
---

### Post by muzz on 2005-12-05
Does anyone know how to install diablo on ubuntu?i wud like to play it

---

### Post by jasay on 2005-12-05
1 or 2?

I've never gotten 1 to work, but I haven't tried very hard <5 minutes.

For 2:

Make sure you have video drivers installed: [ati]("http://www.ubuntuforums.org/showthread.php?t=75378"), I'm not up to date on the NVidia drivers since I don't have one, do a search.

Make sure you have the latest wine (0.92).  ```
sudo gedit /etc/apt/sources.list #gnome
sudo kwrite /etc/apt/sources.list #kde

```and add this line at the bottom.```
deb http://wine.sourceforge.net/apt/ binary/
``` Save, then ```
sudo apt-get update
sudo apt-get install wine
```
Put in the installation cd and run, but change /path/to/cdrom to your cdrom path, something like /media/cdrom```
wine /path/to/cdrom/setup.exe
```That *should* bring up the installer program, run thourgh it as normal.  I find it helpful to have the disk mounter panel applet or some other way to quickly mount/unmount/eject cd's.  Download the latest update patch from [http://www.blizzard.com/support/?id=msc0387p]("http://www.blizzard.com/support/?id=msc0387p") and put in the in the Diablo directory (usually something like ~/.wine/drive_c/Program\ Files/Diablo\ II) and run ```
wine D2Patch_111b.exe
```Hopefully you now have an updated install.  When you start the game it will search for your cd and (at least a few months ago) wouldn't find it, so I downloaded a no-cd cracked version of the Game.exe file from [http://www.megagames.com/cracks/html/c31040_2.htm]("http://www.megagames.com/cracks/html/c31040_2.htm")I renamed it to Game_crack.exe and put in the the Diablo directory.  Then I made a blank file called D2.sh (gedit D2.sh) and put this code in the new file```
#!/bin/sh
mv -f Game.exe Game1.exe
mv -f Game_crack.exe Game.exe
wine "Game.exe" &
sleep 2
mv -f Game.exe Game_crack.exe
mv -f Game1.exe Game.exe
exit
```  This starts the game with the cracked exe to get past cd autodetection and then changes back to the real exe so you can play online.  Now make it executable ```
chmod a+x D2.sh
``` Now we set up wine preferences for Diablo```
winecfg
```
Click "Add application" and find Game.exe.  Change the windows version to Windows 98.  Make sure the audio driver under the audio tab matches the one you actually use (For gnome: Gnome Menu > System > Preferences > Multimedia system selector).  I use ALSA with no problems.  Under graphics tab I turned off double buffering and put vertex shader support to none, but you should experiment to find the best settings for you.  I think that's everything. Cd to the diablo directory and run ./D2.sh or make a launcher pointing to it to play.  

Most of the credit must go to Frank of [Frank's Corner]("http://frankscorner.org/index.php?p=diablo2").

---

### Post by muzz on 2005-12-05
david@Muzz:~$ sudo gedit /etc/apt/sources.list #gnome
Password:

david@Muzz:~$
david@Muzz:~$ deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
bash: deb: command not found
david@Muzz:~$ deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
bash: deb: command not found
david@Muzz:~$ sudo kwrite /etc/apt/sources.list #gnome
sudo: kwrite: command not found
david@Muzz:~$ deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
bash: deb: command not found
david@Muzz:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [2 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [Working]                                                        502kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 3B in 6s (0B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3) 86/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3) 86/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
david@Muzz:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate
david@Muzz:~$ wine /path/to/cdrom/setup.exe
bash: wine: command not found
david@Muzz:~$
david@Muzz:~$
that is what it said when i put in that stuff you said to????

---

### Post by DariusTriplet on 2005-12-05
In place of "/path/to/cdrom/" put the actual path to the CD-ROM drive (e.g., /media/cdrom/setup.exe)

---

### Post by jasay on 2005-12-06
Sorry I may not have been very clear.  ```
sudo gedit /etc/apt/sources.list 
``` should open the file "sources.list" in a text editor.  Copy and paste the repository info there.  Save the file, then```
sudo apt-get update
sudo apt-get install wine
```And like DariusTriplet said, make sure you use the correct path to your cdrom when you run wine(they're different on different computers, but /media/cdrom or /media/cdrom1 are common.)

---

### Post by anil_robo on 2005-12-06
[quote=jasay]
Make sure you have video drivers installed: [ati]("http://www.ubuntuforums.org/showthread.php?t=75378"), I'm not up to date on the NVidia drivers since I don't have one, do a search.[/quote]

I do not have NVidia - I have intel graphic chipset (915). I did exactly according to what you wrote, but it says:

**Error 22: A critical error has occurred in initializing directdraw.**

What should I do now?

[quote=jasay]When you start the game it will search for your cd and (at least a few months ago) wouldn't find it, so I downloaded a no-cd cracked version of the Game.exe file from [http://www.megagames.com/news/html/patches/d.shtml]("http://www.megagames.com/news/html/patches/d.shtml")I renamed it to... [/quote]

This link is not for nocd crack. The correct link is [http://www.megagames.com/cgi/download/download.cgi?action=search&category=cracks&search=FDX2109.ZIP](http://www.megagames.com/cgi/download/download.cgi?action=search&category=cracks&search=FDX2109.ZIP)
ALternate link: [http://gokservers.com/pcgamefixes/FDX2109.ZIP](http://gokservers.com/pcgamefixes/FDX2109.ZIP)

---

### Post by jasay on 2005-12-06
[QUOTE=anil_robo]What should I do now?[/QUOTE]I'm not an expert by any means, but I've never had trouble with mlomkers ati guide.  You might ask on that thread, a lot of people have gotten help there.

> 
This link is not for nocd crack. The correct link is [http://www.megagames.com/cgi/download/download.cgi?action=search&category=cracks&search=FDX2109.ZIP](http://www.megagames.com/cgi/download/download.cgi?action=search&category=cracks&search=FDX2109.ZIP)
ALternate link: [http://gokservers.com/pcgamefixes/FDX2109.ZIP](http://gokservers.com/pcgamefixes/FDX2109.ZIP)Whoops, you are correct, my apologies, thanks for pointing that out.

---

### Post by e2k on 2005-12-11
I have a strange problem.. I've installed wine and configured it, everything fine, but when I try to install d2 with wine /media/cdrom0/install.exe (or setup.exe), I get a windows-like window that says "Please insert the disc labelled Install Disc" even though that is the one I'm using? I've also tried using the Play Disc and Cinematics Disc to install (just to be sure :P) but they didn't work either (naturally).. Why am I getting this error?

---

### Post by jasay on 2005-12-11
Hmm.  I wonder. . . some companies put hidden files on cd's (the setting of which is completely ignored by windows and seen as normal files) that mess over wine.  You might try running ```
sudo gedit /etc/fstab
```and adding "unhide" as an option on your cd drive in /etc/fstab.  This makes hidden files on cd's visible.  Mine looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda2       /media/windows     ntfs   umask=0222         0       0
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,unhide     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,unhide     0       0

```

---

### Post by e2k on 2005-12-11
[QUOTE=jasay]Hmm.  I wonder. . . some companies put hidden files on cd's (the setting of which is completely ignored by windows and seen as normal files) that mess over wine.  You might try running ```
sudo gedit /etc/fstab
```and adding "unhide" as an option on your cd drive in /etc/fstab.  This makes hidden files on cd's visible......[/QUOTE]I edited fstab and rebooted, tried again, but unfortunately got the same error.. After clicking Cancel twice, I get this message:
```
Setup was unable to read the following data file.
Your Diablo II CD may not have been in the CDROM drive.
            setupdat\setup.vis

Installation aborted.
```
Am I supposed to have a setupdat folder on my Install disc?
```
$ ls -a /media/cdrom0/
.            binkw32.dll   dsetup.dll    d2data.mpq    d2speech.mpq  setup.exe
..           diabloii.ico  dsetup16.dll  d2readme.htm  extras        setup.mpq
autorun.inf  directx7      dsetup32.dll  d2sfx.mpq     install.exe   support
```I don't seem to have one.. :shock: This shouldn't be the case though, since I've successfully installed it on my other computer (on windblows though)

---

### Post by jasay on 2005-12-11
Hmm.  I just tried reinstalling to see if I could recreate your error and I got it too.  I wonder if something has changed in wine since I last installed Diablo with  wine 0.90.  I'll keep looking for ya, but I'm about out of ideas (only have ~6 months of linux under my belt, so I don't claim to know much).

---

### Post by jasay on 2005-12-11
Shot in the dark . . . You might try "winecfg", go to the "drives" tab and hit autodetect.  Then apply and try to install now.  I seem to be able to get to the install now.

---

### Post by anil_robo on 2005-12-11
I did that - winecfg. Selected autodetect drives. Also selected automatic label and serial finding. Selected the /media/cdrom0 as "CD-ROM DRIVE". the game detects it, but now there's a DIRECTDRAW error (no. 22)

---

### Post by jasay on 2005-12-12
Never seen that one.  When does it come up? During install, afterwards?  If you can install what did the video test say?

---

### Post by anil_robo on 2005-12-12
Install goes fine. WHen I run the game, it asked for CD initially (which I put in drive) but kept asking. This was solved by applying latest patch (11.1b) from blizzard site.

Vidtest said "YOU CANNOT RUN DIABLO! No video adapters found on your computer"! Makes me speechless :-#
And frustrated! #-o

---

### Post by johnsorc on 2005-12-12
All right, I followed the instructions and everything appeared to work.  I passed the video test, updated, and created the nocd crack just fine.  when I run ./D2.sh, I receive a little box saying: Unhandled Exception: Access_Violation (c00000005).

Any thoughts?  BTW, thanks for the indepth steps, they really helped!

---

### Post by e2k on 2005-12-12
[QUOTE=jasay]Shot in the dark . . . You might try "winecfg", go to the "drives" tab and hit autodetect.  Then apply and try to install now.  I seem to be able to get to the install now.[/QUOTE]Thanks, this fixed it! Now I got the installer up and running, installed D2 successfully, but while installing LOD it crashed at about 50%.. Had to restart X (couldn't even get the cd unmounted). Tried to install it again, but the installer thinks it's allready installed.. :???: Tried to uninstall D2 with $ wine ~/.wine/drive_c/windows/DIIUnin.exe but got a segment fault (or something like this, in a wine-window though)

I think I have to reinstall wine and try to install D2 over again :) But thanks for your help!

---

### Post by jasay on 2005-12-12
[QUOTE=anil_robo]Install goes fine. WHen I run the game, it asked for CD initially (which I put in drive) but kept asking. This was solved by applying latest patch (11.1b) from blizzard site.

Vidtest said "YOU CANNOT RUN DIABLO! No video adapters found on your computer"! Makes me speechless :-#
And frustrated! #-o[/QUOTE]
Just looked back at your previous post and realized I sent you on a wild video card driver goose chase.  I think the driver you want is i810.  Here's what synaptic says:```
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.
```  The problem is, I'm not sure how you specifiy that driver in xorg.conf. Try this, run ```
sudo dpkg-reconfigure xserver-xorg

``` and select i810 from the driver list.  Defaults should mostly work after that unless you know of anything specific to your computer that would be different.

---

### Post by anil_robo on 2005-12-21
[quote=jasay]Just looked back at your previous post and realized I sent you on a wild video card driver goose chase. I think the driver you want is i810. Here's what synaptic says:```
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.
``` The problem is, I'm not sure how you specifiy that driver in xorg.conf. Try this, run ```
sudo dpkg-reconfigure xserver-xorg

``` and select i810 from the driver list. Defaults should mostly work after that unless you know of anything specific to your computer that would be different.[/quote] 
I did that (sudo dpkg-reconfigure xserver-xorg) and chose the options given to me. Restarted. But it messed up with everything! Even planetpenguin racer game stopped working! So I booted off livecd, and copied that default xorg.conf file to hard disk, and now things are back to normal.

Normal=Planet Penguin Racer flies smoothly, Diablo2 gives error22.

:( ](*,) [-o<

---

### Post by Qharos on 2008-02-23
> **jasay said:**
> Shot in the dark . . . You might try "winecfg", go to the "drives" tab and hit autodetect.  Then apply and try to install now.  I seem to be able to get to the install now.


I don't mean to necromancer this thread, but having this issue was solved by the above. Thanks much!

---

### Post by Chipter on 2008-02-23
Just like to say thank you for this thread.
I'll be installing D2 on my computer as soon as I get home.

Can you play on Battle.net (online) through Wine or does Battle.Net think that Wine is a third-party hack-program and boot you off?

---

### Post by uberlube on 2008-02-23
Im almost positive that Diablo 2 runs in Wine. I have played WoW, Warcraft 3, Starcraft through wine as well.

---

### Post by uberlube on 2008-02-23
Battle.net worked for me on Warcraft 3 as well.

---

### Post by Rithmarin on 2008-04-04
The simplest instructions I've seen are on wine's website - see link
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=315&iTestingId=22633](http://appdb.winehq.org/objectManager.php?sClass=version&iId=315&iTestingId=22633)

I had to set up a profile for the game in winecfg and switch off window integration so that the desktop panels would disappear, but the rest has worked out the box for me including patching up to the current v1.11b

I'm using Hardy beta which comes with wine v0.9.58, nvidia drivers.

---

### Post by skoh-fley on 2009-04-13
> **jasay said:**
> Shot in the dark . . . You might try "winecfg", go to the "drives" tab and hit autodetect.  Then apply and try to install now.  I seem to be able to get to the install now.

For those trying to install from a mounted ISO rather than a physical disc, there is an extra step to this, and I thought I would share my discovery.

You need to add a drive mapping in that window (winecfg -> Drives) and point it to your mount point folder.

So for instance, I'm using the application Gmount-iso to mount my Diablo II ISO file. When you mount something, it asks you for the location of the ISO and for an empty folder to use as a mount point. If my mount point was "/home/skoh/mount/", in the winecfg window I would hit "Add" then edit the Path field below the Add button to point to "/home/skoh/mount/".

This will make Wine recognize your virtual drive and you should be able to install fine from there.

---

### Post by SnickerSnack on 2009-04-16
> **skoh-fley said:**
> For those trying to install from a mounted ISO rather than a physical disc, there is an extra step to this, and I thought I would share my discovery.

You need to add a drive mapping in that window (winecfg -> Drives) and point it to your mount point folder.

So for instance, I'm using the application Gmount-iso to mount my Diablo II ISO file. When you mount something, it asks you for the location of the ISO and for an empty folder to use as a mount point. If my mount point was "/home/skoh/mount/", in the winecfg window I would hit "Add" then edit the Path field below the Add button to point to "/home/skoh/mount/".

This will make Wine recognize your virtual drive and you should be able to install fine from there.

That worked well for installing, but now the game won't run (insert disc).  I want to play v1.07, so patch 1.12a won't help.  Any ideas?

---

### Post by hikaricore on 2009-04-16
You might want to look into something like a nocd fix.  I can't link you anywhere here you'll have to find it yourself.

---

### Post by SnickerSnack on 2009-04-16
> **hikaricore said:**
> You might want to look into something like a nocd fix.  I can't link you anywhere here you'll have to find it yourself.

I'm aware of no-cd-hacks, but that won't work for me.  I'm a member of a trade group that doesn't allow hacks or cheats.

I will probably ask the group leaders for permission to use the hack in linux only if I can't find a different way to do it.

If several posters here could confirm that there is no other way to run D2 1.07 in ubuntu, then it may help my case in asking for permission to use the hack.

Thanks, though.

---


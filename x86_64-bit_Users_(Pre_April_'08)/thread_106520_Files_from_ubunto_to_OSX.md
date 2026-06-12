---
title: "Files from ubunto to OSX"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by burobaaje on 2005-12-20
I'm a newbie at ubuntu.  Works great right from intall, by the way, on an iMac 17" flat panel.

I downloaded a file to the Desktop and then wanted to get it over to my the Mac OSX system.  Is there a way to install a drive that both will recognize AND allow transfer via Gnome.  I tried copying it to a USB drive that both recognize but I don't have the privilege to do so.  How do you become a superuser in Gnome?  I know I could do it with sudo in Terminal, but yuk!

---

### Post by Iandefor on 2005-12-20
run the command ```
gksudo nautilus
``` to open up Nautilus as root. You should also change the permissions for the disk while you're in Nautilus;
go to the location "Computer", right-click the icon for your drive, and select
"Properties". Go to the "Permissions" tab and set the permissions to your preference.

---

### Post by pauljwells on 2005-12-21
Instead of an external drive, you can use this utility to mount your linux drives in OSX

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)


Ubuntu already includes utilities to mount HFS volumes.

---

### Post by burobaaje on 2005-12-21
I tried gksudo nautilus.  Terminal responsed, Not authenticated.  The window still came up as root browser after I put in password and I changed the permissions but they evidently were not accepted.  On exit, terminal gave message of pending operations that could not be done.  Back on regular desktop opened browser and noticed that the permissions were never changed.

I am going to look at mounting the HFS volumes in ubuntu, although I have no idea where to find that utility.

Will also look up way to mount linux volumes in OSX.

Thanks

---

### Post by Iandefor on 2005-12-21
There are two tools you need to access HFS volumes: hfsutils and hfsplus. To get them, open up a terminal and type in ```
sudo aptitude install hsfutils hfsplus
``` which will install them both. I don't know what to tell you 
about the permissions thing; that's always worked for me.

---

### Post by ctt1wbw on 2005-12-21
[QUOTE=burobaaje]I'm a newbie at ubuntu.  Works great right from intall, by the way, on an iMac 17" flat panel.

I downloaded a file to the Desktop and then wanted to get it over to my the Mac OSX system.  Is there a way to install a drive that both will recognize AND allow transfer via Gnome.  I tried copying it to a USB drive that both recognize but I don't have the privilege to do so.  How do you become a superuser in Gnome?  I know I could do it with sudo in Terminal, but yuk![/QUOTE]

I have a 17" G5 iMac, too.  How did everything go?  Does your built in wifi work?  How about bluetooth and usb and firewire?  I'm anxious to get back in to the Ubuntu fold myself.

---

### Post by burobaaje on 2005-12-21
First thanks to Iandefor and pauljwells for the help.

Works great!  I downloaded and installed FC4 and never made it to the desktop.  I could have, but decided to trash it and get ubuntu.  No problem at all, it automatically partitioned the free space on the iMac and intalled without a problem.  The iMac is on DSL via router and it found the internet immediately and updated the system.  Firewire,USB (logitec usb wireless keyboard and mouse), CD Drive, all work without problem.  Don't have Bluetooth so don't know.  I installed the utility to mount linux drives in OSX so I can move from one system to another have have acess to files.  It looks good!  Been about 6 years since I have had a linux system so I really can't compare it with any other distro.

BTW I used iPartition to get the free space for ubuntu, so I did not have to trash OSX and reload it.  That was nice.

One other thing, my iMac is a G4 and does not have wifi...should have written G4 in first post, forgot about the new stuff!

---

### Post by muchmusic on 2005-12-21
[QUOTE=pauljwells]Instead of an external drive, you can use this utility to mount your linux drives in OSX

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)


Ubuntu already includes utilities to mount HFS volumes.[/QUOTE]

be warned that that SF project has not been updated for tiger, and the kernel extension uses some code that has been changed - at best it won't mount a volume, but could cause problems with a mounted volume.

---

### Post by pauljwells on 2005-12-21
Good point, muchmusic. Since discovering Ubuntu I haven't bothered to keep up with OSX releases and I'm still a Panther Luddite! To be sure, it's best to mount the linux drives only as long as needed to move files around, then unmount, just to avoid any chance of screwing up one system from another.

---

### Post by burobaaje on 2005-12-21
Thanks, I'm running 10.3.9 and only mount occasionally for transfer to one folder only on the linux side and then unmount immediately.  I have 10.4.3 on an external usb drive but use it very little.

---

### Post by DJ_Max on 2005-12-21
A simple way to share files between patitions is to follow [http://ubuntuppc.info/index.proxy.php?node=24](http://ubuntuppc.info/index.proxy.php?node=24)

---

### Post by burobaaje on 2005-12-22
[QUOTE=muchmusic]be warned that that SF project has not been updated for tiger, and the kernel extension uses some code that has been changed - at best it won't mount a volume, but could cause problems with a mounted volume.[/QUOTE]

Don't know what the culprit was, but yaboot failed after using extfsx.  Re-installed the entire ubuntu os and probably??? could have used the install cd to fix yaboot.  extfsx may not have been the problem, but don't know what else could have wipped yaboot.

---

### Post by burobaaje on 2005-12-22
[QUOTE=DJ_Max]A simple way to share files between patitions is to follow [http://ubuntuppc.info/index.proxy.php?node=24](http://ubuntuppc.info/index.proxy.php?node=24)[/QUOTE]

how do I install hsfplus.  tried:

      sudo aptitude install hsfplus

nothing installed.  i've found a .deb package for it but as of yet unable to get it installed.  i've read all i could find.

thanks

---

### Post by Iandefor on 2005-12-22
[quote=burobaaje]how do I install hsfplus.  tried:

      sudo aptitude install hsfplus

nothing installed.  i've found a .deb package for it but as of yet unable to get it installed.  i've read all i could find.

thanks[/quote] have you [enabled the Universe and Multiverse repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto")? In addition, to install the .deb package you downloaded, have you tried the command ```
sudo dpkg -i <name of hfsplus .deb>
``` If that doesn't work, post whatever that command returns.

---

### Post by DJ_Max on 2005-12-22
```
sudo apt-get install hfsplus
```
It's in the main repo.

---


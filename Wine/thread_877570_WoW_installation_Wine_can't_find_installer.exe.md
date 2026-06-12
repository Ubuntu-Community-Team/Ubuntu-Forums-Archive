---
title: "WoW installation: Wine can't find installer.exe"
date: 2008-08-01
forum: Wine
---

### Post by Floridor on 2008-08-01
Hi. I'm a Ubuntu noob, but I seem to be having a problem that nobody else has raised.

I've been trying to install World of Warcraft on Ubuntu 7.10 using Wine.

I've copied the files from cd to a folder on my desktop and have tried to open the installer using wine. But when I do, nothing happens for about thirty seconds. Then a window labelled "installer" opens, and says, "no installer data could be found."

So what do I do? The file is there, despite the error message.

Is this a wine problem or a blizzard problem? I've installed the game successfully on another machine (windows).

Another problem. When I try to install directly from the DVD, I can't  get the installer.exe file to display. I followed the directions on the main "installing WoW" instructions, but to no avail. When I give the command, 

"sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/"

Terminal says, 

"mount: /dev/scd0 already mounted or /media/cdrom1/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/cdrom1"

I've also tried using Playonlinux, but I get to the stage where it says "don't click ok because you're not SURE that the installation is complete" And even if I do click ok it just creates an empty file named world of warcraft.


Any suggestions? I'd be very thankful for any help anyone can offer.

---

### Post by flytripper on 2008-08-02
try unmounting the disk before inputting the mount command.. did you do that?

also did you run winecfg in terminal?

---

### Post by Floridor on 2008-08-02
I ran winecfg, but I'll try unmounting before mounting as you suggest.

ummm, how do I do that?

---

### Post by miegiel on 2008-08-02
i just copied the wow from the win program files too
.wine/drive_c/Program Files in my home

than ran the wow.exe with wine
no need to install really

---

### Post by Spydr4590 on 2008-08-02
Floridor, this is a common issue when trying to install from WOW DVDs. You won't be able install this way, even when you copy these files to your hard drive.

You will need to download the game via these links to install. I would recommend burning these to dvd when you're done downloading.

[http://www.worldofwarcraft.com/account/download/clients/pc/WoW-BurningCrusade-enUS-Installer-downloader.exe](http://www.worldofwarcraft.com/account/download/clients/pc/WoW-BurningCrusade-enUS-Installer-downloader.exe) WOW Burning Crusade

[http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe](http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe) WOW

---

### Post by Floridor on 2008-08-02
Brilliant! Thanks! That's solved that problem.

---

### Post by NuSuey on 2008-09-23
thanks for this solution..

[http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab](http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab)

had problem with the installer.exe thing ;)

---

### Post by benow on 2010-12-14
Even after the nohide, I received this same error on Wrath upgrade.  The fix was to do a chown -R user:user * on the installer files.  When copying I received a perm denied after custom nohide mount, so copied them with sudo cp and they were then owned by root and unaccessible to when the installer was run with wine ./Installer.exe.

Hope this helps someone... Certainly saved me a couple days of downloading.

---


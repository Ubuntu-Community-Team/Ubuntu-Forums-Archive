---
title: "How to install Starcraft"
date: 2007-02-21
forum: Wine
---

### Post by flaak_monkey on 2007-02-21
I was wondering how to install games like Starcraft and Diablo 2 to Ubuntu under Wine?

---

### Post by Sqwishy on 2007-02-21
Use should a program called wine, it replicates the windows api, and its free. Sometimes cedega works better but it cost's $$$!

Diablo 2 works really well. Check out the Wine Application Database! [http://appdb.winehq.org/](http://appdb.winehq.org/)
 
Diablo 2 [http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49)
Diablo 2 LOD [http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315)
Starcraft [http://appdb.winehq.org/appview.php?iAppId=72](http://appdb.winehq.org/appview.php?iAppId=72)

---

### Post by edemark on 2007-02-22
try these links

[http://frankscorner.org/index.php?p=starcraft](http://frankscorner.org/index.php?p=starcraft)
[http://frankscorner.org/index.php?p=diablo2](http://frankscorner.org/index.php?p=diablo2)

---

### Post by slimdog360 on 2007-02-23
nevermind

---

### Post by the.unclean.cpp on 2007-03-25
Any idea of how to install on cedega? It's kinda choppy on wine. Thanks!

---

### Post by x1a4 on 2007-03-30
Hi,

Here's how I'm running Starcraft and StarCraft Broodwar using *wine* without being choppy.  

I have Starcraft on my XP drive (/mnt/hda1) which I installed in Windows.  I then installed FUSE and ntfs-3g.  Then mounted my windows drive using ntfs-3g in _/etc/fstab_  like so: 

**UUID=FE80761A8075DA1B /mnt/hda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1**

I also tweaked my _xorg.conf_ file and set some OpenGL specific environment variables. See page 19 of [this thread](http://ubuntuforums.org/showthread.php?t=221313&page=19) for details.  

I also have these wine environment variables set: 

[B]setenv WINEPREFIX  ${HOME}'/.wine'
setenv WINESERVER  '/usr/bin/wineserver'
setenv WINELOADER  '/usr/bin/wine'
setenv WINEDLLPATH '/usr/lib/wine:/usr/lib:/mnt/hda1/WINDOWS/system32'[/B]

I then created ISO images of my StarCraft CDs and mounted them in _/etc/fstab_ like so: 

[b]/iso/starcraft/starcraft.iso /mnt/starcraft iso9660 rw,loop=/dev/loop0 0 0
/iso/starcraft/starcraft-broodwar.iso /mnt/starcraft-broodwar iso9660 ro,loop=/dev/loop1 0 0[/b]

Finally, I created these symlinks to the mounted ISO drives in the _~/.wine/_ directory: 

~/.wine/dosdevices/i: -> /mnt/starcraft/
~/.wine/dosdevices/j: -> /mnt/starcraft-broodwar/

I run Starcraft like so: 

*wine /mnt/hda1/Program\ Files/Starcraft/starcraft.exe*

I've 1GB of system memory and a 8xAGP Nvidia GeForce FX 5200 video card with 128MB of video memory. 

While Starcraft takes longer to load than on windows, once it loads it's nice and smooth.

---

### Post by sloggerkhan on 2007-04-08
I tried doing this for warcraft III, and istalled it successfully from the ISO I extracted, but it doesn't detect them when I launch the game. (I'm afraid my CD drive is dying because wine doesn't always detect the disk WITH it in the drive.)

---

### Post by Swimerdude on 2007-04-08
Slogger maybe try a crack on it?  also umm check out euro-battle.net for a free crack and a server to play on if your into battle.net but you don't ahve a cd key.

---

### Post by carlosalvatore on 2008-03-27
> **x1a4 said:**
> Hi,

Here's how I'm running Starcraft and StarCraft Broodwar using *wine* without being choppy.  

I have Starcraft on my XP drive (/mnt/hda1) which I installed in Windows.  I then installed FUSE and ntfs-3g.  Then mounted my windows drive using ntfs-3g in _/etc/fstab_  like so: 

**UUID=FE80761A8075DA1B /mnt/hda1 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1**

I also tweaked my _xorg.conf_ file and set some OpenGL specific environment variables. See page 19 of [this thread](http://ubuntuforums.org/showthread.php?t=221313&page=19) for details.  

I also have these wine environment variables set: 

[B]setenv WINEPREFIX  ${HOME}'/.wine'
setenv WINESERVER  '/usr/bin/wineserver'
setenv WINELOADER  '/usr/bin/wine'
setenv WINEDLLPATH '/usr/lib/wine:/usr/lib:/mnt/hda1/WINDOWS/system32'[/B]

I then created ISO images of my StarCraft CDs and mounted them in _/etc/fstab_ like so: 

[b]/iso/starcraft/starcraft.iso /mnt/starcraft iso9660 rw,loop=/dev/loop0 0 0
/iso/starcraft/starcraft-broodwar.iso /mnt/starcraft-broodwar iso9660 ro,loop=/dev/loop1 0 0[/b]

Finally, I created these symlinks to the mounted ISO drives in the _~/.wine/_ directory: 

~/.wine/dosdevices/i: -> /mnt/starcraft/
~/.wine/dosdevices/j: -> /mnt/starcraft-broodwar/

I run Starcraft like so: 

*wine /mnt/hda1/Program\ Files/Starcraft/starcraft.exe*

I've 1GB of system memory and a 8xAGP Nvidia GeForce FX 5200 video card with 128MB of video memory. 

While Starcraft takes longer to load than on windows, once it loads it's nice and smooth.

Hello! 

I did something different and now my Starcraft is running like in windows.

I didn't install StarCraft again 'cause i had my starcraft installed in a partition of my hard drive when i had windows, but it will be the same. The only difference was to add the reg info to the wine registry, but i guess it won't be a problem if you're making a new clean installation.

The key avoiding starcraft get slow is disabling "Allow the window manager to control the windows" on WineConfig, or disabling the gnome visual effects (System -> Appearance -> Visual Effects -> None. (But i rather prefer the first option).

To see Starcraft on full screen do NOT use the virtual desktop (also an option in WineConfig).*

I can play both single player and multiplayer with the last blizzard patch (to run UDP protocol on LAN).

If you still have problems with Starcraft you should trying the info on the winehq plus what I've told you.

If you  don't want to use your cdrom you alway can do and iso image, and use a no CD app (Be aware that you must have the original CD, if don't you might be violating the law!). I use acetoneISO2 to mount easy and quickly.

Greetings! and I hope this info helps you!

-
* I strongly recommend using the virtual desktop when you're installing something with Wine, in case it freezes, and the first time you run it. Once you've test the application well, you can run it without the virtual desktop.

This tip works also for Diablo 2 + Expansion.

---


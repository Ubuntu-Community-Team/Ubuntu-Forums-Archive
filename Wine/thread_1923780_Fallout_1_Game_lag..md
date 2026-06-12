---
title: "Fallout 1 Game lag."
date: 2012-02-11
forum: Wine
---

### Post by Vyst on 2012-02-11
[SIZE=2]I'm running Ubuntu 10.04 and I just installed Fallout 1 from a store-bought CD-ROM (the downloaded version I tried just kept crashing on me). I installed the game and run it with Wine 1.2.2 and everything works fine except the game is pretty laggy, specifically moving the cursor around. I have noticed this problem before playing other PC games on Ubuntu but I was never attached enough to playing the game to put the effort into fixing it.

I've read around a little bit and have noticed different suggestions, from re-allocating RAM, messing with video card drivers, to using different versions of Wine.

Has anyone had a similar problem to this and have any suggestions?

Thanks for any help!
-Vyst
[/SIZE]

---

### Post by Dlambert on 2012-02-11
Update to latest WINE, 1.4-rc3 as of late.

---

### Post by Dlambert on 2012-02-11
Try playonlinux maybe? Set the graphics settings to > Use winecfg to set the Windows version to Windows 98 for the setup.exe program located on the Fallout CD.
Run the setup.exe program with Wine.
Fallout doesn't correctly detect disk sizes, this problem also occurs when you try to install Fallout while running Dosbox or Windows, select the small installation for now.
If you have version 1.0, download the 1.1 patch, and extract it to your Fallout directory, for example:
$ tar xf fallout_patch_1.1.tar.gz -C ~/.wine/drive_c/Fallout/
Use winecfg to set the Windows version to Windows 98 for the Fallout executable, falloutw.exe.
Optional:
If you don't want to insert the Fallout CD every time you want to play the game, you can copy the game files to your hard disk:
$ cp -r /mnt/cdrom/master.dat /mnt/cdrom/critter.dat /mnt/cdrom/data ~/.wine/drive_c/fallout/
Be sure to overwrite master.dat and critter.dat, Fallout generates smaller versions of these files when running as a cache. 
Edit fallout.cfg, and change the paths specified by the music_path1, critter_dat, and master_dat options from your CD-ROM to your harddisk, for example:
master_dat=D:\master.dat should be changed to master_dat=C:\fallout\master.dat.

> Notes / Possible Issues

The sound stutters, movies stutter, game is generally slow.
Setting the nice level for Fallout can seriously increase performance:
$ /usr/bin/nice -n 18 wine falloutw.exe
You may want to try fiddeling with the exact nice level.
The game crashes, even after the 1.1 patch!
Some patches have all the filenames uppercased, Fallout only seems to look for lowercased filenames, download the patch from above.
I can't save my game!
Again a problem with uppercase/lowercase filenames, try: mkdir data/savegame, you can remove the uppercased SAVEGAME if you want
The fade-in/fade-out takes ages!
Use winecfg, and set turn "graphics->emulate a virtual desktop" on.
The game won't run: segmention error.
ALSA is known to cause this, try Wine 1.0-rc1 or use OSS or Arts.
Mouse pointer is unusable
This known bug #6033, and appear on 24bpp desktop, for workaround use this command: 
xinit `which wine` /home/path/to/fallout2.exe -- :1 -depth 16



---

### Post by Vyst on 2012-02-12
Thanks Dlambert!

At the moment I'm using someone else's computer to write this because I can't seem to get mine connected to the internet. Thus I am for the moment unable to update wine. However, I adjusted the nice level. This didn't fix it completely, but it made a significant improvement to the laggy-ness of the game.

Installing from a CD-ROM doesn't give me the option of what size of installment I want, so there's not much I can do abot that one. 

I'll update wine next to see how the game runs and report back when that happens.

By the way, what exactly is the nice level, and how does adjusting to make the game flow smoother?

-Vyst

---

### Post by Vyst on 2012-02-14
[SIZE=2]I just got to a working internet connection and updated my version of wine. In combination with changing the nice setting, the game is operating at a usable level. I wouldn't call it 100%, but it's significantly better than it was and I can at least feel not irritated when playing it.

Thanks for the help!
-Vyst
[/SIZE]

---


---
title: "Lates wine and Steam (Game) problem"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Braindamaged on 2007-05-26
Its probably me doing somthing wrong as this is the first time using wine to play a game.

Steam will install fine and update without a problem but if i try to run a game CS:S Steam tells me its Preparing to start the game and then it crashes with a Windows error message saying the following
> SteamStartup() failed: SteamStartup(0xf,0x0034E064) failed with error
1: The registry is in use by another process, timeout expired

any one got a clue as to whats wrong?

-----
System Spec

AMD X64 3000+
1gb pc4000 ram
Geforce 4 MX 440 64mb
Ubuntu 7.04 Fiesty 64bit
Wine 0.9.37

---

### Post by sonicborg on 2007-06-03
bump, same problem.
tried running as user and root. command line and desktop/menu items

---

### Post by fabertawe on 2007-06-03
This can be a real pain, fortunately creating a file named shortcuts.dat in the Steam directory usually fixes it.

I use a script to run Steam which looks like this...
```
#!/bin/sh

cd /home/paul/c/Program\ Files/Steam/
touch shortcuts.dat

WINEDEBUG="fixme-all" wine steam.exe

mv *mdmp /home/paul/.Trash
```
Obviously you'd have to alter the 'cd' path to point to your Steam folder. The last line moves the crash dump files to the bin as they tend to mount up rather quickly! (again, alter the path if using.. unless your name is Paul ;))

One brilliant thing you can do is use the ntfs-3g read-write driver and then create a symbolic link to 'Steam\SteamApps' on your real Windows partition. This gives me access to all my Steam games from Wine without having to copy across 17.2 Gb of data! :D

EDIT: I've just found **[this link]("http://developer.valvesoftware.com/wiki/Steam_under_Linux")** on the Valve site stating...
"Creating a Symlink to SteamApps on a NTFS partition doesn't work either. Steam will start up, but your GCFs will get corrupted or - if you're lucky - Steam only assumes they are corrupted. So you won't get around having duplicate GCFs for Linux and Windows if you plan on using Steam with both operating systems and having NTFS partitions for Windows."
I've not had any problems yet myself and will continue to use the symlink but let it be a warning to everyone!

EDIT 2: Typical! I spoke too soon... using ntfs-3g and symlinking does indeed corrupt your GCFs ](*,) Oh well, saves anyone else the frustraton of finding out ;)

Paul

---


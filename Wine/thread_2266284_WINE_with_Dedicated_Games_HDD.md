---
title: "WINE with Dedicated Games HDD"
date: 2015-02-21
forum: Wine
---

### Post by Abdul_Hakim on 2015-02-21
What's up everyone, sorry if this is a noob question that is addressed in the stickies somewhere.

I'm currently working with Ubuntu in Virtual Box, making sure I can get things set up how I like before I actually install it onto my system (previously tried Linux Mint but didn't like it, had to switch back to Windoze 7 for the time being). I think I've got everything figured out except for WINE.

I think I've kinda got the basic idea, you install wine, run winecfg and it creates the fake C: drive in your home folder, and then you can install applications from there.

However, I haven't been able to find any information about how this works with separate dedicated hard drives. For example, I have:

an SSD for the OS
two HDDs for storage (one for home storage, one for media server storage)
another HDD for games only

I want to use WINE, but have all the games actually physically installed onto the Games drive (i've tried installing steam direclty into Linux Mint before and I just didn't like it, graphics performance took a significant hit). But I have not been able to find clear instructions on how to do this. Gaming is really my only use for WINE/playonlinux, other Windows applications I really don't need.

If someone could give me a basic walkthrough or point me in the direction of a tutorial, I'd be super appreciative :)

---

### Post by TheFu on 2015-02-22
Windows wants applications installed on the "C" drive.
The best way I know to make WINE use a different location is to set the WINEPREFIX  environment variable to the location you want -.... like on your Games disk before doing the install.
Sadly, I think you'll need many WINE installs, as almost every different program needs different, often conflicting, winetricks to work.

So .... setup different scripts that set WINEPREFIX, then run wine with the program you want for that session. Here's mine for quicken.
```
#!/bin/sh
WINEPREFIX="/home/thefu/.wine-Qucken2008/" wine "C:\\Program Files\\Quicken\\qw.exe " &
```
make sense?

However, in the end you'll end up with 
/extraStorage/wine-CS
/extraStorage/wine-quicken
/extraStorage/wine-msoffice
/extraStorage/wine-stargate
/extraStorage/wine-game5
/extraStorage/wine-game6
/extraStorage/wine-game.....N

I've never used playonlinux.  Perhaps it has a cleaner way to do this same thing?

---

### Post by Abdul_Hakim on 2015-02-22
Forgive my ignornace, I'm still fairly new in Linux, where do I put that code you provided? Is there a config text file somewhere?

Basically what I want to do is be able to install my few steam games (CS:GO, TF2, L4D2, etc) onto my Games drive. And also some "acquired" games I can install from an .iso

So if I can successfully install Steam with WINE, once I run Steam, could I just point the game installations to my Games drive, just like I would do in Windows?

I'm sorry but I don't quite understand what you mean by multiple WINE installations, could you elaborate?

I haven't quite yet figured out Playonlinux either

Apologies again for my noobiness, I'm trying to learn :)

---

### Post by TheFu on 2015-02-22
> **Abdul_Hakim said:**
> Forgive my ignornace, I'm still fairly new in Linux, where do I put that code you provided? Is there a config text file somewhere?

Basically what I want to do is be able to install my few steam games (CS:GO, TF2, L4D2, etc) onto my Games drive. And also some "acquired" games I can install from an .iso

So if I can successfully install Steam with WINE, once I run Steam, could I just point the game installations to my Games drive, just like I would do in Windows?

I'm sorry but I don't quite understand what you mean by multiple WINE installations, could you elaborate?

I haven't quite yet figured out Playonlinux either

Apologies again for my noobiness, I'm trying to learn :)

So - I'm terrible at helping people new to linux. Sorry.  You probably won't understand what I say.
Create a file - like a batch file - and put those commands inside, make the file executable in the permissions - I'd put each of these files into my PATH, so they are available from any directory. If you are too new for that, sorry. I give up.

BTW - Linux programs need to be run from Linux file systems with Linux permissions. I've always run WINE that way - don't know how it will work with an NTFS formatted file system, like I suspect your "games disk" probably is. It might work fine, or not at all - Linux is a multi-user OS at the core, unlike Windows. That shows up everywhere - especially in file systems.

Different WINE installs is really about having a different base directory for each program you need to use with WINE. Just change the prefix as shown in the script file above - you need to do that for both the game install and for running that same game again. Each game gets a different prefix - that will cause another virtual Windows install.

I haven't used Windows in years for anything new - definitely not for gaming. Never used steam either, but I thought there was a native version for Linux.  I use Windows daily, but just for the same 2 things, over and over.

My thoughts on learning Linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - this is more for server admins, but the first 4 items in the list are good for everyone to learn as basic knowledge.

I wish you well in your learning and gaming success!

---

### Post by Tweak42 on 2015-02-28
> **Abdul_Hakim said:**
> Forgive my ignornace, I'm still fairly new in Linux, where do I put that code you provided? Is there a config text file somewhere?

Basically what I want to do is be able to install my few steam games (CS:GO, TF2, L4D2, etc) onto my Games drive. And also some "acquired" games I can install from an .iso

So if I can successfully install Steam with WINE, once I run Steam, could I just point the game installations to my Games drive, just like I would do in Windows?

I'm sorry but I don't quite understand what you mean by multiple WINE installations, could you elaborate?

I haven't quite yet figured out Playonlinux either

Apologies again for my noobiness, I'm trying to learn :)

It's not multiple installations of wine, but wine [PREFIXES]("http://wine-wiki.org/index.php/WINEPREFIX").  Each are intended to be standalone "bottles" so they can be individually tuned and configured to work with 1 particular program and not interfere with another program.  You might try out Codeweavers [Crossover Linux]("https://www.codeweavers.com/") product since it does make bottle management easier with a gui.  FYI: Codeweavers funds the wine project development. However anything you can do in Crossover you should be able to do at the command line with plain wine.

A suggestion for reusing your windows games drive or locating just the game directory to a separate physical drive, try [symlinking]("http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/") directories.  Before I obtained a larger SSD to fit a local install, I used to symlink my World of Warcraft directory on my NTFS windows drive to my .wine prefix.  Some games might require registry entries and dll files placed outside the game directory at install time so YMMV.

---


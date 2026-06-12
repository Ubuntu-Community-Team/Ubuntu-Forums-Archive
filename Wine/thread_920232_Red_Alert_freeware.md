---
title: "Red Alert freeware"
date: 2008-09-15
forum: Wine
---

### Post by Rohaq on 2008-09-15
I'm having issues getting the freeware version of Command And Conquer: Red Alert to run. The AppDB says that it looks like it's because I've mounted the ISO (since I have no blank CDs at the moment), and that I'd need to create 'an additional d:: device link'.

However I can't seem to find any information on creating this link. I tried creating a symlink for e:: (as the previous mount for the location was e:) to the location where it was mounted, but still couldn't get it to run. Has anybody got any suggestions?

---

### Post by Rohaq on 2008-09-15
Never mind, figured it out:
[LIST=1]
[*]Mounted via sudo mount -vo loop <path to ISO file> <mount location>
[*]Opened winecfg and set to Windows 98, added drive with path to mount point for ISO
[*]Opened terminal
[*]Typed ln -s <path to ISO file> <drive letter>\:\:
[*]Opened drive in dosdevices, SETUP.EXE runs perfectly.
[/LIST]

---

### Post by davidpeace on 2008-09-15
I have tried following your directions. I'm up to the part about opening the drive in dosdevices. Found the dosdevices. What command do you use to open it? I tried open, but I get the following error messages:

Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console

---

### Post by sanone on 2008-10-01
You could also try open red alert. This is an open source game engine for red alert. Combined with the data files you have a native version of this great game for linux!

Check this site for more info: [http://code.google.com/p/openredalert/](http://code.google.com/p/openredalert/)

---

### Post by Mic_Droz on 2008-11-20
Man, trying to get it to work from .iso is doing my head in...

I *think* I've got the correct links in place in the wine config, it just refuses to see my iso from wine... I mounted using Gmount-iso, among other things... still says that it can't find the setup files...

Can anyone help out? The AppDB page didn't really seem to help - I think I've gotten lost in the instructions...

---

### Post by Thelasko on 2008-11-21
I don't know about the freeware version, but I've had great success running the original in dosbox.

P.S. Read the Readme.txt file.  In the original, it mentions that the Windows version is actually the DOS version in dosbox.  Running it in Wine would just be running it in dosbox anyway.

---


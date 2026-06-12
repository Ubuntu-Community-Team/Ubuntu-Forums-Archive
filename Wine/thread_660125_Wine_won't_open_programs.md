---
title: "Wine won't open programs"
date: 2008-01-06
forum: Wine
---

### Post by Nazty_Nayt on 2008-01-06
Ok, what I'm trying to do is use my RCO editor to create custom coldboots for my PSP. I downloaded the program, and with it comes the following; a bin folder, a bmp folder, an output folder, a readme, and a start.lnk file.

Now it's a windows based program so first thing I did was get wine from the synaptic manager. Ok, as the readme says, I make my template, then it says run start, I try to open start with wine, and nothing happens, at all. Now the rcoeditor has an exe file inside the bin folder, and I know that .lnk files are shortcuts to the actual .exe so I decide to just ahead and open the .exe using wine, and still nothing happens, it's just not running the program, does anyone think they can help me out here, I'd greatly appreciate it.

---

### Post by uechi on 2008-01-06
Wine doesn't open .exe files by default when you install it.

To do this, right click on the exe, choose "Properties",  "Open With" tab (or something like it), click "Add", "Custom Command" at the bottom, and type:
```
wine %s
```
exactly like that. Now all .exes should automatically open with Wine.

or to do this in a terminal, cd to the directory with the file, and type:
```
wine "name of file here.exe"
```
obviously replacing the name of course ;)

If you've already done this (you said you opened it with Wine) and the program still doesn't work, then it may just not work because Wine isn't Windows, it's an emulation. And although many programs do work, there are also a lot that don't.

Hope this helps!

---

### Post by Nazty_Nayt on 2008-01-06
Ok, when I tried the first one, I got nothing same thing, nothing opens, the cursor doesn't change to load anything either, like usual.  When I try the second option all I get is this...


rcotool v0.4 by Z33

Usage: rcotool [-option] file.rco [name1] [name2]

        Maximum of 1MB from the files is used.

   -a   Decompress all files
   -A   Decompress all files & convert images to bitmaps
   -c   Compress the inputfile using zlib.
   -d   Decompress file
   -D   Decompress file & convert images to bitmaps
   -f   Find file
   -F   Find file & display informations
   -g   Get file as is
   -l   List all files
   -L   List all files & display informations
   -r   Replace file
   -w   Replace wave texture in *.gmo file

So I don't know if it worked or not.

---

### Post by hikaricore on 2008-01-06
Looks like it's working fine.

You're running a command line based program and it's giving you the standard help output since you gave it no options.  (this will also never show anything when run outside of a CLI environment, your first test was normal)
Perhaps you're trying to run a GUI for said program and are typing the wrong filename?

---

### Post by Nazty_Nayt on 2008-01-06
Yeah I want the GUI, cause I have no idea how to fully work the command line, I just don't get it.

---

### Post by hikaricore on 2008-01-06
Then you'll need to run the proper program, whatever you are running is a CLI program like I said..  have you ever used this "rcotool" before?  Do you understand how it functions?

---

### Post by Nazty_Nayt on 2008-01-07
That I do not, I think I'll just have to wait for my girlfriends laptop to get fixed, and just run it on her xp.

---

### Post by DoktorSeven on 2008-01-07
From what I read about it, it's commandline only.  Read up on its options (you mentioned a readme file, that's a good place to start) and you should be able to figure out how it works.

---

### Post by tomasmateus123 on 2011-05-14
.exe files wont open because of the permission right click the .exe file and select properties and go to permissions and check the "allow executing file as a program, and then run it!!

---

### Post by NM5TF on 2011-05-15
> **tomasmateus123 said:**
> .exe files wont open because of the permission right click the .exe file and select properties and go to permissions and check the "allow executing file as a program, and then run it!!

or you can try this fix for wine....go here:

[http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

follow the "install from ppa" directions, then do the update apt

---


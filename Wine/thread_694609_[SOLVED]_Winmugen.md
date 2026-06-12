---
title: "[SOLVED] Winmugen"
date: 2008-02-12
forum: Wine
---

### Post by SMA11784 on 2008-02-12
Yeah, I know Linux Mugen came first, but all my friends' characters are for WinMugen.  I can't run theirs and I don't think they'd be able to run mine.

The actual EXE appears to run normally except that it can't seem to navigate the folders.  All I get is this popup (see attached PNG).


Error message: Can't open data/mugen.cfg. Make sure you have
extracted with directories
Error reading data/mugen.cfg


Everything's currently in a folder named Mugen on my desktop and there is indeed a valid file called "mugen.cfg" in /home/<me>/Desktop/Mugen/data, but for some reason the program can't see it.

Anybody else get this and find a fix for it?

---

### Post by happyhamster on 2008-02-12
Perhaps it needs a windows folder structure. You could check if installing/extracting to the mock c: drive  (~.wine/drive_c) makes a difference.

Or try looking into every .ini or .cfg  file you can find, to see what paths the program expects to use (and try editing those manually). And remember that linux is case-sensitive.

---

### Post by SMA11784 on 2008-02-12
That's actually where I had it first.  I thought moving it higher in the directory structure would make a difference, so I put it in /home/<me>.  It still didn't work.  I moved it to my Desktop purely to make it easier to find.

Case is not an issue; everything in mugen is lowercase.

There don't seem to be any .ini files at all.  And the .cfg file is exactly the file it can't find.  I've tried placing a copy in the Mugen folder.  It's as if WinMugen simply can't navigate the Linux file structure.


There has to be somebody out there who has WinMugen running in wine in Ubuntu.  I can't be the only one.

---

### Post by CarpKing on 2008-02-13
How are you running it?  Often programs can't find stuff if you just click the exe or run it from the terminal with the full path.  If you haven't already, cd to the directory where the exe is and then run it from there.

---

### Post by SMA11784 on 2008-02-13
Everything is currently in /home/<me>/.wine/drive_c/Mugen

I have a launcher with the command:

wine "C:/Mugen/Winmugen.exe"

Same error as always.

---

### Post by CarpKing on 2008-02-13
> **SMA11784 said:**
> Everything is currently in /home/<me>/.wine/drive_c/Mugen

I have a launcher with the command:

wine "C:/Mugen/Winmugen.exe"

Same error as always.

I just tried it out on my computer.  You should open a terminal and type "cd .wine/drive_c/Mugen" followed by "wine Winmugen.exe."  If this works, you can get the same functionality by creating a script in your home folder (or anywhere really) containing those two commands and then point your launcher to that script (make sure to make it executable in the "Permissions" tab of the Properties dialog).

---

### Post by CarpKing on 2008-02-13
Also, are you sure that your friend's characters don't work in the Linux version?  I've always been able to just drop the Linux executable into whatever folder the exe is in and double click it (in Gutsy I had to turn off AppArmor for it to run).

---

### Post by SMA11784 on 2008-02-13
Thank you for sufficiently advanced technology.

Now explain to me why it works.

---

### Post by messatsu on 2008-02-13
Linux Mugen is winmugen save for the hi-res backgrounds and select screens added recently by executable hacks.  Just use Linux Mugen.

---

### Post by Ferrat on 2008-02-13
> **SMA11784 said:**
> Thank you for sufficiently advanced technology.

Now explain to me why it works.

wine runs from the dir that you are in as a starting point, for some programs this doesn't matter but others really don't like it, this is just a guess but it should depend on how the program itself handles looking for files ect. 

for ex. if the program just reads the path to itself from the system source (or how you should put it) then it reads from the folder where you stood when you launched wine and the program should find everything without any problems since the change is added and accounted for when looking for the rest of the system.

but if your program just tries to read from the base of the wine install point and your standing in another area then all the paths will be wrong 

that's why all desktop links wine creates has the 
env WINEPREFIX="/home/user/.wine" 
 tag added before wine so that wine knows to work from that folder

at least that's why it works afaik, I could be wrong

---

### Post by Apex_G on 2008-10-07
There has to be somebody out there who has WinMugen running in wine in Ubuntu.  I can't be the only one.[/QUOTE]

Yeah, I've been running Winmugen under Wine for some time now. It runs perfectly. But recently I tried moving the folder to another directory, and an 'Error can't find CFG file' popped up...

---

### Post by mwillams73 on 2009-05-26
Ok this is starting to really piss me off ive read 5 old posts now about winmugen and linux mugen, but nobody is answering the real question here! I have win mugen it installed in wine but when i try to run it i get an error about some file not working properly: cant find file qoh_sm~1.fnt also this error:Error loading system data:data/system.def

So what does all that mean? I keep trying to find a full linux version of mugen but all i get are these 2.6 mb add ons tar.bz that dont work at all I extract it then another tar.bz, extract that another tar.bz

So whats the deal no linux native mugen? and yes i tried pain town it sucks.

Im glad everyone else got theirs to work so now how about a how to on how you did it instead of "it works for me"? What versions of wine are you guys running, how did you fix the errors that pop up? so on and so forth. Maybe then those of us who come here for help wont feel left out cause we're not as tech savvy as you.

---

### Post by sonicfactor on 2009-06-22
Ok i Tried Carbkings idea and it would of work but i got these errors:
-----------------
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea68,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x12b4f8) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12bb70 with type 1,WINED3DRTYPE_SURFACE
Loading button config for P1 joystick win.
Loading button config for P2 joystick win.
fixme:d3d:IWineD3DDeviceImpl_Release (0x12dbe0) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12b950 with type 1,WINED3DRTYPE_SURFACE
Initializing keyboard.
Initializing sound...ok
Initializing graphics.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132838,0x32f120): stub
Killed

----------------
So how is this fixed? and i guessing these are the reasons why mugen.cfg wouldnt work.

---

### Post by Elfy on 2009-06-22
Possibly it's because this is an old thread.

I would start a new one.

Thread closed.

---


---
title: "Trying To get Warcraft 3 to work using wine"
date: 2008-01-06
forum: Wine
---

### Post by Hitaroe on 2008-01-06
I have warcraft 3 ready in ubuntu using wine, c drive, it's in the program files (me trying to copy what it looked like it windows) and when I run the Frozen throne.exe with the disk in the cd drive It does this flashy black screen thing then magnify's everything I can't see my mouse but I use alt+tab and get out of it to find an error message. 

This Application has encountered a fatal error.

Program: c:\program files\Warcraft II\war3.exe
Exception : seemingly random numbers and (AccessViolation) right in the middle

The instruction at (Random number/letters) referenced memory at (Random but same as previous one..weird?).
The Memory could not be 'read'.

Press Ok To Terminate Application. 

I did not install warcraft in Ubuntu because I've lost my Frozen Throne CD-Key so to prevent losing the game I copied the warcraft folder to my Removable HardDrive I've tried it on other computers and it works fine so nothing is missing out of the folder.

I MIGHT be able to find my cd-key and install in directly but I thought this would be easier or exactly the same as installing it.

---

### Post by sauronsmatrix on 2008-01-18
hey, install this first,

[http://rapidshare.com/files/32999732/w3battle_121a.rar](http://rapidshare.com/files/32999732/w3battle_121a.rar)

and then try opening the game.

you can also play online on battle.net through a different server. enjoy!

also, if that dont work. try the other exe's:

Frozen Throne.exe
i forgot the otehrs, but yeah :D

---

### Post by liveforfunnow on 2008-03-08
I see this exact same error! I am running Gutsy with the restricted drivers installed. Does anyone have an idea? I am not trying to run Frozen Throne, but the regular Warcraft III.

---

### Post by liveforfunnow on 2008-03-08
> **liveforfunnow said:**
> I see this exact same error! I am running Gutsy with the restricted drivers installed. Does anyone have an idea? I am not trying to run Frozen Throne, but the regular Warcraft III.

FIXED! I just went into Applications >> Wine >> Configure Wine >> Applications. I added Warcraft III.exe to the list, and chose Windows XP. I then tried to start the program, and it worked! Does that work for you?

---

### Post by maximus5000 on 2008-10-01
> **liveforfunnow said:**
> FIXED! I just went into Applications >> Wine >> Configure Wine >> Applications. I added Warcraft III.exe to the list, and chose Windows XP. I then tried to start the program, and it worked! Does that work for you?


srry but i cant seem to make it work even after doing this?? :confused::confused: any more ideas???

---

### Post by sauronsmatrix on 2008-10-01
hey folks, i remember having to use the 
```
-opengl
``` paramater.

Maybe that will help? What is the problem you guys are having? Glitches/startup/crashes?

---

### Post by satbunny on 2008-10-08
I installed Warcraft III RoC and FT normally into a winxp bottle using Crossover Games.

I then downloaded the path 1.22a from Blizzard and copied into the executable folder.

I ran it and it failed with this error message:

"Blizzard PrePatch v2.70 compiled on Jul  7 2003
This program patches Warcraft 3

Log created at  5:34 pm on 10/08/2008

Registry error loading key 'Warcraft III\InstallPath'
File not found


RESULT: Prepatch failed"

Has anyone met this problem with the patch and/or solved it?

---

### Post by fusionisthefuture on 2008-12-06
i think the -opengl command is used at the end of the command when running in terminal:
```
wine /wherever/your/game/is.exe -opengl
```

i have an asus micro-atx motherboard with the new integrated intel x4500 graphics, and ive got TFT patched to 1.22a and every time i try to run it with wine, it changes shows the splash screen, changes the resolution to really low, and brings up a black screen, then promptly crashes X, and i have to re-login. i tried running it in terminal with opengl, but i get the same thing, and i cant figure out how to read what the terminal says when it crashes.  
thanks,
-FITF

---

### Post by PandaGoat on 2008-12-06
Try renaming the Movies folder located in the Warcraft III folder.

---

### Post by cpeake on 2010-02-26
> **PandaGoat said:**
> Try renaming the Movies folder located in the Warcraft III folder.

Hiya, 

Thanks for this tip. This got me as far as getting into the menus and in theory, I belive the game would've worked after this.

However, I think I'm suffering from not getting the -opengl parameter to work. FPS in the menus was unbearable and it didn't look very hardware accelerated to me.

When I go into the terminal, my 'Frozen Throne.exe' appears in WINE to be under /media/disk/Program Files/Warcraft III/Frozen Throne.exe. The terminal tells me that this directory can't be found. Or to be more precise: "wine: cannot find '/media/disk/Program'

What else do I have to include in the command line?

---

### Post by dyltman on 2010-02-27
> **cpeake said:**
> Hiya, 

Thanks for this tip. This got me as far as getting into the menus and in theory, I belive the game would've worked after this.

However, I think I'm suffering from not getting the -opengl parameter to work. FPS in the menus was unbearable and it didn't look very hardware accelerated to me.

When I go into the terminal, my 'Frozen Throne.exe' appears in WINE to be under /media/disk/Program Files/Warcraft III/Frozen Throne.exe. The terminal tells me that this directory can't be found. Or to be more precise: "wine: cannot find '/media/disk/Program'

What else do I have to include in the command line?

try typing the path in " ".

In my case I start warcraft 3 with:

```
wine "C:/Program Files/Warcraft III/Frozen Throne.exe" -openGL

```
and if I also want it to be windowed I add -window at the end.

---

### Post by Khakilang on 2010-03-24
> **liveforfunnow said:**
> FIXED! I just went into Applications >> Wine >> Configure Wine >> Applications. I added Warcraft III.exe to the list, and chose Windows XP. I then tried to start the program, and it worked! Does that work for you?

 I manage to go into the menu but my Frozen throne goes blank after when I go in to campaign, Is it I got to update something?

---


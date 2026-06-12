---
title: "Diablo 2 problem"
date: 2008-07-19
forum: Wine
---

### Post by Albert-21 on 2008-07-19
Hi!

I am new to ubuntu, i have throwned out vista for good. I installed linux ubuntu 8.04 and I wanted to play diablo 2 lod. I searched on google, to find a way to install it, I installed wine and typed this when i putted my diablo 2 disc one in.

wine /media/cdrom0/install.exe

and this error message pops up

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7d3625b

earlier I had a problem with the binkw32.dll, I placed it in the windows/system32 folder in wine.

aand then that message popped up.

Now i am starting to fell a need for smashing my computer.

Please help.

Thank you.

---

### Post by OpposingForce on 2008-07-19
Try navigating to the CD folder in the nautilus file manager, then double clicking the install.exe and wine should be set to run those .exe files by default.  Doing things from the command line with wine is harder.  If that doesn't work, try taking that .dll out of the windows folder to see if that makes it work, if that isn't what's screwing something up, then just put it back.

I also got sick of vista on my new laptop within 1 day, bothering me every time I wanted to do literally anything, and installed ubuntu 8.04 without a second thought.

---

### Post by Albert-21 on 2008-07-19
I tried navigating to the folder clicked on the install.exe it popped up but then it says:

"the application has encountered a critical error

Error #131 (0x85100083)
program:     D:\install.exe
file:  D:\setupmpq

press ok to terminate the application.



So that didn't work, got any other sugestions?

---

### Post by LasTSuRvivoR on 2008-07-19
Setup the game from Windows XP if you have
And copy all mpq files to game folder.
Then doublick your diablo II.exe from ubuntu 
you will be able to run your game if you have cd placed in your rom

---


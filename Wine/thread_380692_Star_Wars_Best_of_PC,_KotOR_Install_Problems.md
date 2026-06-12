---
title: "Star Wars Best of PC, KotOR Install Problems"
date: 2007-03-09
forum: Wine
---

### Post by Poptart on 2007-03-09
Okay, so I have WoW working flawlessly in Edgy with the beta NVidia graphics drivers. I have both Wine and Cedega installed. I bought the_ Star Wars The Best of PC_ collection a while ago, and I'd like to get KotOR running in Ubuntu. But, when I try to run the setup program from the CD (with Wine, specifically) I get the following error:

[I]Error Number: 0x80040708
Description: Unable to create required engine components, check whether you have appropriate privileges to create COM components.

Setup will now terminate.[/I]

This error is, I think part of the setup and not a Wine error (although I really could be wrong - I haven't used Wine enough to know one way or the other). When I attempt to install with Cedega I don't even get an error before it just closes down the setup program. I haven't been able to track anything down about it. Any thoughts?

---

### Post by buttons on 2007-03-10
Odd that it doesn't work in either one.  There was a bug posted (kinda) to the wine list that might involve 0.9.32 and InstallShield, which is the program that's crapping out here.  However cedega 5.2.10 (I'm assuming) isn't based on that and should work just fine.

The only thing I can manage is to try it in an older version of wine and see if it keeps dying.

Be sure that you've got permissions to write to your ~/.wine folder and that you aren't trying to install it anywhere but somewhere in there, e.g. C:\Program Files\anything.


You might also try copying (as user) the contents of the CD to a folder somewhere and installing it that way as a last resort.

If there's nothing important in your ~/.wine directory, you could also try rm -rf ing it and just typing "wine" at a prompt to regenerate a fresh environment.  The only mention I could find of this specific error anywhere on the net involved a corrupted windows installation, so that's something else to try.

hope something helps!

---

### Post by Poptart on 2007-03-12
I haven't tried the older version option, but none of the other suggestions work. :/

Oh well. I may borrow an original KotOR disc set from a friend and see if that helps at all. *boggles*

Thanks for the suggestions, though!

---

### Post by Banthaman on 2010-06-09
OK, I use my vista laptop to run most of my games from but with the latest update KOTOR died. So I went to the Linux 10.4 partition and with the help of WINE was able to install it and have it up and running with a big problem the graphic are showing a white screen as if a negative of a photo and the text is not showing, only a blue section of the screen. I have Wine configured to run the game as in XP default setting and verified through glxinfo direct rendering is enabled. My laptop has a Intel GMA4500 graphics card which was running the game fine in Vista until the latest update. Also in order for the window not to crash I have to run WINE in virtual desktop mode.

---

### Post by Contrast on 2010-06-09
> **Banthaman said:**
> OK, I use my vista laptop to run most of my games from but with the latest update KOTOR died. So I went to the Linux 10.4 partition and with the help of WINE was able to install it and have it up and running with a big problem the graphic are showing a white screen as if a negative of a photo and the text is not showing, only a blue section of the screen. I have Wine configured to run the game as in XP default setting and verified through glxinfo direct rendering is enabled. My laptop has a Intel GMA4500 graphics card which was running the game fine in Vista until the latest update. Also in order for the window not to crash I have to run WINE in virtual desktop mode.

How are you going about launching the game? The game's entry on WINE's Application Database ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=13024](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13024)) says the default launcher doesn't work, and that you must run it by executing swkotor.exe.

---

### Post by BigSilly on 2010-06-09
Even on XP I had to use a hacked .exe to get this game to run. It wouldn't play otherwise. I've never tried it on WINE, but it could be worth a pop.

---

### Post by del_diablo on 2010-06-09
> **BigSilly said:**
> Even on XP I had to use a hacked .exe to get this game to run. It wouldn't play otherwise. I've never tried it on WINE, but it could be worth a pop.

It works quite nice, I myself can't get it to run in any other way :/

---

### Post by Iowan on 2010-06-09
Moved to Wine - although original thread is getting kinda old...

---

### Post by Banthaman on 2010-06-15
I run it out of the swkotor.exe file directly.

screenshot:

[http://i41.photobucket.com/albums/e280/Bantha1/Screenshot.png](http://i41.photobucket.com/albums/e280/Bantha1/Screenshot.png)

---


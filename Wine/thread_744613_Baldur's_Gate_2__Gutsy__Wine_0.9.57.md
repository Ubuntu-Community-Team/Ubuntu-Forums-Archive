---
title: "Baldur's Gate 2 / Gutsy / Wine 0.9.57"
date: 2008-04-03
forum: Wine
---

### Post by myrtle1908 on 2008-04-03
Hello All,

I have read the posts on this forum about BG2 and Wine but none seem recent enough or answer my question.

I'm having trouble with the install.

Apparently with Wine 0.9.57 BG2+ToB has gone platinum on Gutsy so I thought I'd give it a shot.

I have tried the following:-

Using winefile browse to Setup.exe on disc 1

Run Setup.exe, worked fine but cannot change to disc 2.

Tried using 'wine eject d:' and disc ejects but when I insert disc 2 setup cannot read and when i browse to it the file manager displays question marks instead of the actual files.

Does anyone have a morons guide to installing BG2+ToB on Gutsy with Wine?

I once got it all installed with Cedega but then couldn't run due to some error with ChDimm.cpp/ couldn't find some *.bif file.

Are loki or GemRB of any use?  I'm actually not even sure what these are and the references on the forum to these are very old.

Please help.

Thanks muchly.

---

### Post by myrtle1908 on 2008-04-04
Well I have now managed to get BG2 to install and run.

Problem now is it is virtually un-playable due to annoying pauses after each action eg. I ask my char to move somewhere and after approx 3 second pause he does so.  Most annoying,

I read the sticky named "What I've learned about Wine" and tried some of the suggestions eg. WINEDEBUG but this did not help.  I've also tried different resolutions and different color depth but again no help.

Anyone know any Wine tweaks that may help or has anybody solved the annoying pause issue?

Cheers

---

### Post by myrtle1908 on 2008-04-05
I don't normally bump my own threads but ...

Anybody?  Any tips?

---

### Post by Melcar on 2008-04-05
Don't use 3D acceleration/animations and run it at 800x600.  I have also had problems with sound going on and off randomly.

---

### Post by Melhisedek on 2008-04-07
What kind of graphics card do you use myrtle? 
I was thinking of trying out BG2 as well but if we have same setup (Nvidia card here) I wont bother than :)

---

### Post by Firebat451 on 2008-05-13
How did you mannage to get the install to run?  I've tried everything even copying CDs to my HD, but I can't get the second CD to get recognized in the install.

---

### Post by RevNomad on 2008-07-04
Looking for help on this one as well. My son's enjoy Baldur's Gate but since our Windows machine died we have been unable run Baldur's Gate.

We get an error message(I'll need to try again to get the exact message) when ever we try.

Thanks in advance.

---

### Post by Modax42 on 2008-09-20
I sucessfully installed BGII just now, but the game fails to launch.   The WINE app database says that BGII should work.  It even gets a platinum rating.  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=408&iTestingId=23299]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=408&iTestingId=23299")

So i don't know what's wrong.  Could be my gimpy graphics card, but then again I've been playing BG1 on my laptop for some time now, and that game runs like a dream with WINE.

I don't know what the next step is or what I should try now...can anyone help?

---

### Post by Modax42 on 2008-09-20
I managed to get the game to run now, but its still kinda buggy.  I changed the Wine Configuration to run BG2 with Windows 98 settings, and then I changed the graphics options from Full Screen to windowed mode.  When I try to run now, BG2 appears on the task bar and appears to stall.  So I click rapidly on the taskbar tab and this (somehow) seems to help the launcher to load.  

Anyway, The bugs include sound which cuts in and out, and a blacked out screen outside of the field of play.  When I go out of the game, the blackness remains, and I have to refresh the screen by launching applications and clicking on it to clear it.  I will continue to report as I continue to try to make the game run better!

---

### Post by Modax42 on 2008-09-21
> **RevNomad said:**
> Looking for help on this one as well. My son's enjoy Baldur's Gate but since our Windows machine died we have been unable run Baldur's Gate.

We get an error message(I'll need to try again to get the exact message) when ever we try.

Thanks in advance.

I'm using the latest versions of WINE and Ubuntu, and for me the installation wasn't too much trouble.  I had a problem getting the disks to eject, but that can be handled simply by using the terminal command "wine eject" as I learned in this thread [http://ubuntuforums.org/showthread.php?t=925486&highlight=baldur%27s+gate]("http://ubuntuforums.org/showthread.php?t=925486&highlight=baldur%27s+gate")

To start the installation I opened the BG_CD1 directory and right-clicked on BG2.exe, selecting 'Open with WINE windows program loader'. the first time I tried the installation, the Installer Wizard crashed and I had to start over, but the second time it installed properly.  

For best performance, run BG2 in 'windowed' mode instead of fullscreen, make sure no other applications are running (I have found that this can cause serious problems) disable 3D acceleration, and use the performance settings indicated in BGConfig for a 450 MHz (!) computer.  BG2 has worked perfectly with these settings so far. (knock on wood!)

Hope this helps

---


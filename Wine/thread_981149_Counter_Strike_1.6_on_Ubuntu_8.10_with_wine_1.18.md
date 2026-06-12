---
title: "Counter Strike 1.6 on Ubuntu 8.10 with wine 1.18"
date: 2008-11-13
forum: Wine
---

### Post by kipe on 2008-11-13
Basically when I upgrade my system from ubuntu 8.04 to 8.10 and wine from 1.01 to 1.18 respectively - Counter Strike 1.6 stops working correctly. First when I was with wine 1.17 the game starts but after a minute everything messed up - all of the textures were going wrong. Then I reinstall wine and counter strike several times (including ~/.wine delete) without success.

Now I'm with latest wine 1.18 the CS 1.6 starts to the main menu, but when I start new game or try to join local network game. The status bar loads almost to the end and then returns me back to main menu. My video card is intel 815.

Please give me some clues, because I don't know what to do anymore.

---

### Post by cogadh on 2008-11-13
Just don't install 1.1.8 (it is an unstable version), stick with the stable 1.0.1 version that is in the Ubuntu repositories.

---

### Post by kipe on 2008-11-14
> **cogadh said:**
> Just don't install 1.1.8 (it is an unstable version), stick with the stable 1.0.1 version that is in the Ubuntu repositories.

Sorry for the dummy question but how to install exactly version 1.0.1 with 'apt-get install' ??? I went to winehq site but there is no version 1.0.1 for ubuntu 8.10 in their archive

---

### Post by cogadh on 2008-11-14
You don't need to go to WineHQ to get it. There already is a 1.0.1 package in the default Ubuntu 8.10 repositories. Just uninstall your existing version of Wine, remove the WineHQ repository from you software sources, reload the sources, then install Wine. You can do all that through Synaptic Package Manager.

---

### Post by kipe on 2008-11-14
OK, I've uninstall wine 1.18 and I've done installation of wine 1.0.1 from ubuntu repos. But the problem is the same. 

First wine asked me for msvbvm60.dll file. And I've copy the file from windowsxp to ~/.wine/drve_c/windows/system32.

After that the game starts to main menu, but when it's about to enter a network game or start a new one and the progress bar is near to end - stops and return me again to main menu.


HELP PLEASE:confused:

---

### Post by cogadh on 2008-11-14
What are you getting for terminal output from Wine? The full output, that is. The file you attached above does not appear complete. 

Also is this CS through Steam or standalone?

---

### Post by Ackiel on 2008-11-15
I have the same problem. I use none-Steam CS version.

I tried to:
* Use 1.0.0 and 1.0.1 Wine versions (where the game normally works on Ubuntu 8.04).
* Disable Compiz before game start.
* Emulate virtual desktop in Wine.
* Turn off DirectX options in Wine.
* Use PulseAudio, OSS instead ALSA as audio driver for Wine.
* Disable audio in Wine.
And also:
* Use Direct3D, Software video driver instead OpenGL in the game.

But the same problems are in any case. :(

---

### Post by heroidi on 2008-11-16
in my pc counter strike runs but with low fps and the sxe does not work

---

### Post by Ackiel on 2008-11-16
> **heroidi said:**
> in my pc counter strike runs but with low fps and the sxe does not work
As I know, this game doesn't need a good hardware resources. Maybe video or another important driver is not installed.

All drivers are installed... Try to:
* Disable Compiz (if you use it) before the game start.
* Install another CS build.
* Install another version of Wine.

And about sXe Injected Client...
"What does not works: Running the application", - (see the _[Wine AppDB - sXe Injected Client 3.2 Fix 2.0]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7725")_).

---

### Post by Ackiel on 2008-11-19
I have the same problem running Need for Speed Hot Pursuit 2 in Wine. Maybe problem in incompatibility with my video driver (Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller). I think it's the best theoretic explanation.

---

### Post by hoggson on 2008-11-19
I have upgraded to 8.10 and have noticed that on my Dell Latitude 110L, which uses the Intel 910GML chipset, graphics have become slower, and am now unable ot use the desktop effects.  I also noticed that to boot from the 8.10 CD i have to /xforcevesa to get more than a blank black screen.  I run CS 1.6 from Steam using Crossover Games, and the game will run for me.  It may have something to do with the changes that were made that affect the Intel 910GML chipset.  It is definatly different from 8.04.  I dont know if you can add your CS 1.6 to a free steam account, if you can try this.  And you could also try giving Crossover a go.  I also use Microsoft Office 2007 with Crossover Pro and it runs perfectly, more than can be said for WINE.

---

### Post by pqrs295 on 2008-11-20
Up to 70% Off, Hurry Sale Ends SoonAustralian Real Sheepskin Boots**[color=#c76200]Uggretailsale.com[/color]**Authentic ugg boots, crafted from 100% natural Australian merino sheepskin leather.**[color=#c76200]Uggretailsale.com[/color]****[color=#c76200][/color]**100% Genuine AustralianUgg BootsPay by Paypal, Non-tax, Hurry!**[color=#c76200]Uggretailsale.com[/color]**

---

### Post by Ackiel on 2008-11-21
I've tried to use Crossover Games to run CS... There are the same problems. :(
I think it's incompatibility with my video driver.

---

### Post by cogadh on 2008-11-21
The Intel driver has had issues on Linux in the past, plus it is not the most robust gaming chipset to begin with. I don't know if the driver version is different on 8.10 as compared to 8.04, but that might be something to check (can't check on my system, I have an Nvidia card).

---

### Post by uldo on 2008-12-08
I got this proble - everything runs just fine (so far) but when i pres on "Find Servers" it tries to connect for some time and then says "Could not contact master server to retrieve server list".
I'm running stand alone cs 1.6...

---

### Post by hoggson on 2008-12-09
Sorry to sound stupid, but how would I go about finding out what the difference in the drivers is from 8.04 to 8.10?

---


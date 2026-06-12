---
title: "help with installing in powermac G4"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrewlt on 2005-12-12
[FONT="Comic Sans MS"][SIZE="4"][COLOR="DimGray"]kk, i have got a powermac G4, added some RAM, installed CD Drive, because it didnt have an optical drive, cleaned it up, and ordered ubantu PowerPC CDs, hopig I will finally have a decent computer in my house . Last Monday i got CDs and prepare to install. Pressed ALT and see Macintosh harddrive (icon), and CD with linux mascot.... Click onto the CD icon, click onto the arrow, screen blinks, and everything freeses, returning to the previous menu. Pleae help , because i know that someone here had a successful experience with doing it.

 i digged out some info, like thise one [https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC), buy as i follow it , it doesnt work and osx boots, then i came over this [http://www.ppcnerds.org/Article207.html](http://www.ppcnerds.org/Article207.html) it mentions something about some "Open Firmware", im not sure what that is, maby some may help me with using it... , anyway i really want to install Ubantu on my Mac, and as a newbie i need some help....

thank you all
[/COLOR][/SIZE][/FONT]
 [IMG]http://www.apple-history.jabluszko.com/support_files/images/models/g4.jpg[/IMG]

---

### Post by spencer on 2005-12-12
Hello, I just installed Ubuntu on a Power Mac G4 too. Instead of pressing "Alt", you can press "C" and see if that works for you, That's what I did and the entire install went perfect! I only had a few minor quirks that I mentioned in another post. Hope that helps.

-spencer

---

### Post by andrewlt on 2005-12-12
[FONT="Comic Sans MS"][SIZE="5"][COLOR="DimGray"]sorry,as i mentioned before, i tried it and mac still booted[/COLOR][/SIZE][/FONT]

---

### Post by andrewlt on 2005-12-12
OSX Stiil Booted*

---

### Post by spencer on 2005-12-12
What if you choose the Ubuntu Installation CD from the System preference pane while you are in OS X. That should boot the Ubuntu CD. I hope that gets you somewhere.

-spencer

---

### Post by andrewlt on 2005-12-12
[FONT="Comic Sans MS"][SIZE="5"]I cant get into OSX, because I don't know the password of the person, who previously owned it, and i can't get hold on him or her... some stupid asian store in vancouver, and now im back in toronto...[/SIZE][/FONT]

---

### Post by andrewlt on 2005-12-12
Thats why i wanto to install ubantu on the 1st place:???:

---

### Post by spencer on 2005-12-12
The last thing I can think of is getting a hold of a Mac os 9 or 10 disk and holding down the "C" button. From there you could erase os x from the drive and afterward install ubuntu on it. The Ubuntu CD should boot the mac with the "C" key down. But, you said holding the "C" key down is not working for you. I sometimes have to hold the "C" key down before I boot the Mac and then press the power button and it will go right in the the startup disk. I don't know what else to tell you, maybe someone else has some ideas if these don't work for you. Good luck!

-spencer

---

### Post by andrewlt on 2005-12-13
[FONT="Comic Sans MS"][SIZE="4"][COLOR="DimGray"]about some "Open Firmware", im not sure what that is, maby it may help...[/COLOR][/SIZE][/FONT]

---

### Post by tmeier on 2005-12-13
My ideas as I think about it.

You can reset the NVRAM from open firmware.  When starting the computer hold down apple-option-o-f.  This will come up with a prompt, let up on the keys and at the prompt type

reset-nvram <enter>
reset-all<enter>

This should restart your computer.  As it just starts to restart hold down the "C" Key.  The computer should find the Cd and boot from it.  If it still does not start from this CD, make sure to try another CD to see if it will boot from it, preferably a Mac OS CD.  Can't think of anything else of the top of my head, but will come back to it again.

---

### Post by andrewlt on 2005-12-13
i tried and clearing of ram didnt work, if i forgot to mention, then the CD unit (drive) is newly installed, it wasn't there when i got the mac. Also clearing of ram just reboots the system and pressing "c" has no affect OSX still boots...

As for another CD i'll try to get one..

Thank you:confused:

---

### Post by andrewlt on 2005-12-13
[FONT="Comic Sans MS"][SIZE="5"][COLOR="DimGray"]oh yeah here are some pictures, if that can help...[/COLOR][/SIZE][/FONT]

---

### Post by andrewlt on 2005-12-13
[FONT="Comic Sans MS"][SIZE="5"][COLOR="DimGray"]oh yeah here are some pictures, if that can help...:smile: [/COLOR][/SIZE][/FONT]

---

### Post by andrewlt on 2005-12-13
some more...please dont ban me for the f one, i was just really angry at the mac, for not working and booting OSX...](*,) #-o

---

### Post by spencer on 2005-12-14
It could be that your CD-Rom drive is bad. Is it new or used? If you recently purchased it and it's not working; you could try exchanging it for a new one from wherever you purchased it.

You could try to change the jumper pin setting on the CD-Rom drive. The pin is located on the back of the CD-Rom drive and should be set in the master position, it may be that it is in the wrong position and the Mac is not reading the CD-Rom drive. Keep trying, someone here I'm sure has got the answer.

-spencer

---

### Post by andrewlt on 2005-12-14
new problems...

first of all it booted perfectly... i was be the mac untill the partitionog phase, then I left, when the partitioning started....Hear the startup noise, mac restarted... Second time boot from CD ... it stops on the kernel welcome, says Welcome to kernel this and this for powerPc full screen of random words, and stops, USB mouse and keyboard don't get power.. wtf is going on...](*,)

---

### Post by spencer on 2005-12-14
Maybe there's something wrong with the CD. If you have another computer, you could download Ubuntu and burn the iso image to disk and then try again with the new cd.

-spencer

---


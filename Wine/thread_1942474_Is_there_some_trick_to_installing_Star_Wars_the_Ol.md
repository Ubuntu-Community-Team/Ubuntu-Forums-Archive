---
title: "Is there some trick to installing Star Wars the Old Republic in WINE?"
date: 2012-03-17
forum: Wine
---

### Post by venom104 on 2012-03-17
Okay here is the thing. I've been trying for HOURS to get SWTOR to install sucessfully on my machine, but I constantly run into problems. The downloadable installer crashes with the error wine: Unhandled page fault on write access to 0x0000000c at address 0x7e6b8ea3 (thread 0027), starting debugger...(when it tries to extract SWTOR customer support.url). And I can't install from the cds, because whenever I (either by using wine eject D: or having the installer do it automatically), the installer (or Ubuntu) can't see the second disk! The second disk DOES NOT MOUNT (I've checked fdisk and /media), I have to mount it manually to get it to work, which is wierd because even if I mount both cds on /media/cdrom...IT STILL DOES NOT SEE IT! Even though I can open it in a terminal and ls the contents of the file.

I've tried installing wine using git ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022)) and installing the patch, so I don't think that is the problem. I've also tried numerous ways of getting the stupid cd to work (even messing around with the D drive in winecfg). 

Has anyone successfully installed SWTOR in WINE, if so how?

---

### Post by venom104 on 2012-03-17
Well this isn't a fix, but a workaround. I tried starting the launcher from my NTFS (windows) partition, and the game actually works! 

Again, it's not a fix, thread NOT solved. I want to blow away my windows partition completely .

---

### Post by schtufbox on 2012-03-18
Copy all the files from the DVD's into a folder in your home dir, call it 'Swinstaller'  (or in fact call it anything you like!)
Install from the folder instead of the dvd's and it'll work fine...mostly!

You MAY have an issue of the launcher not loading/patching properly.  By that I mean it runs, and supposedly patches (but goes dark..you'll know what I mean if you see it) but when you log in, once it gets past the movies it'll crash, if you do, just download the online installer from the game's official site, swtor.com and install it.

It will ask if you want to reinstall using default settings as you already have SWTOR installed, just say yes and it will install with an updated launcher, which will actually update itself this time and the game will then install fine..it will NOT delete your existing install, it just puts a new launcher app in (along with fixlauncher.exe)

Hope this helps :)

---

### Post by venom104 on 2012-03-18
> **schtufbox said:**
> Copy all the files from the DVD's into a folder in your home dir, call it 'Swinstaller'  (or in fact call it anything you like!)
Install from the folder instead of the dvd's and it'll work fine...mostly!

You MAY have an issue of the launcher not loading/patching properly.  By that I mean it runs, and supposedly patches (but goes dark..you'll know what I mean if you see it) but when you log in, once it gets past the movies it'll crash, if you do, just download the online installer from the game's official site, swtor.com and install it.

It will ask if you want to reinstall using default settings as you already have SWTOR installed, just say yes and it will install with an updated launcher, which will actually update itself this time and the game will then install fine..it will NOT delete your existing install, it just puts a new launcher app in (along with fixlauncher.exe)

Hope this helps :)

This sounds like a good idea, but how would I get around the installer asking for another disc? Wouldn't I have to mount an iso and make wine think that it's a drive for this to work (also I heard that the program checks if I inserted a real cd, or if it's just reading from an iso, would cause problems)? Also, as I said before, the downloadable installer keeps crashing, so would using it after installing from the dvds fix that?

Thanks for responding, I honestly think I'd get any help at all, since the wine patch is apparently new.

---

### Post by schtufbox on 2012-03-18
If you are copying the contents of all 3 dvd's into a folder and then installing from there it won't ask for any DVD at all. That's how I had to install it :)
I didn't even have any of the DVD's in the drive when I installed.

---

### Post by ogoudge on 2012-04-27
Do you guys know if you have to install the game in WINE to get it to work? I have a 2nd partition I have the game backed up on for windows. This way I do not have to re-install and update if I reload windows.

My issue I am currently having in Ubuntu 10.1 is that the launcher loads fine however a few seconds later it suddenly closes.

---


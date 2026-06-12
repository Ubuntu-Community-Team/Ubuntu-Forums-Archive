---
title: "HOW TO - FLASH FOR 64bit USERS"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-10-18
Okay K/Ubuntu users some helpful advise from the friendly team of SuSe 10 users. This is how you get flash to install for 64bit Linux:

STEP 1: Download the linux(32bit) flash installer from Macromedia [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

STEP 2: In "flashplayer-installer", edit line 249 from "i[3456]86)" to "i[3456]86|x86_64)"

STEP 3: Run the installer and install into your mozilla compatible browser.

STEP 4: Open Firefox or Thunderbird and YES!!! She works.

BEAWARE!!! This doesnt work for all setups, works on mine, so have fun!!

---

### Post by Dr. Nick on 2005-10-19
Edit- Didnt work here :( Those who have sucedded what was the install path?, I also copied the files directly to /usr/lib/mozilla-firefox but like I expected it didn't work.


I am DEFINATELY trying this out tomorrow on my amd64, I will post back with results. If it works I will probably die laughing since its so simple and complex at the same time, glad I am the 1st to respond as I found this by looking at unanswered post and wouldnt have seen it otherwise, have you posted in the Ubuntu 64bit forum aswell?

Glad you got it working on yours, its the one annoyance I have with 64bit linux

---

### Post by Navyblue on 2005-10-19
My Firefox didn't pick it up. Not sure if it is having conflict with the gplflash plugin, I don't know how to uninstall it :p.

---


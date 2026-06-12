---
title: "Dual Boot OSX/Ubuntu Information Needed!!"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrstimpson on 2006-03-26
Hello All, 

I've installed dual boot OS's on windows machines before and installed an earlier ubuntu on my pc laptop. But last year i sold all my pc stuff and bought a mac (which I'm still learning) I basically am going to recive a ubuntu dvd in a few days and would be greatful if anyone has a guide or a link for information on how to install osx & ubuntu on my mac mini. I have an external harddrive (usb) and a internal 80gig, 512 ram ppc g4 1.2ghz computer. I don't mind backing everything up and doing it all from fresh. is it easy to set up dual install or complicated on macs? any help or information greatfully - Sam

---

### Post by TrinitronX on 2006-03-26
I haven't tried out a mac install of ubuntu yet... since I don't have one :D.  But just to be helpful... here's something that looked a bit promising:
[http://www.journalhome.com/billhutchison/18421/](http://www.journalhome.com/billhutchison/18421/)

It's got some other tutorial links at the bottom of the article that looked helpful too.

It looks like he's installing the different OS's on two partitions on the same harddrive.  If you want... you could use each of your hard drives to house the different OS's.

---

### Post by jdp on 2006-03-26
No need to wipe and reinstall OS X, just read [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=89960) and don't skip the first step to disable the journal under OS X.  Also, be sure to have enough free space for your install.  You only need 5GB to do much in Ubuntu.  More is gravy.

---

### Post by shawnhcorey on 2006-03-26
I have recently install Ubuntu on my PowerBook G4. You can read all about it on my Wiki page: [https://wiki.ubuntu.com/Shawnhcorey](https://wiki.ubuntu.com/Shawnhcorey)

I made some mistakes but hopefully you can avoid them. Good luck.

sc

PS: Thanks jdp for your help.

---

### Post by robo_creeler on 2006-03-27
[QUOTE=mrstimpson]Hello All, I've installed dual boot OS's on windows machines before and installed an earlier ubuntu on my pc laptop. But last year i sold all my pc stuff and bought a mac (which I'm still learning)[/QUOTE]

congratulations!

to clarify, you only need to turn off journaling if you are installing onto the same partition - right?

---

### Post by linear on 2006-03-27
You need to turn off journaling only if you want to **resize** the existing partition - so you can create empty space for the Ubuntu partition(s).

---

### Post by ssam on 2006-03-27
[QUOTE=shawnhcorey]I have recently install Ubuntu on my PowerBook G4. You can read all about it on my Wiki page: [https://wiki.ubuntu.com/Shawnhcorey](https://wiki.ubuntu.com/Shawnhcorey)[/QUOTE]

sounds like you had rather a rough time installing. i have always been able to change the host name in the install and have things work.

did you do the expert install? that is usually not a good idea (in the enough rope to hang yourself sort of way).

---

### Post by mrstimpson on 2006-03-30
I decided in the end to backup my mac and install a fresh copy of osx I used the utility in it to partition the drive one 60gig and 1x8.5gig (for ubuntu) OSX installed fine. Im rather lacking in too much detail here before I go on, I inserted the ubuntu cd it asks what partition i wish to install on I selected the 8.5gig it installed on the 8.5 gig partition restart computer boots into ubuntu. I cant find osx now no dual boot option? just a tiny harddrive with ubuntu on. was there an option i missed in the installing process that would of given me the dual boot option or does it detect an other os? I have no clue but tomorow is another day and another format and reinstall lol and constructive suggestions? greatfully --- Sam

I'm really impressed with this black ubuntu theme OS looks great!

---

### Post by mrstimpson on 2006-03-30
oooooooh maybe I missed out an important step:


   4. Chose to boot from CD (Hold C upon boot)

   5. Follow the install directions until you get to partition tables

   6. Go to Manually edit partition table and delete the partition you created for your  Ubuntu install during the Tiger install, but leave the Tiger partition alone.
--------------------------I didnt delete partition-------------------------------====

   7. Go back to the main partition table and select "use largest free space" for your installation.
---------------------------didnt do this either---------------------------

   8. Sit back and wait while it runs and installs your dual boot 

I should read more before post bad habbit - thanks for the info though  ---cheers

---

### Post by dailyplanet on 2006-03-30
[http://www.ubuntuforums.org/showthread.php?t=134967&highlight=dual+boot+os]("http://www.ubuntuforums.org/showthread.php?t=134967&highlight=dual+boot+os")
My thread on how to dual boot OS X and Ubuntu. Hope it helps.

---

### Post by AlphaMack on 2006-03-30
I used Disk Utility on my OS X installation CD to divide my HD into 3 partitions with OS X occupying the first and Ubuntu the second (until I later learned that I could easily mount the other partitions via /etc/fstab).  The Ubuntu partition was formatted as free space so when the time came to install Ubuntu, the partitioner automagically rationed out space for boot, swap, and /.  My only issue is that I should have created a /home!  Then again, I'm not too worried about losing it in a FUBAR incident since all of the important stuff is on the last HFS+ partition anyway.

OS X has to go first and be the first installed.

---


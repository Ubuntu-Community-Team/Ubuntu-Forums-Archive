---
title: "photoshop activation"
date: 2008-01-28
forum: Wine
---

### Post by SyCo123 on 2008-01-28
When trying to activate i get a disk full error.

So I have the latest version of wine, and according to winehq CS2 should install no problem but the bug thats reported as closed is still affecting me.
```
simon@master:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
simon@master:~$ 
```

and here [http://bugs.winehq.org/show_bug.cgi?id=10018#c16](http://bugs.winehq.org/show_bug.cgi?id=10018#c16) it says at the end the bug is fixed.

> nishyl, just use wine-0.9.54 as described at
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)
It already supports photoshop cs and cs2
activation.[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

I have no entry for wine in applications>add/remove so is it possible to check the version number of wine?

---

### Post by Jad on 2008-01-29
This should do the trick 
> aptitude show wine | grep 'Version:'

---

### Post by SyCo123 on 2008-01-29
Thanks, I'll check at lunchtime. I have a feeling I had a different repository set from another tutorial so it's possible the version is old. At least now I can find out one way or the other!

---

### Post by SyCo123 on 2008-01-29
Yep the version was out of date so found the correct wine repos and have the corect version now.

However I now have an error saying theres no serial number so it closes. I tried to uninstall all the adobe programs in Wine but it wont install anything. I tried uninstalling wine too but the programs remained there even though wine was gone.

How can I remove all wine programs and start over fresh?

---

### Post by hikaricore on 2008-01-29
```
sudo apt-get remove --purge wine
```

or simply remove the entire wine configuration folder and remake it:

```
rm -R ~/.wine
wineprefixcreate
```

---

### Post by SyCo123 on 2008-01-29
cool thanks I'll have a go when I get home.

---

### Post by SyCo123 on 2008-01-30
I've run the commands hikaricore  and the .wine folder is gone (i did view hidden files to be sure) however there is still an entry in Applications for Wine and even a programs sub-folder that goes to Photoshop.

Also it looks like  have to install wine to get wineprefixcreate
simon@master:~$ wineprefixcreate
The program 'wineprefixcreate' is currently not installed.  You can install it by typing:
sudo apt-get install wine

Which is Ok but I'd like to remove everything wine and photoshop and start again fresh.

---

### Post by SyCo123 on 2008-01-30
I had a quick google and saw it looks like it was just a menu renemant, removable by right clicking Applications and edit So I guessed it might work if i try to reinstall everything.

So installed wine again and it looked good so ran setup.exe again and activation went right this time. Looks like I'm good to go.

Thanks for your help!

---

### Post by SyCo123 on 2008-01-30
agh! Just when I thought I was done....

I got an error complaining  "unable to continue because of a hardware or system error" .
So i find a fix of deleteing the Photoshop CS2 Prefs.psp file which looked like it has fixed it.I can't help but think this file will come back and with it the problem.

Now i try to open a PSD file and "could not complete your requet because of a program error" I can open a JPG no problem I can open a new image and save it as a PSd but cant open it again. i can't open the PSD (gimp created) i want to work on either.

Anyone experienced similar and know the fix?

---

### Post by michaelzap on 2008-02-01
Sounds like you neglected to install the Times32 font before Photoshop. You might have to purge Wine again before it will work now, You can get it from here:

[http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)

---

### Post by SyCo123 on 2008-02-03
Thanks Michael. i guess when I purged Wine the previous times font install went with it to.

So I purged wine again, installed the times font, renamed the adobe folder to adobe_old and reinstalled PS. It appears to work as planned now.

I've even rebooted to see if it would still work and it still good. Hopefully this is now a good install and working fine.

Thanks again all of you for all the assistance.

---


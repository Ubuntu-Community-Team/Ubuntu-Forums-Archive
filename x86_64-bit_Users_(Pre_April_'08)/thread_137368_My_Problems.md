---
title: "My Problems:"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chillaxed on 2006-02-27
ok i have a list of problems here and now that i'm getting the feel for linux a little more i am playing around with it now.

ok i have no clue how to install nvidia drivers

i went into device manager and NOTHING is recognized except for a few prehiperals

i don't think it supports nforce 430

i was wondering if i could run ut2004 from the windows partition but have it patched to run it on linux

thats all i have so far. i just really need to know how to install drivers for now step by step 

thanks guys!:mrgreen:

---

### Post by earobinson on 2006-02-27
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

---

### Post by Chillaxed on 2006-02-27
WOW just to install a driver?

my god. i'll try :(

---

### Post by Chillaxed on 2006-02-27
i tried just typing in the location of the file and the file name and it started the installer but then said "must use root" or something like that i forget

---

### Post by RAOF on 2006-02-28
Simple summary of how to install the driver (the long version is in that thread linked):

Run, in a console:
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo /etc/init.d/gdm restart

```
Enter your password, and you're done.  The last step will log you off, and restart your GUI to load the drivers.  Don't have any unsaved work open at that point ;)

If this doesn't work, check the thread.

---

### Post by earobinson on 2006-02-28
you could also try easy ubuntu or Automatix

---

### Post by rplantz on 2006-02-28
[QUOTE=earobinson]you could also try easy ubuntu or Automatix[/QUOTE]

The notice at the top of the Automatix page ([http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)) says that it does not support 64-bit.

If you wish to keep it simple, you may wish to run 32-bit at this time. I'm running 64-bit, but I enjoy playing around with this stuff, am fairly knowledgeable about computers in general, and have the time to do it. If I were still working and needed to get things done, I would run 32-bit.

---


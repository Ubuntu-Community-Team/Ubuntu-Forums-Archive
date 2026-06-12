---
title: "Picasa won't start (because regedit fails)"
date: 2008-10-12
forum: Wine
---

### Post by jazzgossen on 2008-10-12
I have been using Picasa before, but recently it won't start when running the default starter wrapper. 

I'm using Picasa 2.7 on Ubuntu 8.04.

If I run "wine ~/.picasa/drive_c/Program Files/Picasa2/Picasa2.exe", it works. However, using the starter script in /usr/bin/picasa fails without error messages. 

I have found the error to be on line 175 in the script: 
```

"$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

```
This returns 1, which causes the script to exit. And when I run regedit, I can see that there is no key HKEY_USERS\\S-1-5-4\\Software\\Google so it exits for a good reason.

But how can I work around this? I tried reinstalling Picasa from Google's repository.

---

### Post by paris_alex on 2008-10-12
why don't you just use Picasa for Linux? I works great on Ubuntu.

---

### Post by jazzgossen on 2008-10-13
I use the version from "deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free"

Is there another more specific to Linux?

---

### Post by hananias on 2008-10-14
I'm having problems with Picasa also.  At first it was working fine, I loved it...way better than f-spot.  But now When I start it, the Picasa 3 beta splash screen shows up, but then it goes away (as if the program is about to come up) but it doesn't... I uninstall/ reinstalled and still same thing.:confused:
  I'm running gOS (pretty much ubuntu 8.04 hardy)

Please any help I will appreciated so much.  I actually need this for work:(

---

### Post by jazzgossen on 2008-10-14
> **hananias said:**
> But now When I start it, the Picasa 3 beta splash screen shows up, but then it goes away (as if the program is about to come up) but it doesn't... 


My question was about Picasa 2.7, but what I did for debugging was to locate the starter script ("which picasa" returned "/usr/bin/picasa"). Then I edited the script in a text editor (make sure to back it up first) and added echo statements all over the place to see where it failed. Try to do the same and see if you also have the regedit problem.

---

### Post by humpiedumpie on 2010-02-13
I am running 9.10 Ubuntu and installed 3.0 Picasa. It will not start. It was ok with the previous version, never had problems.
I am waiting for some tips to solve it.

Tx

---

### Post by humpiedumpie on 2010-02-13
I have just uninstalled Picasa 3.0 and downloaded+installed Picasa 2.7 deb. Now it will not start this version as well. Now I have nothing. This is bad. I love Picasa and I would like to get it working again. Please help. Tx

---

### Post by humpiedumpie on 2010-02-13
As indicated previously I installed picasa_2.7.3736-15_i386.deb, but this seems to show exactly the same problem as with Picasa 3.0. I would like to try older versions of Picasa. Maybe 2.6. Anybody knows how to get the different versions? Tx

---

### Post by stephenmac7 on 2010-04-05
[http://ubuntuforums.org/showthread.php?t=1447530](http://ubuntuforums.org/showthread.php?t=1447530)

---


---
title: "Steam installation"
date: 2011-12-13
forum: Wine
---

### Post by arnab_das on 2011-12-13
I'm using 10.04 and using the latest version of wine 1.3.34

i know many users have successfully installed steam but unfortunately no amount of tweaking is working for me. steam does install everything but crashes as soon as i launch it.

please help!

---

### Post by Dlambert on 2011-12-13
I would try playonlinux, it has several of the files needed to run steam on linux built into its install script, once installed (POL) just hit install and find steam on the list.


[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by arnab_das on 2011-12-13
Thanks. 

I did try that. The installation proceeds smoothly but then when I launch steam it crashes.

should i be installing any other dependencies? Or configuring wine?

---

### Post by ergo-proxy on 2011-12-14
> **arnab_das said:**
> Thanks. 
 
I did try that. The installation proceeds smoothly but then when I launch steam it crashes.
 
should i be installing any other dependencies? Or configuring wine?
 
Check winehq for instructions.

---

### Post by P-I H on 2011-12-14
I use winetricks to install steam and this has worked so far both on 11.04 and 11.10. On this system I use 11.10 and wine version 1.3.32.
You will find steam when you select **Install an app** in the Winetricks menu.

---

### Post by guyver_dio on 2011-12-14
i had the same problem, i tried playonlinux, completely removing wine and playonlinux and starting again, same problem. I think I tried every recommendation and still no luck, I ended up getting the shits and reinstalling ubuntu lol. PlayOnLinux will give you debugging information and tell you why it's crashing if you turn that on, but even with that I couldn't figure out what it's problem was, kept telling me it could not find winemenubuilder in a certain directory so I went to that directory to see if it was there and it was.... tried replacing the file with another winemenubuilder file, same thing. After resinstalling ubuntu, instead of installing wine myself I just installed playonlinux, and do everything through that, it'll download the appropriate version of wine for a given application and is just a better way of managing things.

Thinking about it some more, one thing I didn't check was environment variables, try uninstalling wine and anything related (playonlinux etc...) then check to see if any relevant environment variables are gone. If there's some wine related things there get rid of them then install playonlinux.

---

### Post by arnab_das on 2011-12-15
okay solved it.

i would strongly recommend following the procedures mentioned here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=67108](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=67108)

now steam works flawlessly. thanks for the help!

---


---
title: "screen rez problem"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by virtualsnyper on 2007-02-13
hey a;;. I wanna say thx for helping me out. I love that linux has a tight community :P. I was wondering if anyone would know why I couldn't get my screen resolution above 1024...I have a 7900gs, im running edgy x64. Nvidia drivers installed....what gives?

---

### Post by agamotto on 2007-02-13
You most likely need to do the following:

start your system, and do a console login from your sessions menu
login at the text prompts

sudo apt-get update
sudo dpkg-reconfigure xserver-xorg

This will walk you through setting up your graphics options.  After a few screens asking you about your video card, keyboard, mouse... you will see a screen that will let you choose which resolutions are available.  This should fix your problem.
After completing this - 

sudo reboot

Hopefully, your system will come back, and you can choose your new resolution from your settings menu.

Ta

---

### Post by John.Michael.Kane on 2007-02-14
@virtualsnyper if your still having resolution issues have read over this [http://ubuntuforums.org/showpost.php?p=1691257&postcount=2](http://ubuntuforums.org/showpost.php?p=1691257&postcount=2).  

Edit to fit your needs.


Note: you may need your monitor/lcd manual as well.

---


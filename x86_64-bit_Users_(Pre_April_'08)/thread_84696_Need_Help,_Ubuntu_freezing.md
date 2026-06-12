---
title: "Need Help, Ubuntu freezing"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by leinad1313 on 2005-10-31
Okay I really dont like to post messages because I always feel that the answer is out there somewhere.  However after 2 weeks of trying to get Ubuntu 5.04 64 and 32 bit to work on my laptop I am still not able to access the X11 system.  I bootup using grub and can get to the login splash screen.  The problem is I can not actually initiate a session in gnome or kde.  I log in and then the system hangs at start-up.  I get the first gnome box but none of the little icons come up and the music plays like a broken record.  The first thing I thought was maybe gnome was corrupt and since I dont like Gnome anyway I booted into the recovery mode, changed my aptitude repositories and installed kde.  After installing kde I booted back into normal mode, click the select session box and as soon as I choose kde the system hangs everytime.  The only thing that I can think of now is that when I installed Ubuntu the installer would crash to a blank screen within a minute from the start.  I did some research and found that I could get all the way through the normal and the expert install modes if I used the argument "vga=771".  I think this has something to do with my X11 system crashing however if I dont add the argument I cant get through the installation. 

I would really appreciate any help in this, since I am being forced to use my Windows partition and that is just not cool. 

Thanks a bunch

---

### Post by NickB on 2005-10-31
If you are using the ati driver in /etc/xorg.conf, add:

Option "NoAccel" "true"

Nick

---

### Post by leinad1313 on 2005-10-31
I checked my Xorg.conf and it was actually located under /etc/X11/Xorg.conf and I didnt see any area that I should add that value for.  If you could can you post an example of your Xorg.conf????  I dont have the new drivers for my radeon card but the Xorg.conf recognizes it as the correct model, if I need to install new drivers could you show me an example of how to get those using only the command line, I am relatively new to linux (1 yr only) and havent gotten fully used to working only in the terminal.  

Thanks

---

### Post by NickB on 2005-11-01
I'm sorry, I did type the path wrong, it is /etc/X11/xorg.conf.

The relevant section would look something like:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "radeon"   <-- maybe you have "ati" here
        BusID          "PCI:1:5:0"
        Option          "NoAccel"               "true"

Note that this may not be *exactly* the same for you, but you can see where the line would go.  Good luck.

Nick

---

### Post by leinad1313 on 2005-11-01
sweet, thanks man.  I will try that out tonight.  I am having to switch between my Windows, and linux box so I cant try it out right now.  But I will get back with you on how it goes.

---

### Post by leinad1313 on 2005-11-02
Hey thanks man I added that option line and ubuntu was able to log in correctly.

---


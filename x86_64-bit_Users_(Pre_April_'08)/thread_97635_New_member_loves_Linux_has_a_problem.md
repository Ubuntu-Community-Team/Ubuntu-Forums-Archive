---
title: "New member loves Linux has a problem"
date: 2005-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by time on 2005-12-01
I just installed Breezy Badger and now I have some mouse and window problems. The right button doesn't work so I can't unmount volumes etc, The left button highlights and clicks in a window from outside the window and sometimes just doesn't work at all.  Any help will be appreciated. Thanks  Time

---

### Post by Digitallysick on 2005-12-01
what type of mouse do you have??

---

### Post by az on 2005-12-01
I had something like that happen a long time ago.  The mouse cursor on the screen and the mouse hotspot on the screen were not in sync.

I resolved it by making the X server use a software cursor.

It is described here:

[http://www.ubuntulinux.org/support/documentation/faq/hwcursor](http://www.ubuntulinux.org/support/documentation/faq/hwcursor)

Option          "HWCursor"      "off"

Or you can use

Option    "sw_cursor"   "true"

I think it is the same effect.  

This may or may not be your problem.  I dunno.

---

### Post by alex_esplin on 2005-12-04
Hi everyone, this is actually a computer I built for my Dad and installed Ubuntu on.
I don't personally have an amd64 system myself, so I don't know much about it, but here's the problem.

The initial install worked just fine for about 8 hours.  I then tried to install the fglrx drivers, but I did this in two chunks of time about 3-4 hours apart.  about halfway through the second chunk of time, I noticed that alt-tab no longer worked to switch between windows, and the mouse would no longer function inside a window that had been open for a while.  So I used apt-get remove to remove everything I had added for fglrx and copied the old xorg.conf file back from where I had backed it up.  However, this didn't fix the problem, nor did a complete re-format and re-install that my dad did after I had come back home.  Has anyone experienced anything like this?  I don't think it's a hardware failure as the computer has worked just fine under Hoary for 5 or 6 months, unless it is something that just went wrong while I happened to be there.

I don't really know what to search for to do much research myself because I have never used an amd system before.

Thanks

---

### Post by time on 2005-12-05
Thanks, I'll look into that

---

### Post by time on 2005-12-05
[QUOTE=Digitallysick]what type of mouse do you have??[/QUOTE]

Thanks for your reply. I took the computer apart-put it back together bought a new mouse and it' s worked since then. thanks again

---


---
title: "X-Fi Help"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by zoommy99 on 2008-02-11
Hey.  I am trying to use method 2 on Nullhead's how-to for xfi driver installation.  It all works for me fine and dandy until I go to actually installing the drivers.

I do ./configure CC=gcc-3.3

then sudo make (won't work without sudo)

then sudo make install.

When I do sudo make install it goes until it reaches this line
/bin/sh: line 9: /sbin/chkconfig: No such file or directory
Then it completely freezes.  Everything stops, no mouse movement, nothing works, the scroll lock and caps lock LEDs on the keyboard blink, and I have to hold down power button to turn it off.  I retried the installation multiple times.  I even reinstalled the custom kernel as well.

Another thing, I used sudo make install -d to print a whole bunch of info about what is happening as it happens.  The last few lines before the system freezes goes like follows

must remake target 'load'
putting child 0x00656840 (load) on PID 8825 on chain
live child 0x00656840(load) PID 8825

note that is not "exactly" how it goes because I couldn't copy and paste it because my system was frozen.

I really want the sound to work.  This is really the only thing holding me back from using ubuntu (or kubuntu in my case) as a more permanent OS.

Thanks

---

### Post by Sockerdrickan on 2008-02-11
I am happy to say that X-FI will be supported in the alsa driver in one of the next coming releases

---

### Post by Yellow Pasque on 2008-02-11
You should try the X-fi support in OSS4. It's a better sound system than ALSA anyway. The link is in my sig.

---

### Post by radamo on 2008-02-16
> **Temüjin said:**
> You should try the X-fi support in OSS4. It's a better sound system than ALSA anyway. The link is in my sig.

Wow... thanks... I am going to reinstall Ubuntu and give this a try.
RA

---

### Post by NullHead on 2008-02-16
> **Tux0r said:**
> I am happy to say that X-FI will be supported in the alsa driver in one of the next coming releases

How do you know this? I've looked on the site and I haven't noticed anything, but i'm not getting any news letters or anything special. So maybe it was said somewhere else?

---

### Post by Sockerdrickan on 2008-02-16
Phoronix.com

---


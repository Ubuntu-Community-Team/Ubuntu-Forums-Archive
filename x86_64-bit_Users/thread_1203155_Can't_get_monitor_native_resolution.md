---
title: "Can't get monitor native resolution"
date: 2009-07-03
forum: x86 64-bit Users
---

### Post by dpell on 2009-07-03
I'm using an LG Flatron W2252TQ 22" LCD monitor and just switched to Ubuntu 9.  My desktop has a Geforce 8600 GT graphics card.  Ubuntu seems to have recognized the video card (it makes me use the nVidia software to make display changes rather than Ubuntu), but for some reason I can't get it to output my monitor's native resolution (1650 x 1080).  The most I can get is 1152x864.  

I've also noticed that the nVidia software that Ubuntu installed is calling my monitor CRT-0.  That doesn't seem right since this isn't a CRT...or does that stand for something else here?  

Does this sound like an issue with the video card driver or something else?  

Do I have to use the nVidia software?  I was fine on Windows not installing any extra software and just using Windows to adjust the display resolution.

---

### Post by JDShu on 2009-07-03
have you tried entering your desired resolution in the display subsection of the screen section in /etc/X11/xorg.conf?

---

### Post by giancast on 2009-07-03
I am having the same issue and have not changed the etc/X11/xorg.conf because in the file it says:

"Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)"

"# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored."

also I have no idea as to what to put in there since the man pages are for me very cryptic.

Eventually I will try and see if I can figure out what to put there and hopefully I wont crash my install.

---

### Post by JDShu on 2009-07-04
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

The above link explains how to do some basic modifications to xorg.conf. Check out the part under the heading "Adding custom modules".

---


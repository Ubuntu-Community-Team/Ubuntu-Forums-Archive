---
title: "Problem with ATI and OpenGL"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Disablez on 2005-11-21
Hi!
I recently tried to add 3D Acc. to my comp (Acer Aspire 1501 with a Radeon 9600 (Mobility M10). So I installed the ATI drivers with the installer from their website. 8.19.10-x86-64, to be precise.

Everything went ok, configured the xorg.conf file and rebooted with no problem (but for the mouse having a strange white stripe under it during the initial screen of KDE (I installed the kubuntu-desktop), or everytime I click on the Gnome menu bar).

Anyway, I tried to run supertux, just for trying, and it doesnt work. so I tried to run it from konsole, and I get a message saying that it couldnt find the shared library libGL.so.1 .

I found the library, /usr/X11R6/lib/libGL.so.1.2 ,and started making ln -s in all possible /lib , /lib32, /usr/lib, /usr/lib32, (lib64 are links to lib, so...) even I have tried with creating linked folders /usr/lib/fglrx , /usr/lib/ati-fglrx ... with no luck.

Can anyone tell me where is my system looking for them ? I tried for hours in Google but had no luck finding a solution... :(

---

### Post by DRF on 2005-11-22
I posted a reply to a similar question at this thread:

[http://www.ubuntuforums.org/showthread.php?t=90575](http://www.ubuntuforums.org/showthread.php?t=90575)

However I noticed that there was an update for the ATI drivers today when I ran Update Manager so that might have fixed this problem so check that it's not been fixed allready before looking into the solutions I found previously.

The original thread from when the problems first started to occur is at:
[http://www.ubuntuforums.org/showthread.php?t=75585](http://www.ubuntuforums.org/showthread.php?t=75585)

I run the drivers in synaptic rather than downloading new ones so your problem might be different. There have been quite a few similar posts in this forum if you look though the earlier threads. Seems that about a week before the breezy release a few ATI problems occured but some people in the forum managed to find a couple of ways around them.

Hope this helps,

Daniel

---

### Post by Disablez on 2005-11-22
Thanks for your help.

I kept on trying but in the end the most I got was mesa GL, so I gave up and installed the slightly older ones directly from synaptic, like in my 32 bit partition, everything is ok now, and at nice speed :) .

---

### Post by Septor on 2005-11-23
The ATI installer won't work on Breezy.  Check out the Ubuntu HOWTO at: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

note that on 64bit systems you might need the libdri.a workaround mentioned at [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

---


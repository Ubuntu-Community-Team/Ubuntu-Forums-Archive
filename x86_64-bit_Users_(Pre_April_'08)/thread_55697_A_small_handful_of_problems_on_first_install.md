---
title: "A small handful of problems on first install"
date: 2005-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Khoram on 2005-08-09
Hi folks,

I was using Ubuntu on an old P-III. Recently built myself a new AMD 64 machine and installed Ubuntu 64-bit. I'm having a few problems that I was hoping someone could either help with or point me in the right direction. 

1. CPU frequency scaler panel applet shows my processor running at 55%... but /proc/cpuinfo shows correctly. Just a display bug in the applet, or is my machine being scaled back? This works fine in an install of Gentoo/AMD64 I have on the machine. 

2. No sound. Using SB Live 24 bit. I've seen a couple threads so I have some stuff to try, but that will have to wait til tomorrow.

3. Network Activity panel applet. Shows a big red error symbol over it and clicking it shows a dialog that explains the error as SIOCGIFFLAGS error: no such device. Any ideas? Again, something that is working fine in Gentoo.

4. No volume control (related to sound not working?)

Any ideas?

---

### Post by DancingSun on 2005-08-10
How do you get the frequency scaler applet to work?  I couldn't get any frequency reading from it.  Does powernowd have to be running and activated for it to work?  I heard powernowd causes some problems for 64-bit systems, has anyone have any problems with it?

My network activity panel works fine, however.  Is your network connection working?  What kind of network device do you have? I have the integrated network connection from a NForce4 Ultra chipset.

---

### Post by Khoram on 2005-08-10
[QUOTE=DancingSun]How do you get the frequency scaler applet to work?  I couldn't get any frequency reading from it.  Does powernowd have to be running and activated for it to work?  I heard powernowd causes some problems for 64-bit systems, has anyone have any problems with it?

My network activity panel works fine, however.  Is your network connection working?  What kind of network device do you have? I have the integrated network connection from a NForce4 Ultra chipset.[/QUOTE]


Hmm, I am not sure about the powernowd, will have to research. How did I get it to work? Well, I'm not sure it IS working ;) All I did was add it to the top panel in my Gnome desktop.

Yep, I'm sure the network connection is working, I'm using it right now. I also am using an nForce4 integrated NIC.

---

### Post by DancingSun on 2005-08-10
I vaguely remember encountering the error message you did on the Network Activity applet, or maybe it's just my imagination....  In either case, make sure you selected eth0 in the "preference" of the Network Activity applet.  If that still doesn't work, try restarting.

---


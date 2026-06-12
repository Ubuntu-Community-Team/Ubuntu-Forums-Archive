---
title: "Seamonkey installation &amp; 64bit Kubuntu 6.10"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by derGhostrider on 2006-12-24
Hi!

I read the thread "HOW TO install SeaMonkey" ([http://ubuntuforums.org/showthread.php?t=186011](http://ubuntuforums.org/showthread.php?t=186011)) and followed the instructions but it does not work for me.
I use the 64bit version of Kubuntu 6.10 Edgy and hope that someone may give me a hint what I am doing wrong because the already mentioned HOW-TO does not work for me. :( 

The first step from the HOW-TO, running ./seamonkey-installer with sudo or as root, gives me the following error:
> ./seamonkey-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

The libgtk-x11-2.0.so.0 is located in usr/lib/

It's some time ago that I used Linux (1996) so my knowledge is a little bit degraded... But maybe you have an idea what I can do to get seamonkey installed.

Thanks in advance!

Ghostrider
------------------------

P.S.: Next problem to solve: WINE installation. I'll post the detailed problems after the first one from above is solved.

---

### Post by Simpele on 2007-01-26
What I do is download the gzip file for Linux x64 from [http://www.mozilla.org/projects/seamonkey/releases/1.0.6.html](http://www.mozilla.org/projects/seamonkey/releases/1.0.6.html) and then move the contents to a convenient folder from where I run the binary.

---

### Post by kuja on 2007-01-28
Debian 101:

> ./seamonkey-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
dustin@terra:~$ dpkg -S libgtk-x11-2.0.so.0
ia32-libs-gtk: /usr/lib32/libgtk-x11-2.0.so.0.1000.6
ia32-libs-gtk: /usr/lib32/libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgtk-x11-2.0.so.0.1000.6
dustin@terra:~$ sudo aptitude install ia32-libs-gtk

---

### Post by derGhostrider on 2007-01-28
Hi!

Thanks for the (late) replies... I think that I'll try it this evening once again. On the other hand I recognized that Seamonkey will come with some additional "features" that I don't even want to have. I just want a Browser + Mailclient. No HTML-Composer stuff or additional functionality. Nevertheless I want to get it working. Even if I'll remove it right after the successful installation. :D

---

### Post by derGhostrider on 2007-01-28
> ghostrider@Opteron:~/Desktop$ dpkg -S libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgtk-x11-2.0.so.0.1000.6
ghostrider@Opteron:~/Desktop$
Hmmm... looks a little bit different than it looks at your system.

---

### Post by kuja on 2007-01-28
Oops, I guess it would. Drat.

---

### Post by Simpele on 2007-01-29
In the meanwhile, there's a 64-bit version of Seamonkey 1.1.

---

### Post by derGhostrider on 2007-01-29
**SUCCESS!**
This posting is done with Seamonkey 1.1 (64bit).

After downloading the 64bit version it was quite easy to do the rest. I just had to add a library: "Libstdc++ 5". Version 6 was already installed but that was not enough for seamonkey - it required the older version.

Thanks to all of you for your help! :)
Now I'll check if I'll prefer using Thunderbird & Firefox or just Seamonkey.

----------------------------------------------
Edit:
During the installation and when I start seamonkey I get these errors:
> 
ghostrider@Opteron:/usr/local/seamonkey$ ./seamonkey
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Nevertheless everything seems to work fine...

---

### Post by kuja on 2007-01-30
derGhostRider: you get those because of the wacom devices in your X configuration (/etc/X11/xorg.conf). They can be ignored, or, if you're annoyed by them, you can remove those entries from the /etc/X11/xorg.conf, seeing as you apparantly don't have the wacom stuff anyway.

---


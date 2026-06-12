---
title: "VLC reboot my laptop"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-10-16
Hi ,

i installed from synaptic VLC for Breezy , i think was the 32 bits version of VLC because i don't know how to know when you install a 32 bits package or amd64 package from synaptic.

Well , the version of the package is vlc 0.8.4-svn20050920-3+hal0ubuntu3 and i can't watch any video , i can play some music , but i can't play video , when i try to play video , my laptop reboots.

Any solution?

Another question is that in [http://nightlies.videolan.org/](http://nightlies.videolan.org/) i see an AMD64 packages for Debian , why not there are available a VLC AMD64 packages in ubuntu repository ?

---

### Post by RAOF on 2005-10-16
First, if you're running the AMD64 version of Breezy, (almost) everything you install through synaptic will be a 64-bit package.  (I believe that openoffice 2 is an exception.  I don't know if anything else is).  So, the VLC you installed **is** a 64-bit version.

Also, if I remember correctly, the version of VLC in the repositories has very incomplete support for video - this was due to licensing issues.  It might have been fixed before release, I don't know.

Rebooting your laptop seems like an extreme error :).  It might help us to help you if you could look in the system logs (applications->system tools->system log) and see if any errors occur just before it reboots (check the times).

Also, you could try changing the VLC video output - that's under preferences.  Try each one in turn, and see if there's one that doesn't reboot your laptop :)
If none of them work, you can try enabling advanced settings (in VLC) and fiddling with the advanced settings of the video outputs...

---

### Post by JuanC on 2005-10-17
It works !!!

I change Video Output from Default to X11.

Thanks.

---


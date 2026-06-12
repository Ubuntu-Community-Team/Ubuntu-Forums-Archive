---
title: "She Won't Sutdown"
date: 2006-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by charlie. on 2006-11-16
My Ubuntu-Edgy (gnome, EM64T) box is displaying typical Windows 98 behavior - it wont shutdown!

Yes, that's right folks, it wont shutdown. I click the shutdown button and gnome closes, the shutdown screen appears and some progress bars move around (some of them backwards) but after the progress bars stop moving, it just sits showing the Ubuntu logo and a few small, vertical lines - forever!

Any ideas?

---

### Post by ciscosurfer on 2006-11-16
Depends on which kernel you are using.  Kernels before 2.6.17 have had issues with full shutdown or reboot.  With older kernels, it was always necessary to manually shutdown and reboot.  Try dist-upgrading if you're using Edgy so that you can get the most upgraded kernels.  Otherwise, you can always manually shutdown when it comes to that screen and everything has stopped.

---

### Post by charlie. on 2006-11-16
I am using edgy and my kernel is 2.6.17.

Reboots work fine.

Manually holding in the button does turn the PC off, I have been using it when I get to that screen and everything has stopped. It's a pain in the arse, but it works.

If I dist-upgrade'd on Edgy, where would that put me? I thought Edgy was the latest stable release.

Thanks.

---

### Post by ciscosurfer on 2006-11-16
I suggested the dist-upgrade to see if you needed a newer kernel upgrade.  Obviously, you don't.  You can always try compiling a newer kernel...I'm running 2.6.18 and it's faster than 2.6.17 ... and it may have better support for your hardware.  Remember, when you compile your own kernel, you can setup which features you want.  Other than that, I don't know how else to help you out.  Sorry. :(

---

### Post by Kross on 2006-11-16
This Worked For me,,,

[http://www.ubuntuforums.org/showthread.php?t=298595&highlight=shutdown]("http://www.ubuntuforums.org/showthread.php?t=298595&highlight=shutdown")

4th Post down...
Post there If it worked for you..

Thanks

-Kross

---


---
title: "LogOut/Ctrl+Alt+Backspace FREEZE"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by wally00 on 2008-02-07
so i have this lil' problem....

I cannot use the LogOut button or the <Ctrl>+<Alt>+<Backspace> combination....after i press either one of them everything closes (the panels, the windows, any application running) excepting the desktop...i mean that i can only see the desktop wallpaper, nothing else, the login screen doesn't appear either (i waited a few minutes and nothing),  the only thing that works/ i knew to do is press the <Ctrl>+<Alt>+<Delete> keys and the pc reboots.

maybe it has something to do with the ATI video driver or xgl....cause i have installed and reinstalled them, quite a few times...

PS.: i have searched the forum for similar problems but nothing...maybe i haven't searched good enough.

---

### Post by OffAxis on 2008-02-07
anything in the log files?
/var/log/syslog
/var/log/Xorg.log
dmesg | tail

---

### Post by wally00 on 2008-02-07
i have solved the problem (at least temporary)...it was something related to the video drivers (i used the ones from ati`s site.)... cause i have uninstalled the drivers with the script from this thread

 [http://ubuntuforums.org/showthread.php?t=127157](http://ubuntuforums.org/showthread.php?t=127157)

 and installed form the repositories xserver-xorg-video-ati package...and seems to work now...even though it works on vesa driver (dunno if this is right for an ati card...)


thank you OffAxis for the quick reply...

---


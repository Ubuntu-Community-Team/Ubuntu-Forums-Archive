---
title: "Flash Sound Issue in Firefox 1.5"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by chessforce on 2006-01-05
Hello,

I am currently using Firefox 1.5 (from the Mozilla site) via 32-bit chroot and am encountering a weird sound issue when viewing Flash files.  When I launch Firefox from the gnome-panel (i.e. clicking the icon), sound does not work in Flash.  However, if I run the application from the console (using the exact same command as set in the  launcher), then sound in Flash works.  Thus, I was wondering why this was occurring.

---

### Post by chessforce on 2006-01-05
It seems as if I found a solution.  Originally, when I did not have sound working in Flash files within Firefox at all, I used the following guide [http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237) Thus, I modified the FIREFOX_DSP variable setting in the config file in the 32-bit chroot.  However, I left the default setting in the config file in the main (non-chroot) system.  Then, when I changed the main system's config file to the same settings as listed in the chroot's config file, followed by `killall esd`, and re-started Firefox using the launcher, the sound worked.

---

### Post by PhilOSparta on 2006-01-07
I just installed the flash and java RT using this thread :  
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)
and both worked fine except the sound in flash didn't work.

The common solution that I found worked i.e.

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---


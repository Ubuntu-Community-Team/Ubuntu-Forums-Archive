---
title: "ELF header error using ATI Video Card"
date: 2009-08-25
forum: x86 64-bit Users
---

### Post by gavotte on 2009-08-25
I recently purchased and installed a Radeon 4850 video card and am having nothing but problem getting it working on my system.  I am running 9.04 (x64) and can only run in the GNOME Failsafe mode.  I have tried both the ATI proprietary drivers and the Ubuntu non-proprietary drivers and both fail on the restart.
   
  The error messages coming from the ~/.xsession-errors file are as follows…
   
  /etc/gdm/Xsession: Beginning session setup...
  access control disabled, clients can connect from any host
  fold: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  /usr/lib/gdm/gdmtranslate: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  /usr/bin/zenity: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  grep: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  basename: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  cut: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  readlink: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  id: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  /usr/bin/xdg-user-dirs-update: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  readlink: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  grep: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  Setting IM through im-switch for locale=en_US.
  readlink: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to .
  grep: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
  /etc/X11/Xsession.d/98vboxadd-xclient: 20: /usr/bin/VBoxClient: not found
  x-session-manager: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
   
  Any suggestions anyone could provide would be most appreciated.

---

### Post by dcstar on 2009-08-26
> **gavotte said:**
> I recently purchased and installed a Radeon 4850 video card and am having nothing but problem getting it working on my system.  I am running 9.04 (x64) and can only run in the GNOME Failsafe mode.  I have tried both the ATI proprietary drivers and the Ubuntu non-proprietary drivers and both fail on the restart.
   
  The error messages coming from the ~/.xsession-errors file are as follows…
........
  x-session-manager: error while loading shared libraries: /usr/lib32/libc.so.6: invalid ELF header
   
  Any suggestions anyone could provide would be most appreciated.

Did you force install some 32-bit software on your 64-bit system?

---

### Post by gavotte on 2009-08-26
Yes, g77.  Think this might be the culprit?  Any suggestions on how to fix it?

---

### Post by Yellow Pasque on 2009-08-27
> /usr/lib32/libc.so.6
I don't have this file on my system, and I have the 32-bit libc installed. I DO have /lib32/libc.so.6 though (a symbolic link to libc-2.9.so)

See if that file belongs to a .deb package:
```
dpkg-query -S /usr/lib32/libc.so.6
```

---


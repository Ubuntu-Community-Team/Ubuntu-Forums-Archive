---
title: "metacity and X server keyboard shortcuts broken"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by Shum on 2008-12-27
Hi there.

After screwing with xorg.conf I've managed to break a bunch of keyboard shortcuts.


Ctrl-Alt-Fx does nothing so I can't bring up a real terminal.
Ctrl-Alt-Backspace does nothing so I can't restart the X server.


Also I've defined keybindings with metacity such as <super>y to bring up a terminal, and although these definitions are still there in gconf-editor they no longer work.

All the gnome and compiz keyboard shortcuts seem to work though, I can still switch desktops, run applications etc. (with <ctrl><alt>direction <alt>F2 respectively).

Although I'm not entirely sure its related what I was doing immediately beforehand was editing xorg.conf.
I made a backup then made changes to try and get a joypad working differently. The changes didn't work and I was left in low graphics mode, so I restored the backup.
Since then I've had this problem.

I'm running Intrepid 64 bit.

Any ideas anyone?
Thanks in advance.

 - Shum

---

### Post by Coder543 on 2008-12-27
You could either search around on google for the original xorg.conf or you could try installing a Virtual Machine of Ubuntu 8.10 64-bit and get the xorg.conf from it. Or you could reinstall Ubuntu. Right now I'm on a 32-bit machine, or I would consider uploading mine I don't know if 32/64 bit makes a difference._****_[]("http://ubuntuforums.org/showthread.php?goto=newpost&t=1022796")

---


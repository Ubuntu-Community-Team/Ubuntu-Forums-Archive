---
title: "Wine shortcuts"
date: 2007-10-14
forum: Wine
---

### Post by usarmykr on 2007-10-14
Wine installs shortcuts to the desktop.  I don't know how they work exactly, wanted to know, how do I apply the picture that should be on the shortcut?  Or is this even possible?

---

### Post by cogadh on 2007-10-14
If the shortcut is a .lnk file, then that is a Windows shortcut and it doesn't really work (well, you can make it work from the terminal, but that kind of defeats the purpose of a shortcut). If the shortcut is one with a Wine logo, then it is likely a functional shortcut and you can change the icon by right clicking and choosing properties. Click on the icon image in the properties dialog, then browse to ~/.wine/drive_c/windows/temp and look for the image you want (usually installation routines leave a bunch of icon junk in there). If the image you want isn't there, then check the application's install directory for one.

---


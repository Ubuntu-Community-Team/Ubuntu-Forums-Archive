---
title: "ATI Drivers Questions"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ChaperonNoir on 2005-03-13
Hello

How can i know if my 3d acceleration works ?

[http://www.ubuntuforums.org/showthread.php?t=18108](http://www.ubuntuforums.org/showthread.php?t=18108)

This is a previous thread where i installed them via apt-get.

WHen i resize a window, processor usage goes up to 100 %.. I guess i have none.

I have poor scores at glxgear too.

So.. What do i need to arrange to make them work ... 

Thanks

---

### Post by Woolmonkey on 2005-03-13
Is the kernel module loaded? Type lsmod and see if there is a fglrx module loaded.  If the kernel module is loaded, did you change your X config file.

---

### Post by ChaperonNoir on 2005-03-13
[QUOTE=Woolmonkey]Is the kernel module loaded? Type lsmod and see if there is a fglrx module loaded.  If the kernel module is loaded, did you change your X config file.[/QUOTE]

Yea i can see it . It's loaded.

When you say my X config file, you mean my xorg.conf file in etc/X11/ ?

What do i need to change ?

edmond@amd64:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1837 frames in 5.0 seconds = 367.400 FPS
edmond@amd64:~$ fgl_glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

---

### Post by Pse on 2005-03-14
In the Devices section, you should load "fglrx" instead of "ati" or "radeon"...
Of course, instead of manually changing that, you could use ATI's configuration utility:
```
$ sudo fglrxconfig
```

It'll allow you to tweak some settings and it seems to be work pretty well.

You can check which renderer is being used for OpenGL apps by issuing a:
```
fglrxinfo
```.
If it says something about MesaGL, then you're not using ATI's drivers for that.

---


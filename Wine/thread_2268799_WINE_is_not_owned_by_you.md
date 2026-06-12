---
title: "WINE is not owned by you"
date: 2015-03-11
forum: Wine
---

### Post by mdavis1231 on 2015-03-11
I have a program that MUST be installed as root in WINE or I'm unable to click on the buttons needed to install the program.  However, whenever I run "sudo wine file.exe", I get the error ./wine is not owned by you.  How do I rectify this?

---

### Post by slickymaster on 2015-03-11
*Moved to the ***WINE*** sub-forum*

---

### Post by deadflowr on 2015-03-11
Stop using sudo.

There should be no need for sudo to use wine.
[http://wiki.winehq.org/FAQ#run_as_root](http://wiki.winehq.org/FAQ#run_as_root)

Is this possibly an ownership issue with the wine subfolder in your home folder?
Perhaps look and see
```
ls -la .wine
```

---

### Post by mdavis1231 on 2015-03-11
I ran that, and here's what I got.


drwxrwxr-x  4 username username    4096 Mar 11 13:22 .
drwxr-xr-x 28 username username    4096 Mar 11 13:49 ..
drwxrwxr-x  2 username username    4096 Mar 11 13:22 dosdevices
drwxrwxr-x  6 username username    4096 Mar 11 13:04 drive_c
-rw-rw-r--  1 username username 1732451 Mar 11 13:22 system.reg
-rw-rw-r--  1 username username      11 Mar 11 13:04 .update-timestamp
-rw-rw-r--  1 username username    2245 Mar 11 13:05 userdef.reguntu
-rw-rw-r--  1 username username   39907 Mar 11 13:22 user.reg

I was able to install this .exe file the other day with no problem, but unfortunately I had to reinstall my Ubuntu 14.04 LTS yesterday due to some other issues, now WINE won't let me install it at sudo.  And if I don't install it as sudo, I can't click on the buttons to install the program.  Oh, and I'm not running WINE as root, only installing the program as root.

---

### Post by deadflowr on 2015-03-12
Does it really say username or did you put those there for anonymity?

---


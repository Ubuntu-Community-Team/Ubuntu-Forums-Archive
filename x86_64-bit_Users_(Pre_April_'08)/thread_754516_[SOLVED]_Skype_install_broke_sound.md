---
title: "[SOLVED] Skype install broke sound"
date: 2008-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by joetaxpayer on 2008-04-13
In my attempt to get skype running, it seems I've caused some damage to lib32.  

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I used the above guide and copied the files from libdbus-1.3, libqt4-core, libqt4-gui, libsigc++-2.0, and libXss into /lib32.  I realize now that I should have only copied the files listed by ldd /usr/bin/skype | grep not, but I copied ALL of the files in the above libs.  This left me with some linking error such as:

```
/usr/lib32/libdbus-1.so.3 is not a symbolic link
```

...amongst others.  I found a post in another thread addressing this issue like this:

```
/usr/lib32$ ls -la libdbus*
lrwxrwxrwx 1 root root     25 2007-06-06 22:41 libdbus-1.so.2 -> /usr/lib32/libdbus-1.so.3
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3.2.0
/usr/lib32$ sudo rm libdbus-1.so.3
/usr/lib32$ sudo ln -s libdbus-1.so.3.2.0 libdbus-1.so.3
/usr/lib32$ ls -la libdbus*
lrwxrwxrwx 1 root root     25 2007-06-06 22:41 libdbus-1.so.2 -> /usr/lib32/libdbus-1.so.3
lrwxrwxrwx 1 root root     18 2007-06-07 15:33 libdbus-1.so.3 -> libdbus-1.so.3.2.0
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3.2.0
```

So I did that with all the symbolic link problems output by ldconfig, hoping that might fix the problem.  It didn't. :(  

I still don't have sound working in skype or firefox (swiftweasel), although it works in all the other applications I've checked.  I am also unable to open soundrecorder (Your audio capture settings are invalid) (Sorry, I don't know if it is related, I just thought I should mention it).

Please help me.  I can live without skype, but I NEED sound in firefox (swiftweasel).

Thanks

EDIT:  Dunno what happened, but a reinstall of skype has everything working now (except line in, but that is another story). 8)

---


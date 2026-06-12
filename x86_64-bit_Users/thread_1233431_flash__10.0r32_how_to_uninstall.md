---
title: "flash  10.0r32 how to uninstall ?"
date: 2009-08-06
forum: x86 64-bit Users
---

### Post by nacho32 on 2009-08-06
if I go to add and remove programs it does not even show up. If I look in fire fox under plugins I dont see it, but under tools addons in fire fox it shows its their, and the dam thing crashes on pages with flash

---

### Post by MaindotC on 2009-08-06
You can find the package name by using (and here's an example):
```

amd64@amd64:~$ sudo dpkg-query -l | grep flash
ii  adobe-flashplugin                          10.0.22.87-1                                               Adobe Flash Player plugin version 10
ii  flashplugin-nonfree                        9.0.159.0ubuntu1~hardy1                                    Adobe Flash Player plugin installer
ii  libflash-mozplugin                         0.4.13-9ubuntu1                                            GPL Flash (SWF) Library - Mozilla-compatible
ii  libflash0c2                                0.4.13-9ubuntu1                                            GPL Flash (SWF) Library - shared library
ii  libflashsupport                            1.9-0ubuntu1                                               Support library for sound output of Flash 9

```

---

### Post by dcstar on 2009-08-07
> **nacho32 said:**
> if I go to add and remove programs it does not even show up. If I look in fire fox under plugins I dont see it, but under tools addons in fire fox it shows its their, and the dam thing crashes on pages with flash

Delete the libflashplayer.so file.

---

### Post by nacho32 on 2009-08-08
I just ran update manager and had 3 flash updates to install and it works, thanks for the replies:popcorn:

---


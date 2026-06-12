---
title: "ubuntu dapper wine"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by hitekhal on 2006-08-20
updated synaptic with the supposed path and all i get is 404?

tried some other approachs like installing libc6, etc. nada

help

---

### Post by Kilz on 2006-08-20
> **hitekhal said:**
> updated synaptic with the supposed path and all i get is 404?

tried some other approachs like installing libc6, etc. nada

help

Wine needs to be installed slightly differently in the 64bit version. See my signature for a link to the howto.

---

### Post by hitekhal on 2006-08-20
the libxx is for intel, i have amd 64 x2, is that a prob?

---

### Post by Kilz on 2006-08-20
> **hitekhal said:**
> the libxx is for intel, i have amd 64 x2, is that a prob?

wine requires it to start.

---

### Post by hitekhal on 2006-08-20
first try, no usr/lib32 error, so i made a lib32 dir
this is the terminal output for the install:


keith@keith-desktop:~$ cd ~/Desktop keith@keith-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.19~win ehq0~ubuntu~6.06-2_i386.deb
Password:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 74334 files and directories currently installed.)
Preparing to replace wine 0.9.19~winehq0~ubuntu~6.06-2 (using wine_0.9.19~winehq 0~ubuntu~6.06-2_i386.deb) ...
Unpacking replacement wine ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Setting up wine (0.9.19~winehq0~ubuntu~6.06-2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link


keith@keith-desktop:~/Desktop$

ran the sidenet:

keith@keith-desktop:~/Desktop/sidenet$ ./setup

SETUP STAGE 1
Stopping wine process ...
./setup: line 236: /usr/bin/wineserver: No such file or directory
renamed ~/.wine to ~/.wine.0608202149
renamed /home/keith/c to /home/keith/c.0608202149
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/keith/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
./setup: line 501: /usr/bin/wine: No such file or directory
./setup: line 502: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Programs -> Program Magager
./setup: line 504: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Control Panel
./setup: line 507: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Application Uninstaller
./setup: line 509: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Wine Configuration
./setup: line 511: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Task Manager
./setup: line 513: /usr/bin/wine: No such file or directory
./setup: line 515: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Programs -> Accesories -> Notepad
./setup: line 517: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
./setup: line 519: /usr/bin/wine: No such file or directory
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
./setup: line 521: /usr/bin/wine: No such file or directory
./setup: line 525: /usr/bin/wineserver: No such file or directory

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
keith@keith-desktop:~/Desktop/sidenet$


keith@keith-desktop:~$ winecfg
/usr/bin/winecfg: line 29: /usr/bin/wine: No such file or directory
/usr/bin/winecfg: line 29: /usr/bin/wine: Success
keith@keith-desktop:~$

but,sadly, no wine.

---


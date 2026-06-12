---
title: "Lots of problems, can anyone help me out please?"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2007-04-12
hi guys, i broke the xorg section of my ubuntu feisty amd64 system and couldn't get it back so i opted for a clean install. ok so i used a live cd (simply mepis) to back up my home directory to an external hard drive...

so i clean install feisty amd64, then boot in. ok my external hardrive won't mount, so i'm thinking i can't get my old home folder back... so i turn back to simply mepis and use that to copy everything back...

so i boot up again and all is back, but with padlocks and i get a permissions error saying my .drmc file should be 644. so i asked in irc and a guy did me a script to do this:
#!/bin/bash
sudo find /home -type d -exec chmod 755 {} \;
sudo find /home -type f -exec chmod 644 {} \;
for dir in /home/* ; do sudo chmod 700 $dir ; done

ok so stuff looks better now.

but then i tried to use wine. ok so i did the force architecture install as recommended and winecfg but that gives me an error. the wine tech guys in irc couldn't help me with this one:

> 
jonah@jonah-desktop:~$ slocate bin/wine
/usr/bin/wine-preloader
/usr/bin/winelauncher
/usr/bin/wine-pthread
/usr/bin/winecpp
/usr/bin/wineconsole
/usr/bin/winefile
/usr/bin/winedump
/usr/bin/winemine
/usr/bin/winegcc
/usr/bin/wine-kthread
/usr/bin/winebuild
/usr/bin/wineshelllink
/usr/bin/wineg++
/usr/bin/winemaker
/usr/bin/wineserver
/usr/bin/winedbg
/usr/bin/wineboot
/usr/bin/wine
/usr/bin/winepath
/usr/bin/wineprefixcreate
/usr/bin/winebrowser
/usr/bin/winecfg
jonah@jonah-desktop:~$ 
jonah@jonah-desktop:~$ cd ~/Desktop
jonah@jonah-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_*_i386.debPassword:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 108715 files and directories currently installed.)
Preparing to replace wine 0.9.34~winehq0~ubuntu~6.10-1 (using wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.34~winehq0~ubuntu~6.10-1) ...

jonah@jonah-desktop:~/Desktop$ winecfg
exec: 29: /usr/bin/wine: not found

can anyone help getting my system back how it was. wine not working, and there's other stuff that's not quite right, copying the home folder back didnt put evolution email accounts back for example, but the emails are there so that's cool. thanks for any help...

---

### Post by dabl on 2007-04-12
What was the problem with the external hard drive in your new Ubuntu installation?  It seems like if you could fix that (mount the external hard drive in Ubuntu), then restore your /home files, things would be less borked.  "seems" is such a dangerous word ....

---


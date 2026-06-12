---
title: "AMD64 Dependency Problem"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cappy on 2007-05-03
To run Skype 1.4 alpha I need sigc++ 2.0 for i386 installed, when I install it, my system makes me run "apt-get -f install" which reinstalls sigc++ 2.0 amd64 (it's removed when the i386 is installed) but then the i386 version is (overwritten?) and skype 1.4 no longer works.
If I only try to remove the AMD64 version it will also remove these packages: aptitude libsigc++-2.0-0c2a tasksel tasksel-data ubuntu-minimal. 
I can't get around this problem. Anyone know how?

$ sudo dpkg --force-architecture -i libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb 
Password:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 106349 files and directories currently installed.)
**Preparing to replace libsigc++-2.0-0c2a 2.0.17-2build1 (using libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb) ...**
Unpacking replacement libsigc++-2.0-0c2a ...
Setting up libsigc++-2.0-0c2a (2.0.17-2build1) ...

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsigc++-2.0-0c2a
The following NEW packages will be installed:
  libsigc++-2.0-0c2a
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/33.6kB of archives.
After unpacking 94.2kB of additional disk space will be used.

$ sudo apt-get remove libsigc++-2.0-0c2a 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  aptitude libsigc++-2.0-0c2a tasksel tasksel-data ubuntu-minimal
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 12.4MB disk space will be freed.

---

### Post by Kilz on 2007-05-03
I do not suggest in any way shape or form to force in libraries. If you do, you stand a good chance of fubaring the install. Better to extract 32bit libraries and copy them into /usr/lib32. To extract
```
dpkg -x packagename.deb
``` replacing packagename.deb with the debs name.

---

### Post by Cappy on 2007-05-03
I did:
```

 sudo dpkg -x libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb /usr/lib32

```

It didn't break the AMD64 library though.

Edit:
Oops, that worked. I just had to extract it to a local folder and THEN move the files in a subdirectory to /usr/lib32
Thanks! ^^

---


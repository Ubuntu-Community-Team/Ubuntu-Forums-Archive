---
title: "Canon drivers on ubuntu x64"
date: 2009-09-07
forum: x86 64-bit Users
---

### Post by Eugen184 on 2009-09-07
Is it possible for the canon mp 240 32 bit driver to work on ubuntu x64 if I have ia32-libs installed?

---

### Post by ElevenWarrior on 2009-09-07
not sure, I've had the same problem trying to get this printer to work as well,
try following these instructions...
,
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=953292&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=953292&page=2)
then,
(btw this didn't work for me, but it might for you)

[I]Extract "cnijfilter-common-3.00.tar.gz"
Open a terminal
$ sudo apt-get install libtool
In terminal, go to your extracted "cnijfilter-common-3.00" folder
$ sudo dpkg-buildpackage
The installation will most likely stop with the error "there are dependent packages to install": if it does stop and calls for dependencies start "symaptic package manager" from "System" "Administration" to search and install the required packages. After doing this repeat the last terminal command.
[/I]

---

### Post by Eugen184 on 2009-09-10
Thank you for replying I will try this as soon as possible.

---


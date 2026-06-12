---
title: "Help to install 32bits applications into chroot"
date: 2005-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fen-X on 2005-12-22
Hello,

I found a tutorial to create a chroot to use 32bits applications
But i don t understand very well how to use it if the applications can t be downloaded from synaptic :
[http://doc.ubuntu-fr.org/installation/chroot32bits](http://doc.ubuntu-fr.org/installation/chroot32bits)

For exemple, i would like to install drivers for my canon printer, like here :
[http://ubuntuforums.org/showthread.php?t=38995](http://ubuntuforums.org/showthread.php?t=38995)

can you tell me how have i to do ?

thank you very much

---

### Post by waster on 2005-12-23
Once you have set up synatpic to run in the chroot, new applications installed via the 32 bit synaptic are automatically run in the chroot.

I want to know whether things which have extensive interdependencies will work from a chroot, e.g. printing libraries for my exteremly linux un-effing-friendly canon PIXMA ip8500 printer.

---

### Post by Fen-X on 2005-12-27
But i can t install the drivers that i showed you with synaptic, it uses command-line ,
so it s very diff

how can i use th chroot during this kind of installation ?

---

### Post by skylark on 2005-12-28
Hi Fen-X,

It is possible to execute commands from your chroot:
1. from a terminal type: dchroot
2. You are now in your "chroot environment"... go ahead and follow the instructions on how to install your drivers, typing/pasting the commands only into this terminal. When you are finished you can type "exit" to exit the chroot.

However - I think you will run into some problems. Printer drivers are quite low level... even if you install them in your chroot, your 64-bit environment will probably not interface with them correctly. So to print from GIMP for example, you will probably have to install and run GIMP from your 32-bit chroot. Same goes for OpenOffice and all other applications...

You are probably about to explore territory few would venture into! Good luck!

I would also be pestering the printer's manufacturer to provide AMD64 binaries... or better yet open-source specs/code so free 32bit and 64bit drivers can be made!

---

### Post by skylark on 2005-12-28
PS:

From [http://www.arklinux.org/forum/viewtopic.php?forum=6&showtopic=1706](http://www.arklinux.org/forum/viewtopic.php?forum=6&showtopic=1706) :

"However, there has been at least one report of an IP4000 working with the included driver for a Canon BJC-7500. You may want to try that"

Might worth looking into... although I can't find a BJC-7500 driver included in AMD64 breezy, but there are lower models (eg 7100)... might be worth experimenting with these - it might save you some hassles.

---


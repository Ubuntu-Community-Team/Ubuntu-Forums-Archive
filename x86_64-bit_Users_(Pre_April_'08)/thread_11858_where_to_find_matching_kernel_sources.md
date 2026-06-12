---
title: "where to find matching kernel sources?"
date: 2005-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxgrrl on 2005-01-19
hello,
I would like to get lirc remote control working, which (I'm told) requires me to compile a module.
The lirc docs say that I need to have "the entire kernel source tree" in order to do this.  However, I cannot seem to find a kernel-sources package that matches the version of the kernel I'm running.  I haven't done anything fancy so far, just installed warty amd-64 and used "apt-get upgrade" and installed updated packages whenever I was told to do so. 

doing "uname -r", gives me 2.6.8.1-4-amd64-generic; however, the available "kernel-sources" packages only go up as far as 2.6.7. . . .


should I give up on trying to compile these lirc modules, or what?

TIA

---

### Post by az on 2005-01-20
linux-source-2.6

or

linux-headers-2.6.8.1-4-amd64-generic

Just use the headers.  Use the directory
/usr/src/linux-headers-2.6...(whatever)  when prompted for your source tree.

---

### Post by linuxgrrl on 2005-01-20
thanks, I'll give it a try!

---

### Post by linuxgrrl on 2005-01-24
[QUOTE=azz]linux-source-2.6

Just use the headers.  Use the directory
/usr/src/linux-headers-2.6...(whatever)  when prompted for your source tree.[/QUOTE]

I tried it but unfortunately, that did not seem to work.  When I used "kpkg xxx module_image," it printed about 20 lines worth of characters, ending in "done," which looked promising, but then there was no .deb file created for the lirc module (as the lirc docs said there should be after running that command).

If on the other hand I used "dpkg-reconfigure" as the lirc docs also suggested, then it prompted me for the source tree, I input the linux headers directory as suggested above, but it responded "this is not a valid kernel source tree" [natch!] and failed.

Any other hints as to what I might try?
thanks.

---


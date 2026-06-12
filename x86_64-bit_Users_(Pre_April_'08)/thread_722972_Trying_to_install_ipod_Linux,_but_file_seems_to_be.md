---
title: "Trying to install ipod Linux, but file seems to be missing from 7.10"
date: 2008-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by jasong on 2008-03-13
My friend is trying to help me install ipod Linux so we can run a program(you wouldn't believe the program we're trying to run, he custom-made it, and ipods run it better than anything out there.  No lie) and I keep getting the same error:
```
jason@jason-desktop:~/Desktop/ipodlinux-installer-2.31l-r2394$ ./installer
./installer: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
jason@jason-desktop:~/Desktop/ipodlinux-installer-2.31l-r2394$
```
The computer is running in 64-bit, python is at the latest Ubuntu 7.10 version, as of about a half-hour ago.  The libqt installation is newer than a baby's first breath since I re-installed it just now.  It's a Core2quad computer, 2.4GHz, 2GB of RAM.  If it matters, it's a 60GB video ipod, though we haven't even gotten to the point where it matters whether the ipod even exists or not.

My friend told me to post this in here, but I have no idea what's important and what's not, so I offer my apologies in advance.

---

### Post by jocko on 2008-03-13
The file libqtgui.so.4 is provided by the package libqt4-gui.
Do you have it installed?

You don't say that you have the 64 bit version of ubuntu installed, but I assume you have as you have a 64 bit processor and posted in the 64 bit section?
On the ipod linux home page, there are separate downloads for 32 and 64 bit linux, and as far as I can see the one you have (2.31l) is only for 32 bit.
So if you have 64 bit ubuntu, download the 64 bit version instead ([from here]("http://www.ipodlinux.org/Installer_2#Download")).

---

### Post by jasong on 2008-03-13
Yeah, that's labeled as AMD64 on the download page. lol, so not only are there links that don't go anywhere on that page, the link I clicked on was the wrong file.

I'm going to get on the web and see if I can find the right file somewhere else.

---

### Post by jocko on 2008-03-14
> **jasong said:**
> Yeah, that's labeled as AMD64 on the download page. lol, so not only are there links that don't go anywhere on that page, the link I clicked on was the wrong file.

I'm going to get on the web and see if I can find the right file somewhere else.
How about [this]("http://www.josh.sys-techs.com/installer/ipodlinux-installer-2.3lx.tar.gz")? [or this]("http://stepheneisenhauer.com/BHSPitMonkey/ipodlinux-installer-lx-r2397/")? They seem to be the correct ones (If my guess that 'l' after the version number in the file name is linux 32 bit and 'lx' is linux 64 bit)

---

### Post by Kilz on 2008-03-14
Since the program uses an installer, are you sure the program is compiled as 64bit? If not its 32bit and looking for a 32bit library. In a 64bit operating system there are 32 and 64bit libraries of the same name. [You might want to try getlibs.]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---


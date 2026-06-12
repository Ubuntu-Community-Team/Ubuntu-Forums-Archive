---
title: "Feisty AMD64 nspluginwrapper"
date: 2007-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ibbuntu on 2007-04-30
Somehow I've managed to break my system, I had nspluginwrapper working under Edgy. Since then I think I have followed someone's instructions for fixing something else (I don't remember what now) which included copying .so files from /usr/lib/ to /usr/lib32/. Now every time I run "apt-get" I get hundreds of messages saying "ldconfig: blah.so.0 is not a symbolic link". This I think is related to my problem with nspluginwrapper, which returns the following error when I try to run "nspluginwrapper -i /usr/lib/firefox/plugins32/libflashplayer.so":
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libfreetype.so.6: wrong ELF class: ELFCLASS64
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libfreetype.so.6: wrong ELF class: ELFCLASS64
nspluginwrapper: /usr/lib/firefox/plugins32/libflashplayer.so is not a valid NPAPI plugin

---

### Post by Kilz on 2007-04-30
> **ibbuntu said:**
> Somehow I've managed to break my system, I had nspluginwrapper working under Edgy. Since then I think I have followed someone's instructions for fixing something else (I don't remember what now) which included copying .so files from /usr/lib/ to /usr/lib32/. Now every time I run "apt-get" I get hundreds of messages saying "ldconfig: blah.so.0 is not a symbolic link". This I think is related to my problem with nspluginwrapper, which returns the following error when I try to run "nspluginwrapper -i /usr/lib/firefox/plugins32/libflashplayer.so":
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libfreetype.so.6: wrong ELF class: ELFCLASS64
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libfreetype.so.6: wrong ELF class: ELFCLASS64
nspluginwrapper: /usr/lib/firefox/plugins32/libflashplayer.so is not a valid NPAPI plugin

I think you may have fubar'd your 32bit system. /usr/lib is for 64bit libraries. /usr/lib32 is for 32bit libraries. 64bit applications cant use 32bit libraries, neither can 32bit applications use 64bit libraries. Its a good idea and practice never to copy files from one to another.
We can try to replace the 32bit files in your system.
```
sudo apt-get install --reinstall ia32*
sudo apt-get install --reinstall linux32 
```
This commands may install a few more 32bit packages, but will reinstall those you already have.

I also have a new script that [automatically installs the nspluginwrapper and flash ]("http://ubuntuforums.org/showthread.php?t=425672")in case you  are still having problems after that.

---

### Post by ibbuntu on 2007-04-30
Thanks for the suggestion, I tried it out, but I'm afraid I'm still getting the same error message. I gave your script a go, but as I expected I still get the same error message. I am very reluctant to do a clean install, but I fear this is rapidly becoming my only option.

---

### Post by Kilz on 2007-04-30
> **ibbuntu said:**
> Thanks for the suggestion, I tried it out, but I'm afraid I'm still getting the same error message. I gave your script a go, but as I expected I still get the same error message. I am very reluctant to do a clean install, but I fear this is rapidly becoming my only option.

I have to agree, if you above didnt fix it, and you cant remember what files you copied in, it may be your only option.

---

### Post by ibbuntu on 2007-05-04
I've finally found the time to do a clean install, and your script worked perfectly. Thanks.

---

### Post by Kilz on 2007-05-04
Nice to hear you have it all working :D

---

### Post by fatbuttlarry on 2007-05-05
Haha!  This was waaaaay to easy!  Thanks a bunch!

Anyone looking to run Flash 9 + AMD64 Firefox look no further!

This will do great until we can get native support through flash!

Ebaumsworld loaded perfect after this.  Thanks again.

-Tres

---


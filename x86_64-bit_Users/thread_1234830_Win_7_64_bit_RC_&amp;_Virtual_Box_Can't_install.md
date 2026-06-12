---
title: "Win 7 64 bit RC &amp; Virtual Box Can't install"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by craig100 on 2009-08-08
HI, i've just downloaded the iso for Win 7 RC and can't install it into a new VM with VirtualBox 2.2 on Ubuntu 9.04 64 bit. What I get is "Loading Files" then "Starting Windows" then a Windows Boot Loader error "An unexpected error has occured" indicating an error code of "0xc0000225". I've set up the VM with VT extensions on, 2G RAM, 20G HD, audio on (Pulse Audio). Have tried the PCnet-FASTIII and Intel Pro 10/100 MT network adapters. Also tried installing from iso and DVD. Get the same result every time.

Does anyone know what could be causing this?

Craig

---

### Post by craig100 on 2009-08-08
Sorry guys, moved my question to a new thread as it was for VirtalBox not Virtual PC.  New thread at [http://ubuntuforums.org/showthread.php?p=7753055#post7753055](http://ubuntuforums.org/showthread.php?p=7753055#post7753055).

Craig

---

### Post by craig100 on 2009-08-08
Apart from putting the notice that I've moved this question here in the wrong thread, I've now fixed the problem with help from another place.  What was needed was to switch on IO PIC and Nested Paging. Installation then went ahead ok.

Hope this helps someone.

Craig

---


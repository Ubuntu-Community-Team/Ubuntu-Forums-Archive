---
title: "How do you install 32bit antivirus on 64 bit Ubuntu 8.04?"
date: 2008-08-11
forum: x86 64-bit Users
---

### Post by runes on 2008-08-11
I'm in a bit of a crunch and I tried to install a 32 bit version of avg on my 64 bit Ubuntu box.  I have  Windows binaries in my NAS and I want to make sure the users don't get infected not to mention the macros and documents.  

I installed the ia32_libs but I still can't get it to install (avg)

---

### Post by underground on 2008-08-11
Check here  my friend
[http://ubuntuforums.org/showthread.php?p=3836317](http://ubuntuforums.org/showthread.php?p=3836317)

---

### Post by stchman on 2008-08-11
> **runes said:**
> I'm in a bit of a crunch and I tried to install a 32 bit version of avg on my 64 bit Ubuntu box.  I have  Windows binaries in my NAS and I want to make sure the users don't get infected not to mention the macros and documents.  

I installed the ia32_libs but I still can't get it to install (avg)

64 bit OS will support 32 bit .deb files.  I believe you will have to force the architecture.  You can get this from the man pages for dpkg command.

[http://www.grisoft.cz/filedir/inst/avg75fld-r51-a1243.i386.deb](http://www.grisoft.cz/filedir/inst/avg75fld-r51-a1243.i386.deb)

---

### Post by cariboo on 2008-08-11
Why not run clamav, it runs natively in 64 bit, and it is easy to install as you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to instal lit.

Jim

---


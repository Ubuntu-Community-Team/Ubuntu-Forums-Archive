---
title: "Skype libXv.so.1 problem"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschira on 2008-03-21
Hi
I am new to Ubuntu (not entirely new to Linux, but also not advanced)
so please be patient with me...

I installed Skype on my completly new U. 7.10x64 system.

I installed the 32 compatibility libs. When I installed Skype it told me that it needs libqt4-core and libqt4_gui so I installed them as well.
Now, when I try to start skype via the Applications menue nothing happens, when I open a terminal and type "skype" I get  "libXv.so.1: wrong ELF class: ELFCLASS64"
Not sure how to react to that...
Can someone help?
Cheers
M.
P.S. how do I get the command ll (a better ls) like I know it from SUSE?

---

### Post by Kilz on 2008-03-21
> **mschira said:**
> Hi
I am new to Ubuntu (not entirely new to Linux, but also not advanced)
so please be patient with me...

I installed Skype on my completly new U. 7.10x64 system.

I installed the 32 compatibility libs. When I installed Skype it told me that it needs libqt4-core and libqt4_gui so I installed them as well.
Now, when I try to start skype via the Applications menue nothing happens, when I open a terminal and type "skype" I get  "libXv.so.1: wrong ELF class: ELFCLASS64"
Not sure how to react to that...
Can someone help?
Cheers
M.
P.S. how do I get the command ll (a better ls) like I know it from SUSE?

Skype is 32bit, [you need to use getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install the needed files.

---

### Post by mschira on 2008-03-21
I don't seem to have the program getlibs.
When I typed getlibs /usr/bin/skype 
I got: getlibs: command not found (sudo doesn't change that...)

I looked in Synaptic for getlibs, but I couldn't find it...
M.

---

### Post by mschira on 2008-03-21
ups. Sorry i installed getlibs. It is working right now (downloading stuff), let's hope iot does the magic trick.
Thx,
M.

---


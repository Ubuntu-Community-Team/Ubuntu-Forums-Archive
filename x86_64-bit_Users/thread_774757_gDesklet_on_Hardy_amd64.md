---
title: "gDesklet on Hardy amd64"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by unnamedstone on 2008-04-29
I cannot get gDesklet work on Hardy 64 even if I tried the Python2.4 trick described in [http://ubuntuforums.org/showthread.php?t=582721](http://ubuntuforums.org/showthread.php?t=582721)
(python2.4 installed, file headers modified) I still get the same problem (grey window, no response). Can someone help me please?

---

### Post by Saubazi on 2008-05-06
I have the same problem - I found temporary resolution from another thread - there somebody posted .deb for gdesklet 0.35 for amd64 - I installed this and it worked. It is not the most actual version but at least it runs.

I also googled and there was mentioning of some other libraries being then compiled with wrong python - some .so files. I got as far as compiling the gdesklets myself but I could not figure out what I should do extra during compilation in order to have these .so files right...was it about tiling.so or so - can't find the right page any more

I would get rid of the whole buggy gdesklets but I have already some that I wrote myself.

---

### Post by Plasma_NZ on 2008-06-22
I have the same problem as POST-1 - how to fix.? any ideas? updates havent made a difference..?

---

### Post by stlouisubntu on 2008-08-13
Me too.  Same problem as unnamedstone above.  Alternate .deb file installed
all files modified to Python2.4 (including the additional ones not
initially mentioned), and the sudo aptitude install Python2.4, but no luck.  gDesklets still cannot connect
to daemon.

An unpleasant side effect of this (probably the the Python2.4 downgrade) is 
my file types have flaked out (including the desktop icons.)  Any suggestions, fixes, or workarounds would be much appreciated.

Ubuntu 8.04.1 AMD64 on Acer Aspire 5100 Laptop Turion 64 Gnome with
Edubuntu add on.

---

### Post by jwrede on 2008-10-16
+1

---

### Post by stchman on 2008-10-16
Yes, gDesklets from the repos do not work in 64 bit Hardy.  I tried the 0.35 gDesklets for amd64 and it screwed my system up.

I run screenlets instead of gDesklets.

---


---
title: "[SOLVED] please help with youtube/flash"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by NeuB27 on 2008-06-12
I have already tried the sticky posts on fixing flash, and tried flash 10 beta, I have searched the forums and tried three other things to fix my probelems. BUT I still cannot play anything from youtube or other flash video sources. Please help!

---

### Post by komputes on 2008-06-12
Under Hardy, just open a terminal and run the following command. Works well for me although flash does seem slower on Linux.

sudo apt-get install flashplugin-nonfree

---

### Post by Sef on 2008-06-12
Have you tried [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490")?

---

### Post by NeuB27 on 2008-06-12
non-free didn't seem to work I know I've had it installed before and it wasn't playing anything
and yes, I did use the linked tutorial, it was the second one that I tried, but to no avail.

---

### Post by starfunker on 2008-06-12
Have you tried installing ubuntu-restricted-extras?

---

### Post by nirkir on 2008-06-12
Are you using 32bit or 64bit OS/Firefox?

---

### Post by NeuB27 on 2008-06-12
I am using 64bit ubuntu hardy 8.04. I have firefox 3.0 for 64bit. I have tried the restricted drivers. But they didn't seem to fix the problem.

---

### Post by bijeeshvs on 2008-06-12
try downloding and installing from the adobe site,
its a known problem what i faced but i managed to solve it
by the way which browser are you using???????????????????

alternatively you can try "gnash"................

---

### Post by yragrelluf on 2008-06-12
what worked for me was to uninstall all of the mess i made trying to get flash working, then i uninstalled firefox 3 because its beta and thats your problem. after that, open your package manager and install firefox 2. that worked perfect for me.

---

### Post by Kilz on 2008-06-12
> **NeuB27 said:**
> non-free didn't seem to work I know I've had it installed before and it wasn't playing anything
and yes, I did use the linked tutorial, **it was the second one that I tried**, but to no avail.

The number 1 reason for failure is left over files from previous howto attempts. I suggest you go back to that original howto and remove everything it had you add.

---

### Post by nirkir on 2008-06-15
> **NeuB27 said:**
> I am using 64bit ubuntu hardy 8.04. I have firefox 3.0 for 64bit. I have tried the restricted drivers. But they didn't seem to fix the problem.

Just to make sure - are you using nspluginwrapper? You need it in order to run flash (32 bit) on 64 bit firefox.

---

### Post by NeuB27 on 2008-06-17
Thanks to everyone, I removed gnash and some other things I had installed, and it seemed to work. So thanks for the advice about removing previous versions.

---


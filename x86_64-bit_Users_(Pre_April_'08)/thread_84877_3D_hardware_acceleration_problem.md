---
title: "3D hardware acceleration problem"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by sieste on 2005-11-01
hi everybody,

I have an   12 inch ibook with an ubuntu breezy installed, but the 3D hardware acceleration doesn't work. Furthermore, none of the "fglrx" packages exist  for the powerpc architecture. Can somebody help me ? 

information :

my kernel is 2.6.12-9
1 GB ram

---

### Post by autocrosser on 2005-11-01
First--how old is the 'book--any idea what card is in it--post your /etc/xorg.conf & take a look at /var/log/xorg.0.log to see what xorg is doing during boot---With ATI, any card newer than 9500 will not have 3D until Xorg 7.0 or so---

---

### Post by sieste on 2005-11-02
Thanks for your reply

My ibook is one month old. My video card is an ATI RADEON mobility 9550. 
Here is my xorg.conf ([ATTACH]3314[/ATTACH]) and my xorg.log (1->[ATTACH]3316[/ATTACH]; 2-> [ATTACH]3315[/ATTACH])

cheers,

sieste

---

### Post by slux on 2005-11-02
Well, there's an experimental driver at [http://r300.sf.net]("http://r300.sf.net") if you're interested in doing a little work to get it (possibly) working.

---

### Post by monway on 2005-11-03
That particular driver hasn't worked for me. If anyone out there has gotten this to work for a Al powerbook 17" please let me know. Or write a how-to and get it stickied.

---

### Post by autocrosser on 2005-11-03
Well--As expected---"(WW) RADEON(0): Direct rendering not yet supported on Radeon 9500 and newer cards"--I've been waiting for Xorg 7 for the last three months--know that they are getting close---or you can bombard ATI to get the "freesource" drivers in line for PPC users--no luck there:mad:--they have a "hard" enough time ***ing out PC drivers---

---


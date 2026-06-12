---
title: "unstable with ubuntu 64"
date: 2009-06-29
forum: x86 64-bit Users
---

### Post by atomax27 on 2009-06-29
I have recently installed ubuntu x64. I seem to have several issues with the X server. It often come up with some problems, such as firefox crash, apt-get cannot work, etc... Sometmies I follows advice found on this forum and it gets fixed OK. Sometimes I had to run fsck manually to fix some blocks on my hard disk, and finally could start X window... 
 
Now, after I repeating the procedure, the login window appeared, but it doesn't respond to my mouse or keyboard.. There is no problem with my keyboard/mouse - I could use it for Grub..
 
Could anyone help me with this issue?
 
Besides, the OS seems quite unstable on my laptop (T61), and so often do I need to fix hard disk problem... I can't help wonder, does anyone else have similar problems? Shall I just swich to 32 bit? or another hard drive perhaps?

---

### Post by Jaesin on 2009-07-20
there seems to some issue with the X server and desktop effects on the 64 bit version.  I don't know if you are running this on your laptop in addition to your desktop, but you might try the netbook version on the laptop.  

if you disable desktop effects the crashing of X server might go away.  My 32 bit version does the same thing though, so it must be something coded into graphic drivers, or compiz, or even something else entirely.

hope this at least point you in a direction.

---

### Post by Sef on 2009-07-21
1) What is your graphics card?

2) Do you have the restricted drivers for it enabled?

---

### Post by litspliff on 2009-07-21
i believe sef is on to something. i had to constantly switch displays and fk around with xconfig and weird crashes at the login just to get into a minimal gnome. after i finally got in, i was able to activate the restricted nvidia driver, ctrl+alt+F1 to a terminal, run "nvidia-xconfig", then i restarted X "sudo /etc/init.d/gdm restart".  at this point i was able to boot  into a proper gnome session.  

also, make sure you have an interenet connection open in case you need to grab a remote driver file.

---


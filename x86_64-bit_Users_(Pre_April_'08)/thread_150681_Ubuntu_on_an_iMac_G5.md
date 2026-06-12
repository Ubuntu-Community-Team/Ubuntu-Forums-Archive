---
title: "Ubuntu on an iMac G5"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by oppositemedia on 2006-03-26
Hi

I keep trying to Install Ubuntu on my Rev. B iMac G5, but I always get some error about invalid memory access. Anyone have any suggestions?  I really need some help...

-Mav

---

### Post by ssam on 2006-03-26
did you choose the powerpc-64 option at boot?

you need to press tab at the boot screen to get a list of kernel and then type the name in and press enter.

---

### Post by oppositemedia on 2006-03-26
Oh.  Didn't know that.  I can't try that just right now but I will soon!

---

### Post by oppositemedia on 2006-03-26
Thanks so much!  So far it's working!

---

### Post by oppositemedia on 2006-03-26
Hey,

It installed but there is one MAJOR problem.  I am not able to login.  The mouse at the login screen is laggy and the keyboard does not work (I have tried two keyboards: a logitech usb one and an apple wireless keyboard).  Both worked during the installation.  HELP?!

Thanks in advance,
Mav

---

### Post by oppositemedia on 2006-03-26
Help?!

---

### Post by oppositemedia on 2006-03-26
I still really need some help!

---

### Post by jdp on 2006-03-26
There are other threads around here dealing with the G5 iMac.  Have you readd through them to see if they have the same trouble?  I've read threads about sound issues, and various problems with X setting that may slow down the machine.  Leaving DRI enabled in X.Org seems to cause some users trouble.  There is an on-going thread about G5s that lock up when ever any sound is made.

---

### Post by spaceballl on 2006-03-27
So i have no idea if this will solve your problem, but it's worth a try. When the prompt comes up after you select your OS, instead of hitting "enter,"

type: "Linux Single"
then hit enter.

It should but up as root user.

then do an apt-get remove of every package that starts with "bluez" - that's what's messing up your apple wireless mouse. I reported this bug a while back, and it's been confirmed, but no fix yet...

Not sure about your other problems, but this might knock down one of 'em

---


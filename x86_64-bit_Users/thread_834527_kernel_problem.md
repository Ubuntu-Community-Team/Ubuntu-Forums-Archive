---
title: "kernel problem"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-06-19
I do not have a real problem with my kubuntu, except in last few days from time to time, it just logout me in a middle of something and I have to log in again.
But I noticed something .
I had 2 kernel updates.
When I installed kubuntu my kernel was ....16, then updated to .....18 and today to ....19
But when I turn on my comp, and grub shows up, I have a choice to all kernels that I had ( 16, 16 recovery mode, 18, 18 recovery mode, 19, 19 recovery mode ), is this normal and if not, how should I fix it....?

thanks

---

### Post by firecat53 on 2008-06-19
I'm not sure why it would randomly log you out ..... but..... to get rid of the old kernels you can open up Adept (or sudo aptitude from the command line) and remove the old kernels (probably kernel, kernel-headers, and restricted modules). That will automatically clean up those old entries in your grub menu.

The old kernels are left there so in case something is broken with a new kernel update, you can still boot into an old (working) kernel.

Scott

---

### Post by pixel :-) on 2008-06-19
it just logout me in a middle of something 
is that something always the same?X crashed.X is the program that handell your screen and some other stuff.mplayer pluging for firefox does that sometimes to me.

and I have to log in again.
you can configure it to autorelogin when X crashes.

It's probably a bug,a work around could exist ,but if this happens rarelly just live with it, a research will be to painfull for not much.Try to guess whats the incriminating act that trigers the crash,and avoid it.

---


---
title: "[SOLVED] Ubuntu x86-64 won't install"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by spud.dups on 2008-07-14
I just acquired an AMD 3200 64 bit and I was trying to install Ubuntu.  I did make sure to get the correct version to install, but every time it tries to install, or use it without install, it goes to a busybox command prompt.  Has this been a common problem?  The machine does have a SATA harddrive, but so does my laptop and Ubuntu installed fine.

I was able to install Fedora 9 x86-64 on the machine, and it is working great.  Any ideas?

---

### Post by stchman on 2008-07-14
> **spud.dups said:**
> I just acquired an AMD 3200 64 bit and I was trying to install Ubuntu.  I did make sure to get the correct version to install, but every time it tries to install, or use it without install, it goes to a busybox command prompt.  Has this been a common problem?  The machine does have a SATA harddrive, but so does my laptop and Ubuntu installed fine.

I was able to install Fedora 9 x86-64 on the machine, and it is working great.  Any ideas?

Will the Live CD bring up the GUI?

If yes, then what are you doing next?

---

### Post by spud.dups on 2008-07-14
I put in the cd, and it has a list of menu options.  It looks like [[COLOR="DeepSkyBlue"]this[/COLOR]]("http://taqeem.files.wordpress.com/2007/11/vista_ubuntu_05article-width.jpg").  You have to excuse me,  I'm a web developer, but am very new to Linux in general.  I'm not sure what the 'live cd' is.  I go to install, and the splash comes up, the bar below runs across once then it goes to the busyBox command prompt.

Sorry, forgot to add.  I'm installing Hardy, so the graphic above isn't completely accurate.  But you get the idea.

---

### Post by fumduck on 2008-07-14
it might be the same problem I had which is at the install prompt.. hit the F6 for more options... delete quiet splash and hit enter or  replace quiet splash for no splash... good luck..

---

### Post by spud.dups on 2008-07-14
Thanks, I'll give that a try tonight when I get home and let you know tomorrow if that worked.

---

### Post by Neo0351 on 2008-07-14
for you boot options try adding 
```
all_generic_ide floppy=off irqpoll
```

---

### Post by spud.dups on 2008-07-18
That did it.  Problem solved.  If you have a minute could you explain why those options worked?

---

### Post by Neo0351 on 2008-07-18
glad to hear it worked, but im sorry i dont know why they work.

---

### Post by kaligus on 2008-07-19
> **Neo0351 said:**
> glad to hear it worked, but im sorry i dont know why they work.

I have had this problem with several OS when the motherboard only has 1 actual connection for a floppy (or none) and the bios is set to the usual default of two floppies (or one).

Once or twice when the bios was correctly set, but the hardware was missing I have also seen windows take about 20 minutes to get past trying to figure out what the non-existing floppy really is.

---


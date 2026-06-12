---
title: "Linux Kernel 2.6.24.4 sound problems"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jemrpo on 2008-04-07
Hi!

I've just installed ubuntu 7.10 and is running kernel 2.6.22-14-generic the one that comes with the installation,
the thing is that I just compiled kernel 2.6.24.4 with the sources that I've download from kernel.org.
I compiled it with the same .config that I had in 2.6.22-14-generic, it runs well but I've lost my sound, I don't undertand why because had the same configuration that has the older kernel,
tried with lsmod and shows hat kernel doesn't load the same modules that loads on 2.6.22-14-generic, tried to load the with insmod but nothing happened,
can anybody tell me what should I do to make kernel load the same modules that loads on 2.6.22-14-generic?.

thanks in advance :).

---

### Post by Alexis Phoenix on 2008-04-07
Hi,

There are a few changes between 2.6.22 and 2.6.24.  Did you use a graphical/menu based configuration front end (like make gconfig or make menuconfig)?  Or just copy in the old configuration and do make?  You really should refine your choices if you are using the same config from a generic Ubuntu kernel as these are configured to run on as wide a range of hardware as possible - there is probably a lot of stuff there you don't need and you are probably now (due to the changes) missing stuff you do need.  Tweaking it will probably give you a faster kernel too :-)  It can take a long time to get right.  You might be better to start with "make allnoconfig" and then "make gconfig" (or whatever) to get the individual things you need (if you are confident in what you are doing).

HTH

Alexis

---

### Post by jemrpo on 2008-04-07
yes I tried to compile a custom one for my machine but it didn't work, so that's why I tried to compile with the default configuration.
I've done compiling in other distros and have no problems with it,
would you recommend me to get the original source or get ubuntu sources?.

---

### Post by Alexis Phoenix on 2008-04-08
Personally I use sources from kernel.org, however the Ubuntu source may be patched with Ubuntu goodness - I don't actually know.

Since I don't know anything about your hardware I can't really give you any further advice.  Unless it's very old you should be using the alsa drivers - you should also make sure you have the correct bus enabled (pci, pci express or isa).  You may have extra options for your particular sound card.

Are you sure there is simply not some option you have to enable for the card in userland?  (try alsamixer in terminal) Have a look in your /dev/ directory - there should be /dev/snd - this is the sound card.  If this is present it is (probably) not a kernel problem.

If you post some hardware info (try lspci)  I will try to see if I can spot anything you need in the kernel.

---


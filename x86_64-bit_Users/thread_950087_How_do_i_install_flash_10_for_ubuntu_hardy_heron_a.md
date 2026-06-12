---
title: "How do i install flash 10 for ubuntu hardy heron amd64????"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by fignig on 2008-10-16
How do i install flash 10 for ubuntu hardy heron amd64????

I've been looking for a long time now. Is there anyone who can answer my question straight w/ a good working answer? Or do i have to switch back to windows?

---

### Post by tuxxy on 2008-10-16
```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

There is already a thread on how to do this in the recent posts

[http://ubuntuforums.org/showthread.php?t=948729](http://ubuntuforums.org/showthread.php?t=948729)

---

### Post by fignig on 2008-10-16
> **tuxxy said:**
> ```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

There is already a thread on how to do this in the recent posts

[http://ubuntuforums.org/showthread.php?t=948729](http://ubuntuforums.org/showthread.php?t=948729)

still not working....anyone else?

---

### Post by fignig on 2008-10-16
> **fignig said:**
> still not working....anyone else?

how do i know which flash i have installed?

---

### Post by LianRome on 2008-10-17
Hi Fignig
To know your installed flash version, type **about:plugins** in the address bar, and look for Shockwave Flash. I think 10.0 r12 is the last one.
To install it in a 64bits architecture, I followed this steps:
[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)
The tutorial is about a previous version, but it works ok.
I advice you to copy and paste the instructions since it is better to close the browser while you are doing this.
Pay special attention to Nate's comments on Aug 20 about the missing 32-bit libraries. Other way to get them is to install the getlibs package: [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

¡Good luck!

---

### Post by kkady32 on 2008-10-17
that works

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by blackmail on 2008-10-17
ok so my method maybe a bit unorthodox, but it did the job...:lolflag:
so...a method would be to go to xnxxx.com, and enter the site then select a vid and the rest is just like installink a normal flash under windows!
i tryed all the scripts from here but it just wouldn't resolve the mirror.kernel... thing
hope i don't offence anyone, just trying to help, and i am running the 64 bit firefox

---


---
title: "forcing 32 bit install?"
date: 2007-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angelbeast on 2007-10-17
I have a 32 bit debian package of VariCAD. I there any possible way to force it to install on a 64 bit system> I hope so coz 32 bit seems to be all it comes in. Thanks in advance for any help...

---

### Post by FredB on 2007-10-18
You can try. In a console, try :

sudo dpkg -i  --force-architecture name-of-deb.deb

---

### Post by Angelbeast on 2007-10-18
> **FredB said:**
> You can try. In a console, try :

sudo dpkg -i  --force-architecture name-of-deb.deb

Thank you so much. That worked. It installed and everything but when i run it it shuts down.

---

### Post by Angelbeast on 2007-10-18
It almost acts like the same problem i was having with Azzureus where it was shutting down right when you start it up and that was some sort of java problem. I thought maybe it would have something to do with needing to have 32 bit java but that was already installed. Ideas? Anyone?

---

### Post by Angelbeast on 2007-10-18
Okay i tried running VariCAD from the terminal and got the following

ron@ron-laptop:~$ varicad

*** (R) VariCAD - graphic system release 2007 1.08
*** (C) VariCAD
Segmentation fault (core dumped)


Does that give anyone any ideas?:

---

### Post by Kilz on 2007-10-18
[Did you get it here. ]("https://www.varicad.com/3dcaddownload.phtml")

---

### Post by Angelbeast on 2007-10-18
> **Kilz said:**
> [Did you get it here. ]("https://www.varicad.com/3dcaddownload.phtml")

ahhhh..well i didn't originally but i am right now...o now how do i uninstall the other one? It's not listed in synaptic...

---

### Post by Angelbeast on 2007-10-18
> **Kilz said:**
> [Did you get it here. ]("https://www.varicad.com/3dcaddownload.phtml")

Looks like it's working now but it says that OpenGL is not accelerated...How do i accelerate it?  *LOL*

---

### Post by Kilz on 2007-10-18
> **Angelbeast said:**
> Looks like it's working now but it says that OpenGL is not accelerated...How do i accelerate it?  *LOL*

Most probably done by installing proprietary video drivers.

---

### Post by unf on 2007-10-18
Graphics Card: ATI Radeon XPRESS 200 so you need to install fglrx drivers, use should be able to install trought restricted drivers manager, otherwise just install it manually.

---

### Post by Angelbeast on 2007-10-18
> **Kilz said:**
> Most probably done by installing proprietary video drivers.

It says it's installed already...Do i need to configure something?

---

### Post by Angelbeast on 2007-10-21
Someone? Anybody?

---

### Post by Qdlaty on 2007-11-02
If you have Compiz/Beryl desktop you will always get the lack of 3D acceleration message.
You can try with preloading properl GL libs.
I'm a happy VariCAD user (on both, 32 an 64 bits Ubuntus) and even without that 3D acceleration working with complicated 3D models is not so hard. I just hide the unused during editing details and that's it.

---

### Post by PmDematagoda on 2007-11-02
I do not believe you can use an integrated VGA card for eye-candy such as Compiz-fusion, you may need a dedicated and external VGA card, most preferably an Nvidia one.

---


---
title: "Xubuntu with Real Time kernel?"
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hansson_14 on 2007-12-29
Hi, every- and anyone!

I run Ubuntustudio (32 bit), but want to install Xubuntu 64 since I have an older 64 bit computer.
However, I still want to make music (MIDI) now and then, thus I need the Real Time kernel that comes with Ubuntustudio 64-bit (there is a 64-bit version of Ubuntustudio, isn't there?).

How do I combine Xubuntu and the Real Time kernel?

Or should I install Ubuntustudio 64-bit and then install something from Xubuntu on top of that?

I have the feeling there is a simple solution - please let me know :)

Thanks in advance!

/Fredrik

---

### Post by John.Michael.Kane on 2007-12-29
You would install xubuntu either using the xubuntu iso or installing using the meta package xubuntu-desktop, Along with all your audio tools etc, and simply replace the generic kernel with the one below

```
gksudo aptitude install linux-rt
```

---

### Post by aidanr on 2007-12-29
Install Xubuntu 64bit and then
```
sudo apt-get install linux-rt
```

edit: I'm too slow today

---

### Post by zettberlin on 2007-12-30
I run the Ubuntustudio-packages (RT-kernel etc) plus Ardour, Rosegarden and some others from source with Ubuntu installed and XFCE as my desktop.

It works great! :-) 

Ubuntu, Xubuntu, Kubuntu etc. are just preconfigured packages that hold more or less the same software - you can always alter these configurations as you wish.

I have Konqueror as my default-file-manager, Firefox as my browser, XFCE with my own Menufile as my desktop. The nice thing about Ubuntu is not look/feel but a solid basis derived from Debian and polished by canonical and MOTU. Well-mantained repos providing software-packages that do not conflict with each other and the hardware-layer just works OK.

---

### Post by hansson_14 on 2007-12-30
Thanks a lot - just as I thought it seems very easy and logical. I will try soon. :)

---


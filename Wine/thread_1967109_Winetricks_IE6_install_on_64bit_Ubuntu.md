---
title: "Winetricks IE6 install on 64bit Ubuntu"
date: 2012-04-27
forum: Wine
---

### Post by lamb123 on 2012-04-27
"This package does not work on a 64-bit installation"

How to overcome that? Need IE6 to install another program.

---

### Post by oldos2er on 2012-04-27
Moved to Wine.

---

### Post by lamb123 on 2012-04-29
anyone?

---

### Post by ergo-proxy on 2012-04-29
Wine on Ubuntu 12.04x64 comes with two versions 386 and 64 due to new multiarch feature in Ubuntu. Anyway, to get it working you need to define an architecture you want to use and then create a new wineprefix (it won't work for an existisng one) so do this:

export WINEARCH=win32
export WINEPREFIX=$HOME/.mynewwine32prefix/

and then as usually run winecfg and winetricks...

---

### Post by lamb123 on 2012-04-29
ty sir!

---

### Post by MrsUser on 2012-05-01
> **ergo-proxy said:**
> 

export WINEARCH=win32
export WINEPREFIX=$HOME/.mynewwine32prefix/

and then as usually run winecfg and winetricks...
Can you please explain where to put these commands? I tried this in terminal, but nothing happens. I cannot find any information on how to create a wineprefix and what the detailed steps are.

---

### Post by ergo-proxy on 2012-05-02
Yes in a terminal. Once done run 'winecfg' click ok and you will notice that a new directory is created in a path specified in the wineprefix. You have to do export each time you want use this particular wineprefix because by default wine stores its setting in ~/.wine directory and uses 64 bit architecture.

---


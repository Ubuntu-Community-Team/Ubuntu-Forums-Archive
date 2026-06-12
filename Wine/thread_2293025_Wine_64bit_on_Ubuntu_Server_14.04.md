---
title: "Wine 64bit on Ubuntu Server 14.04"
date: 2015-09-02
forum: Wine
---

### Post by xander5 on 2015-09-02
Hi i own a dedicated server running Ubuntu Server 14.04 64bit
i got a problem, i need to install wine 64 bit, i know everything about how wine and settings works, except install it.
that's what i've done from now:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.6

after:

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]winecfg[/COLOR][/FONT]

now i have the directory .wine inside the root folder but it's 32 bit wine, that's not what i need, i know i did something wrong

i know that i have to use the command 

[COLOR=#000000][FONT=courier]--enable-win64
[/FONT][/COLOR]
when i cofigure whine, but cant find a way to use configure command, any help?

thanks for your time[COLOR=#000000][FONT=courier]
[/FONT][/COLOR]

---

### Post by xander5 on 2015-09-02
i think i figured out where to place the --enable win 64, got it working but thats what i get:

checking for pthread_create in -lpthread... yes
checking for X... no
configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.

i think i am at the last obstacle before install wine :D

---


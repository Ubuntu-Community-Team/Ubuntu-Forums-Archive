---
title: "Can't modprobe fglrx"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-11-03
Hi, I have followed the HOWto to install a downloaded fglrx installer in Edgy, but after I followed all the steps, installed the driver AND compiled the module, fglrx can't be modprobed. This shows the problem:

```

roger@roger-desktop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

roger@roger-desktop:~$ sudo modprobe fglrx
Password:
FATAL: Error running install command for fglrx


```

---

### Post by rogeriovinhal on 2006-11-05
up

---

### Post by Brakbabord on 2006-11-05
I don't understand, if "fglrxinfo" is allright, so fglrx is already loaded !

---

### Post by rogeriovinhal on 2006-11-05
lsmod | grep fglrx returns nothing, this means it isn't, right?

---

### Post by xstaticxgpx on 2006-11-05
fglrxinfo is not alright, its using a mesa 3d driver. I sometimes get that after restarting x (control + alt + backspace)

are you sure you did the module-assistant prepare,update then module-assistant build,install fglrx steps?

---

### Post by rogeriovinhal on 2006-11-05
Yes, I did it correctly. If I didn't, it wouldn't find the fglrx module.

---

### Post by xstaticxgpx on 2006-11-05
> **rogeriovinhal said:**
> Yes, I did it correctly. If I didn't, it wouldn't find the fglrx module.

well from what you posted it seemed like it **couldn't** find the fglrx module... which was why 

[QUOTE=rogeriovinhal]lsmod | grep fglrx returns nothing[/QUOTE]

---

### Post by rogeriovinhal on 2006-11-08
Issue solved. fglrx NEEDS gcc-4.0 to compile, so I installed it and temporary linked /usr/bin/gcc to gcc-4.0.
Now everything is fine.

I added this to [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) so everyone can see that now.

---


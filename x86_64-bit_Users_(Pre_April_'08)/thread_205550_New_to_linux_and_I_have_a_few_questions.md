---
title: "New to linux and I have a few questions"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Adam4491 on 2006-06-28
hey, is there any way to install new fonts on linux?
the default font for firefox doesn't look too good, and since it doesnt have the default windows font(s) alot of sites look weird

also, how do I update the drivers for a geforce 6200?
currently, the graphics are doing the same thing as windows does before I update the drivers to the latest ones. When I scrowl down it lags alot, and when I type stuff it lags abit too.


I know linux isn't really user friendly, but I'm willing to learn with alittle help from people :]

what are also some good resorces on installing, un-installing, updating.. ect... apps for ubuntu?

thanks in advance,
Adam.

---

### Post by Rui Pais on 2006-06-28
hi
to the geforce it's NVidia drivers, check this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

About install/unistall apps, its simple manage apt. Check this:
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)
or/and use synaptic.

You could type 
```
sudo synaptic
```
and do a search for "font" you will find a lot :)

edit: ho, who ever said linux isn't friendly user? i always find it enough friendly :)

---

### Post by aysiu on 2006-06-28
Please don't type ```
sudo synaptic
``` Type ```
gksudo synaptic
``` instead.

If you want to know why, read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Adam4491 on 2006-06-28
hey
thanks for the replies


but


> atom@atom-desktop:~$ sudo apt-get install linux-amd64-generic
Reading package lists... Done
Building dependency tree... Done
linux-amd64-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
atom@atom-desktop:~$




does this mean it's the latest version? if so I guess it's time to get  a new graphics card, lol.

---

### Post by Adam4491 on 2006-06-28
the lagging of scrowling and other things isn't as bad
but it isn't at it's best
I guess I have to configure my graphics card, or could my dual boot of windows and ubuntu be causing this problem?

---

### Post by tseliot on 2006-06-28
[QUOTE=Adam4491]hey
thanks for the replies


but





does this mean it's the latest version? if so I guess it's time to get  a new graphics card, lol.[/QUOTE]
It means that you already have the kernel and the restricted modules. Now you can go ahead with the guide and install the nvidia driver

---

### Post by Rui Pais on 2006-06-28
[QUOTE=Adam4491]does this mean it's the latest version? if so I guess it's time to get  a new graphics card, lol.[/QUOTE]
Thats your kernel. 

You need to get the driver (module, under linux terminology) configure your xorg.conf, load the module, restart X.

Please, read carefully the 1st of the links in my post. Check first Method 1.

edit: Oops, tseliot himself was quicker!

---

### Post by Adam4491 on 2006-06-28
ah okay
installed perfecrtly now
^_^


and when you said search for "font", do you mean on google or on ubuntu, or the ubuntu forums?

---

### Post by Rui Pais on 2006-06-28
[QUOTE=Adam4491]when you said search for "font", do you mean on google or on ubuntu, or the ubuntu forums?[/QUOTE]

no, inside synaptic. There is a button for "Search" on main toolbar. 
Or you can use:
```
aptitude search font
``` from a terminal

---


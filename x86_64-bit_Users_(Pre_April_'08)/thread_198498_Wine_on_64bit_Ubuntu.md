---
title: "Wine on 64bit Ubuntu?"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanityscourge on 2006-06-17
I'm looking to get Wine on ubuntu 64 bit, but I'm an ABSOLUTE newb to linux as I just made the switch 7 hours ago.

I wiped my hard drive so I can't dual boot, and I need to wait to get Cedega.

Any help?

---

### Post by Winblowz on 2006-06-17
As far as I know, there is no WINE available for 64-bit linux. Sorry.

---

### Post by mikeyrb on 2006-06-17
There is no compiled 64-bit version, but that doesn't mean you can't use the 32-bit version.  Just download this package: [wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb")

I can't remember if all dependencies are met or what not, but you can install this package using dpkg: dpkg -i --force-architecture wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb

If you look in synaptic, you should be able to find 32-bit alsa libs, those might help.  If you have problems, just respond and we'll see what we can figure out.

---

### Post by Kilz on 2006-06-17
[QUOTE=sanityscourge]I'm looking to get Wine on ubuntu 64 bit, but I'm an ABSOLUTE newb to linux as I just made the switch 7 hours ago.

I wiped my hard drive so I can't dual boot, and I need to wait to get Cedega.

Any help?[/QUOTE]
[I have a howto to help people setup 32 bit wine on 64 bit dapper.]("http://www.ubuntuforums.org/showthread.php?t=185557")  :D  But yes Cedega is the esiest way to play games, I use it myself. Wine will work in a lot of situations. But the $15 dollar subscription I paid to get Cedega has saved me lots of hours trying to get games running in wine. I use wine mainly to run IE and dvdshrink.

---

### Post by sanityscourge on 2006-06-17
Thanks, but I think I'll try Cedega when I get the money. I have no idea how to do anything on linux :x

---

### Post by Kilz on 2006-06-17
[QUOTE=sanityscourge]Thanks, but I think I'll try Cedega when I get the money. I have no idea how to do anything on linux :x[/QUOTE]
The only way to find out is to read and try.  :D

---


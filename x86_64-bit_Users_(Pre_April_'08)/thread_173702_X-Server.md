---
title: "X-Server"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbrown352001 on 2006-05-10
Hello,
I am new to linux period. I have decided to put ubuntu on my system as a secondary to windows xp. I am installing it on a HD all by itself, which is my SATA. The problem I am having is once my installation is complete and I try to start Ubuntu Kernel 2.6.12-9-amd64-Generic, and I get the message that X-Server did not load, restart my system once GDM is configured correctly. What should I do?

Dual 939 AMD 64 3200+ 2.05 GHz
2.0 Gig Dual Channel 
Radeon x1600 256
170 Gig SATA
200 Gig IDE

---

### Post by skylark on 2006-05-11
Hi,

You could try:
sudo dpkg-reconfigure xserver-xorg

to reconfigure your video card. If this doesn't work try:
sudo apt-get install xorg-driver-fglrx

let us know how it goes

---

### Post by zenandruby on 2006-05-11
A few things.

[LIST=1]
[*]Try to select the supported resolutions with:
```
sudo dpkg-reconfigure xserver-xorg
```


[*]If that doesn't help, try to install the new drivers. 
You can read more [here]("http://www.ubuntuforums.org/showthread.php?t=159233&highlight=x1600")
and [here]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide")


[*]If you can't get it to work and are just fine with common resolutions, you can change the driver section in /etc/X11/xorg.conf to "vesa". For example:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		**"vesa"**
	BusID		"PCI:1:0:0"
EndSection
```

[/LIST]

I hope this help. :)

---

### Post by jbrown352001 on 2006-05-11
Hello,
Ok I manually set up my video card. This did not work. I went in and read the log file. The last line there says "No screens detected." 

Does anyone know what would cause this?

---

### Post by jbrown352001 on 2006-05-11
This may be of use in trying to find the source of my problem too...the file /etc/X11/xorg.conf does not exist. I have went completely through etc and cannot find it anywhere.

---

### Post by turbojugend_gr on 2006-05-12
> This may be of use in trying to find the source of my problem too...the file /etc/X11/xorg.conf does not exist. I have went completely through etc and cannot find it anywhere.

try "sudo pico /etc/X1186/xorg.conf" or sth
or try "locate xorg.conf"

---


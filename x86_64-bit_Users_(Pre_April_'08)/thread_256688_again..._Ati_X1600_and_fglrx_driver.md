---
title: "again... Ati X1600 and fglrx driver"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschievano on 2006-09-13
please forgive me, but I can't go out of this situation...
I have an Asus Eax1600Pro ATI video card that works perfectly with windows... but not with linux.

I follow again and again the instruction on wiki/forums to install the ati driver.

Everythings seems ok, but no fglrx.

LET'S GO:
xorg.conf:
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	Option 		"UseInternalAGPGART" "no" #motherboard asus a8n-e nvidia based
	BusID		"PCI:1:0:0"
EndSection
...
Section "DRI"
	Mode	0666
EndSection

```

from a terminal:
```

mschievano@mschievano-desktop:~$ fglrxinfo
Error: couldn't find RGB GLX visual!

```

my pc is an assembled one, not HP like "wiki troubles"
I run dapper 64 bit.

what can i do? 

thanks

---

### Post by Kilz on 2006-09-13
> **mschievano said:**
> please forgive me, but I can't go out of this situation...
I have an Asus Eax1600Pro ATI video card that works perfectly with windows... but not with linux.

I follow again and again the instruction on wiki/forums to install the ati driver.

Everythings seems ok, but no fglrx.

LET'S GO:
xorg.conf:
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	Option 		"UseInternalAGPGART" "no" #motherboard asus a8n-e nvidia based
	BusID		"PCI:1:0:0"
EndSection
...
Section "DRI"
	Mode	0666
EndSection

```

from a terminal:
```

mschievano@mschievano-desktop:~$ fglrxinfo
Error: couldn't find RGB GLX visual!

```

my pc is an assembled one, not HP like "wiki troubles"
I run dapper 64 bit.

what can i do? 

thanks

What version of the driver and wiki were you using?

---

### Post by jespdj on 2006-09-13
I also have an Asus video card with ATI X1600XT, with 256 MB video RAM.

I'm using Ubuntu 6.06.1 AMD64. I did this to install the ATI driver:

1. Go to [ATI website](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300), follow "Linux Display Drivers and Software" / "Linux x86_64" /  "RADEON 8500 Series and higher" / "ATI Proprietary Linux x86_64 Display Driver for XFree86 / X.Org Version 8.28.8".
2. Download "ATI Driver Installer" (52.7 MB).
3. Run the installer:
```
sudo ati-driver-installer-8.28.8.run
```
4. Click "Next" a few times.
5. Run this:
```

sudo aticonfig --initial
sudo aticonfig --resolution=0,1920x1200

```
(not sure if the second line was really necessary).
6. Reboot.
7. Help, X doesn't get started! I'm missing libstdc++5. Run this to download and install it:
```
sudo apt-get install libstdc++5
```
8. Reboot (command: "sudo reboot").

And it starts up with my screen on 1920x1200 without problems.

---

### Post by Kilz on 2006-09-13
> **jespdj said:**
> I also have an Asus video card with ATI X1600XT, with 256 MB video RAM.

I'm using Ubuntu 6.06.1 AMD64. I did this to install the ATI driver:

1. Go to [ATI website](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300), follow "Linux Display Drivers and Software" / "Linux x86_64" /  "RADEON 8500 Series and higher" / "ATI Proprietary Linux x86_64 Display Driver for XFree86 / X.Org Version 8.28.8".
2. Download "ATI Driver Installer" (52.7 MB).
3. Run the installer:
```
sudo ati-driver-installer-8.28.8.run
```
4. Click "Next" a few times.
5. Run this:
```

sudo aticonfig --initial
sudo aticonfig --resolution=0,1920x1200

```
(not sure if the second line was really necessary).
6. Reboot.
7. Help, X doesn't get started! I'm missing libstdc++5. Run this to download and install it:
```
sudo apt-get install libstdc++5
```
8. Reboot (command: "sudo reboot").

And it starts up with my screen on 1920x1200 without problems.


I have noticed some people have lots of trouble with acceleration and the new 8.28.8 drivers. 8.27.10 has issues so I dont recommend it, but [8.26.18]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run") were good. Then use [this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually") but edit the commands for the older driver. Sometimes the newest isnt nessasarly the best.

---


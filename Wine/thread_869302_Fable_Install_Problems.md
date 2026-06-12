---
title: "Fable Install Problems"
date: 2008-07-24
forum: Wine
---

### Post by chaosdesigner on 2008-07-24
Hi,

Im trying to Install Fable on my Ubuntu 8.04 64bit System but it wont even install. According to the Wine AppDB should it be possible to install Fable and (almost) play it perfect, but when i try to install it, this Message pops up:

Error: -1603 Fatal Error while trying to Install.

(This Message was originally in German, here is the original, if somebody does care: 

Fehler: -1603 Schwerer Fehler bei der Installation.

Weitere Informationen finden Sie in der Windows Installer-Hilfe (Msi.chm) oder im MSDM.)

Does anybody how to solve this problem?

Im mounting the cds in a virtual drive through Acetone, if this makes a difference to somebody...

thx

---

### Post by Caeliferum on 2008-07-24
Fable is developed by Microsoft Game Studios, so its really really REALLY DirectX heavy. That said, I think we need to take a look at your graphics card first.

---

### Post by chaosdesigner on 2008-07-24
rigth, these are the specs for my card:
```


id:	display
description: 	VGA compatible controller
product: 	C51 [GeForce 6150 LE]
vendor: 	nVidia Corporation
physical id: 	5
bus info: 	pci@0000:00:05.0
version: 	a2
width: 	64 bits
clock: 	66MHz
capabilities: 	pm msi vga_controller bus_master cap_list
configuration:	
driver	=	nvidia
latency	=	0
module	=	nvidia

```

Hope this will help findeing an solution.

---


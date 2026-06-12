---
title: "Installing USB drivers"
date: 2013-05-17
forum: Wine
---

### Post by timswait on 2013-05-17
I'm trying to set up a USB temperature and humidity datalogger to work in Ubuntu through Wine. I've installed the software by running the setup.exe file, in Windows this would also install the drivers for it. The program runs but it will not communicate with the logger. My output to dmesg gives these lines which refer to the logger:
```
[    2.136617] usb 3-1: New USB device found, idVendor=10c4, idProduct=ea61
[    2.136623] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.136627] usb 3-1: Product: TempRH DataRecorder
[    2.136630] usb 3-1: Manufacturer: CEM

```
So it is being recognised in Linux. How can I make it visible through Wine? The installation CD has a folder called Driver>x64 and in there are two .sys files, which I presume are the drivers. Can I copy these somewhere to "install" the drivers in Wine?
Cheers

---

### Post by gordintoronto on 2013-05-17
I could be wrong, but I don't think you need drivers. The device is completely recognized.

See: [http://sourceforge.net/p/vdl120/bugs/3/](http://sourceforge.net/p/vdl120/bugs/3/)

---

### Post by Mark Phelps on 2013-05-17
You can not use Wine to install drivers, and even if you could, they would not work as they are Windows drivers -- and you need Linux drivers.

---


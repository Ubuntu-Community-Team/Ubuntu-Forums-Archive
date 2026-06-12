---
title: "Getting Wifi DOngle To Work"
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-06-30
I have a USB Wifi stick thing that my desktop uses to connect to the wireless hub. It's a "ez connect N SMCWUSBS-N2" affair.

Now, i'd so frakking love this to work under Linux, but i can't seem to get it going.

I have the disc that came with it which has XP 32 and 64bit drivers, aswell as vista 32 and 64bit drivers.

i tried installing through ndiswrapper, but somewhere along the lines i get the following error repeated about 20 times.

```
module configuration already contains alias directive
```

However, ndiswrapper says the driver is installed:

```
joey@joey-desktop:~$ ndiswrapper -l
rt2870 : driver installed
device (083A:B522) present 
```

Also, 
```
lsusb
```

gives me
```
Bus 002 Device 006: ID 083a:b522 Accton Technology Corp.
Bus 002 Device 004: ID 0d49:7310 Maxtor
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 003: ID 06a3:8020 Saitek PLC
Bus 001 Device 002: ID 04d9:048e Holtek Semiconductor, Inc.
Bus 001 Device 001: ID 0000:0000
```

running 
```
dmesg | grep ndiswrapper
```
tells me that the driver [XP 64 bit ] isn't a 64 bit driver and thus won't work.

```
0_o
```

over to you genii - can you help?

*[i'm using 64bit Ubuntu Hardy on a AMD 64 x 2 3.0GHZ machine with 4gb ram and Ubuntu on it's own 160GB harddrive.]*

---


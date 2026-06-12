---
title: "Wireless, ndiswrapper and 64bit"
date: 2007-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by RocketRanger on 2007-06-17
So this is yet another wireless problem thread. 

I have an zyxel zyair G302-v3 wireless card with realtech chipset. Here's what lspci calls it:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: ZyXEL Communication Corporation Unknown device 340d
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 2800 [size=256]
        Memory at f0000800 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

ndiswrapper seem to be the solution that works for most people. I have installed it from source and installed my driver. Here's the output from ndiswrapper -l

net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

However when I try see if it's load with dmesg | grep ndiswrapper here's the problem.

[  960.666908] ndiswrapper version 1.47 loaded (smp=yes)
[  960.670484] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  960.670490] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8185'
[  960.671071] ndiswrapper (load_wrap_driver:118): couldn't load driver net8185; check system log for messages from 'loadndisdriver'
[  960.679368] usbcore: registered new interface driver ndiswrapper

So where do I go from here? I have been searching for a 64bit version of the driver, however zyxel doesn't seem to be offering one. Is there a way to trick the kernel into using this driver?

Any ideas appreciated.

---

### Post by atararx on 2007-06-17
I have similar problems with by bcm4310 drive I either get 64 versions which dont work or I get 32 versions which give me the same error you get.

This is what I get when I use a 64 version.

[  585.385006] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  585.390257] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff88b2980e
[  585.390263] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[  585.390275] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  585.390281] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  585.390292] ndiswrapper (mp_halt:258): device ffff81001842e500 is not initialized - not halting
[  585.390299] ndiswrapper: device eth%d removed



$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

It seems to me that we have very similar issues.
I wish there was someone out there who could solve our problems once and for all.

---

### Post by Jouke74 on 2007-06-18
I assume you already checked the Ndiswrapper website for card compatibility and 64 bit drivers for your card? This might be an open door but: check which chipset is on your wireless card, and try a 64 bit driver from another company using the same chipset.

---

### Post by RocketRanger on 2007-06-18
> **Jouke74 said:**
> I assume you already checked the Ndiswrapper website for card compatibility and 64 bit drivers for your card? This might be an open door but: check which chipset is on your wireless card, and try a 64 bit driver from another company using the same chipset.

Yes. The ndiswrapper website quotes compatability with the drivers on the accompanying cd for windows XP. The driver downloaded Zyxels website doesn't work either. There are no 64bit driver from zyxel for my card. There is an open source alternative driver for the realtech chipset which I had working for a short while. But after the first kernel upgrade in Ubuntu that would only give a false positives, claiming to have established a connection but dhcp couldn't renew my ip.

Is there another alternative? I.e. a list of propriatary drivers for the various chipsets somewhere?

---

### Post by RocketRanger on 2007-06-19
I'm sorry about this but I still haven't figured this out. If anyone has any ideas they are most welcome. So.. *bump*

---

### Post by RocketRanger on 2007-06-19
This is certainly a 64bit problem. I have tried the same procedure with a clean i686 install of Ubuntu and compiling and installing ndiswrapper was easy as pie. Even the signal strength meters are working now.

So unless there exists a proper driver for the realtech chipset I'm afraid I'm going to take the regressive step and revert to a 32bit Ubuntu untill this has been resolved (please read, work as easily as it did in Dapper).

---


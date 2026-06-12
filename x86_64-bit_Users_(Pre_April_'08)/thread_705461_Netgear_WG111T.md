---
title: "Netgear WG111T"
date: 2008-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sl@y3D for my n@me on 2008-02-23
Greetings fellow ubuntu users! I am quite new to this interesting world of linux, so I don't have much knowledge regarding anything that you won't find in windows.

On the i386 version of ubuntu 7.10, I can get my wireless card (wg111t) to work with ndiswrapper. Since I have a 64bit processor, I want to run the AMD64 version, but when I try and get it to work with the same steps that work under the i386 version, it doesn't start the wireless adapter. On ndisgtk, it says athfmwdl.inf is installed and the device is there, but not the netwg11t.inf driver. I think the first one is the bootloader device, while the latter is the actual device driver. When it works on the i386 version, the netwg11t.inf driver is detected and loaded instead of the athfmwdl.inf driver. This means I have no internet in ubuntu, so I have to use xp for now. I want to use AMD64 however, because there are certainly quite a few advantages over i386. Can anyone give a noobs guide how to set it up properly?

Thanks.

---

### Post by Zzzach on 2008-02-29
I'm having the same problem. Someone said you have to use winxp 64-bit drivers if you're using ubuntu 64-bit. The problem is netgear doesn't make any 64-bit drivers!!! So apparently it won't work? I've been trying for the last hour or two to get this working and it looks like it is impossible in 64-bit! Is there a way to make the wg111t work in 64-bit ubuntu?? :confused::mad:

---

### Post by Sl@y3D for my n@me on 2008-03-11
I don't know if bumping threads is allowed, but I would really appreciate some help on this.

---

### Post by frootloop on 2008-04-25
I've just upgraded from i386 Gutsy to AMD64 Hardy, and I'm running into the same problem. Using ndiswrapper and the windows driver from the WG111T cd, I managed to get it working under i386 Gutsy. I clean installed hardy AMD64 and I have had no luck. 

lsusb shows the device is there:
Bus 007 Device 008: ID 1385:4251 Netgear, Inc 

Ndiswrapper -l shows:
athfmwdl : driver installed
	device (1385:4251) present
netwg11t : driver installed

modprobe ndiswrapper

which I think means the bootloader is working, but the device driver is not?
ndiswrapper -v shows 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 

so it looks all up to date.


A dig in the message log shows:[ 8281.212578] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 8281.343375] usb 7-3: reset high speed USB device using ehci_hcd and address 8
[ 8281.477116] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 8281.477124] ndiswrapper (load_sys_files:210): couldn't prepare driver 'athfmwdl'
[ 8281.478246] ndiswrapper (load_wrap_driver:112): couldn't load driver athfmwdl; check system log for messages from 'loadndisdriver'
[ 8281.478276] usbcore: registered new interface driver ndiswrapper

Does this mean I cant use the current windows driver becasue its 32bit? That would make sense AFAIK, seeing as you cant use a 32bit driver on 64bit OS, I was kinda hoping ndiswrapper would somehow only expose a 64bit link to the OS.


Syslog shows pretty much the same:
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.212578] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.343375] usb 7-3: reset high speed USB device using ehci_hcd and address 8
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.477116] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.477124] ndiswrapper (load_sys_files:210): couldn't prepare driver 'athfmwdl'
Apr 26 03:39:17 frooty-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver athfmwdl 
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.478246] ndiswrapper (load_wrap_driver:112): couldn't load driver athfmwdl; check system log for messages from 'loadndisdriver'
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.478276] usbcore: registered new interface driver ndiswrapper


I thought I'd chase a driver from the chipset perspective, but it looks like madwifi doesnt support USB Atheros :(
Has anyone gotten this working on AMD64? Would really appreciate some help, I'm pulling my hair out! ;)

Thanks!

---

### Post by Kilz on 2008-04-25
> **frootloop said:**
> 
modprobe ndiswrapper

which I think means the bootloader is working, but the device driver is not?
ndiswrapper -v shows 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 

so it looks all up to date.


A dig in the message log shows:[ 8281.212578] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 8281.343375] usb 7-3: reset high speed USB device using ehci_hcd and address 8
[ 8281.477116] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 8281.477124] ndiswrapper (load_sys_files:210): couldn't prepare driver 'athfmwdl'
[ 8281.478246] ndiswrapper (load_wrap_driver:112): couldn't load driver athfmwdl; check system log for messages from 'loadndisdriver'
[ 8281.478276] usbcore: registered new interface driver ndiswrapper

Does this mean I cant use the current windows driver becasue its 32bit? That would make sense AFAIK, seeing as you cant use a 32bit driver on 64bit OS, I was kinda hoping ndiswrapper would somehow only expose a 64bit link to the OS.


Syslog shows pretty much the same:
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.212578] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.343375] usb 7-3: reset high speed USB device using ehci_hcd and address 8
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.477116] ndiswrapper (check_nt_hdr:150): **kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B**
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.477124] ndiswrapper (load_sys_files:210): couldn't prepare driver 'athfmwdl'
Apr 26 03:39:17 frooty-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver athfmwdl 
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.478246] ndiswrapper (load_wrap_driver:112): couldn't load driver athfmwdl; check system log for messages from 'loadndisdriver'
Apr 26 03:39:17 frooty-desktop kernel: [ 8281.478276] usbcore: registered new interface driver ndiswrapper


I thought I'd chase a driver from the chipset perspective, but it looks like madwifi doesnt support USB Atheros :(
Has anyone gotten this working on AMD64? Would really appreciate some help, I'm pulling my hair out! ;)

Thanks!

I bolded the problem.

---

### Post by Viper Daimao on 2008-04-30
he's right. if you're going to use a 64 bit OS you have to have 64 bit drivers. You would run into this same exact problem on Windows 64, and in fact, if you search on google you'll see many are. 

You can try this driver, but I wouldn't hold my breath on it working.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by Sl@y3D for my n@me on 2008-05-01
So Netgear are part of the problem of how people can't move to 64bit. They are total rubbish. I hope someone makes an unofficial driver soon.

---


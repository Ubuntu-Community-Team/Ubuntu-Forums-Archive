---
title: "First experience with V6.06 on Turion X2 + some questions"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lonthong on 2006-08-03
First post, first venture into ubuntu/linux world. So far so good.........
I installed v6.06 64bit onto following laptop:
BenQ Joybook P41
AMD Turion X2 TL-50
512 MB DDR2 Ram
ATI X1100 , shared upto 256MB (set "auto" in bios - took 64MB of system ram)
Realtek HD Audio
Realtek RTL 8139 LAN
Atheros AR5006EG WLAN
Bluetooth stack Toshiba
Modem HDAUDIO Soft Data Fax V.92 with SmartCP
HD Fujitsu 80GB SATA 5400rpm (Ubuntu called it 'sda')

Installation process was really smooth & in less than one hour system was up and running. =D> :-\" 
LAN, audio was working out of the box. Also screen was correctly configured at 1280 x 800 60hz. However, I don't know if wlan, bluetooth, or modem will work as I don't have router or bluetooth enable device to test. As for modem, I just have not tried it yet
I set gateway, dns, ip address and immediately firefox brought me to any webpages that I click...:p 

Initially I had some problems to mount my FAT data partition but from one of threads here, I managed to solve this.......:mrgreen: 

Later on auto update advised for various updates (as many as 140 items) which I allowed. It then downloaded & auto installed those updates (some were failed to download though). Again no problem......
Prior to update, scrolling of synaptics touchpad did not work & now it works.:-D 

Reading through system documentation, I found out that 3D video acceleration did not work so I followed the guide to install xorg-driver-fglrx package.
After reboot, I checked again & 3D acceleration worked but I faced my first problem: screen resolution was set to 1024 x768 & I can't increase it (system-preference-screen resolution), 1024x768 was the max.
I reconfigure & this time I choosed ATI instead of fglrx. Rebooted & I am back to 1280x800 but then 3d acceleration did not work.
Anyone can lead me on how to deal with this minor issue???

Another problem that I faced was saving feature of open office. It showed a save window dialogue with just square fonts.
How to solve this?
[IMG]http://img214.imageshack.us/img214/6341/shotgc0.jpg[/IMG]

Some general and probably stupid questions that I like to ask you all:
- device driver update. Is this included in auto update or do I have to manually look for my specific devices & manually installed them - like what I did for windows???
- Anyone know of a good CAD viewer program?

---


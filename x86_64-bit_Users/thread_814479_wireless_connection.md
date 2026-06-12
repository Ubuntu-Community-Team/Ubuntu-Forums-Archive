---
title: "wireless connection"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by TouchuvGrey on 2008-05-31
in my windows computer i can right click on the
wireless icon on the toolbar and see "available
networks" and easily connect to my home wireless
network. How do i do the equivalent in ubuntu 64
8.04 ?

---

### Post by Novega on 2008-05-31
Forgive me for sounding overly simple, but...
left click on the network connection icon on the toolbar (in the upper right hand corner by default I believe)

---

### Post by TouchuvGrey on 2008-05-31
When i do that i get 

Wired Network

    Connect to 802.1X Protected Wired Network

Manual Configuration

The Blue "Wireless: light is on so i'm presuming that
wireless is woeking, it's just that i can't find
anything to connect to. I have an identical machine
5 feet away from it connecting very well on windows
xp.

---

### Post by bford16 on 2008-06-01
You may need to install the proprietary driver for your wireless card. If you open a terminal, and type the following, what do you get?
```
lspci | grep 802.11
```

My computer gives me:

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

If you have a Broadcom Wireless card, you have to install and enable the driver, while you are connected to a wired network. You do this with System>Administration>Hardware Drivers. A reboot will be required.

---

### Post by TouchuvGrey on 2008-06-01
i get

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

System>Administration>Hsardware Divers shows me

Broadcom B42 wireless driver enabled and in use. hovering cursor over it shows me

" while this driver is free software, it relies on
proprietary firmware which cannot be legally shipped with
the operating system. Your hardware will not work without
the firmware."

the blue wireless light is on.

---


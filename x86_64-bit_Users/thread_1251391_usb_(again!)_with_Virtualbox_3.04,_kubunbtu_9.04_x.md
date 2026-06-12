---
title: "usb (again!) with Virtualbox 3.04, kubunbtu 9.04 x86 64"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by emamm on 2009-08-27
Hello

I have been using VB under 9.04 for a while and had no problem with most of it. However I couldn´t get any of my usb devices to work within VB.  

As far as I know I have the lastest VB (3.04) and the lastest stable version of kubuntu (that is, 9.04) (both of them from a fresh install).  The usb devices (external usb hd and a hp scanner) show up on the list of available devices. I can check both or either box if I want to, but I can´t go any further.  No devices are recognized by the virtual XP.  

I have edited /etc/fstab to include the line
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
but to no avail.

I thought the lastest version of VB would work straight out of the box.  Dream on!

Suggestions are most welcome.

Many thanks

Ed

---

### Post by fatbotgw on 2009-08-27
If you're using the virtualbox from the repositories, it doesn't support using USB.  To get the USB, you have to download and install the version from Sun.

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")


Edit:  Of course, if you already have that version...I have no idea.

---


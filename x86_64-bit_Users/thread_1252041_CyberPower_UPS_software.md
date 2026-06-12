---
title: "CyberPower UPS software"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by ilna on 2009-08-28
Hi!

I have CyberPower Value 500 UPS. Last one can be attached to USB port. Manufacturer suggest i386 deb only. Is there known software to track this UPS status under x86_64 platform?

---

### Post by cariboo on 2009-08-29
Have a look at [NUT]("http://www.networkupstools.org/").

Nut is in the repositories. Just click the link.

[apt://nut](apt://nut)

---

### Post by ilna on 2009-08-29
**cariboo907**,

Thanks! - will dig in.
What does apt://nut mean?

---

### Post by Thelasko on 2009-08-29
I have a CyberPower UPS.  You really don't need to install any software.  Ubuntu will detect it automatically.  To change the configuration, simply go to system>preferences>power management and click on the "on ups power" tab.

---

### Post by ilna on 2009-08-29
> **Thelasko said:**
> I have a CyberPower UPS.  You really don't need to install any software.  Ubuntu will detect it automatically.  To change the configuration, simply go to system>preferences>power management and click on the "on ups power" tab.

- I use Kubuntu and have not found anything related to UPS in "Power Management".

- hal have detected the UPS and started 'hald-addon-hid-ups' process with listening on /dev/usb/hiddev0. Have tried to configure nut, but have not realized how to define the UPS in ups.conf - have tried 

```
[CyberPower]
       driver = usbhid-ups
       port = /dev/usb/hiddev0
```

but upsd can not connect to it.

---

### Post by ilna on 2009-08-29
With help of this article

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

I was able to make all working - up to knutclient. But there are few problems to automate all these in boot. After botting I must terminate 'hald-addon-hid-ups' process and load ups drivers manually ('sudo upsdrvctl start'). After these steps nut service becames startable.

How to boot-automate?

P.S. The thread transformed to state in which it isn't x86_64 related. It seems I have no rights to move it to another forum. Sorry.

---


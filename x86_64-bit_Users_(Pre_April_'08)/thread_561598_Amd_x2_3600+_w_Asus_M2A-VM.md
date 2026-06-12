---
title: "Amd x2 3600+ w/ Asus M2A-VM"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by psycho5 on 2007-09-27
I managed to install ubuntu 7.04 with 

Asus M2A-VM Mobo and Onboard Ati x1250 graphics
Amd x2 +3600 processor


My questions are:

Is it a problem if in device manager, 

"Vendor", "Device", and "Bus Type" is unknown for my motherboard, proc, and graphic card?

How do I install the  downloaded ati amd64 graphic drivers for linux  from the manufacturer's site? Do I really need to? 
 
My Ati Accelerated Driver is enabled under System> Restricted Drivers Manager

I need to know if installing the drivers from the website will fix  my monitor's refresh rate at higher resolution. Since on windows it works fine at 1280x1024. On Ubuntu, it flickers, and refresh rate goes down to 44Hz.

Ty for your help.

---

### Post by dcstar on 2007-09-28
> **psycho5 said:**
> I managed to install ubuntu 7.04 with 

Asus M2A-VM Mobo and Onboard Ati x1250 graphics
Amd x2 +3600 processor

My questions are:

Is it a problem if in device manager, 

"Vendor", "Device", and "Bus Type" is unknown for my motherboard, proc, and graphic card?
.........

Install the **discover1** and **xresprobe** packages, then in a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```
and see if things are now detected.

---

### Post by psycho5 on 2007-09-28
David,

discover1 and xresprobe packages, where do i get them from? I just stated using Linux this week, still very new to it.

Thank you.

---

### Post by psycho5 on 2007-09-28
nevermind, i googled it.

---


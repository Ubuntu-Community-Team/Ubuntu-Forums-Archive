---
title: "Envyng Hardy Proposed Nvidia drivers not working for me"
date: 2008-06-16
forum: x86 64-bit Users
---

### Post by tighem on 2008-06-16
That sums it up, really. No go on the new nvidia drivers in Hardy Proposed. Dell D820 (identifies as Quadro NVS). I did open a bug report but since this is proposed I doubt it's being looked at.

Manually installing the drivers fails, too. Both from within Envyng and downloading the driver myself and running the installer.

---

### Post by stchman on 2008-06-16
> **tighem said:**
> That sums it up, really. No go on the new nvidia drivers in Hardy Proposed. Dell D820 (identifies as Quadro NVS). I did open a bug report but since this is proposed I doubt it's being looked at.

Manually installing the drivers fails, too. Both from within Envyng and downloading the driver myself and running the installer.

What kind of a Nvidia card do you have?

---

### Post by tighem on 2008-06-16
Quadro NVS 110M

---

### Post by d0x! on 2008-06-16
according to nvidia's download site there is no driver that supports your card.
:(

unlike windows where you can download a modded inf to install any driver on mobile cards, that isnt the case unless nvidia releases a driver for your card?

edit: just found out that the card is supported: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) with 
[http://www.nvidia.com/object/linux_display_amd64_96.43.05.html](http://www.nvidia.com/object/linux_display_amd64_96.43.05.html)

what doesnt work about it?
have you installed "nvidia x server settings"?
basically the driver control panel

---

### Post by tighem on 2008-06-16
It simply doesn't load under the -19 kernel. Looks like it installs OK, but xorg dumps me into failsafe mode every time.

---

### Post by Trindol on 2008-06-16
When I manually installed my Nvidia driver (173.14.05) for my 8300GS, it took a lot of attempts. I ended up using synaptic and uninstalling everything related to "nvidia". No linux-restricted-modules, no nvidia-glx, no nvidia-kernel, etc. Then I installed the new driver one more time.

Not really a conclusive solution, but that's what ended up doing it for me.

---

### Post by barney385 on 2008-06-16
I had to drop back to the 18 kernel for now...

---

### Post by win2456 on 2008-06-18
after the kernel 16 update my video drivers have stopped working.  with every kernel and glx-new update, i've hopped that my card would start working, but no luck!

i have a D830 w/NVS 140M

this is getting so frustrating!  even with the kernel 16, I had my card working using the method mentioned above by Trindol... but this method has not worked for me on any of the newer kernels.

---


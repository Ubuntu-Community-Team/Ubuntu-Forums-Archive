---
title: "unable to boot with USB Keyboard"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by 3bit on 2008-02-16
Hi 

I installed Gutsy on my new Computer (x86_64)  using a PS/2 Keyboard. After installation I switched the Keyboard to an USB Keyboard, with the strange effect, that Ubuntu doesn't want to boot anymore. After Grub the message "Kernel alive" will still appear, but after some seconds the computer will reboot again (just like pressing reset). 

I tried to switch USB Keyboard support in the Motherboard Bios settings on and off: no Effect.
If I unplug the Keyboard it will boot again. If I plug it in and also plug in an PS/2 Keyboard It'll boot again, and both Keyboards work. As a workaround ill just keep the PS/2 Keyboard plugged in, but it is not a very satisfying solution. I tried also different USB ports, also no Effect.

Antother question: how is it possible to activate a USB Mouse or Keyboard while the system is running?

Thanks 
3bit

---

### Post by dayanandasaraswati on 2008-02-16
You try removing your normal keyboard and plug in your USB keyboard and try reconfiguring your Xserver with 
> sudo dpkg-reconfigure xserver-xorg

This command will open a dialogue box which will start with settings to configure your monitor..Do not alter any of those settings. Keep default settings and then continue for few steps when it'll start configuring keyboard. Now follow the steps given and continue till then end. Restart the system with the usb keyboard plugged in and see what happens. I feel that ubuntu is unable to detect the usb keyboard so only it may be behaving weird. The above command will add your usb keyboard to the xorg.conf file. Thus next time ubuntu boots, it would detect your keyboad and there'll be no problem. Try if this works

---


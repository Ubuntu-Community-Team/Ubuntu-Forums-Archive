---
title: "No power to usb"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by idiotonuni on 2008-12-13
I recently bought a new computer with an Intel Pentium E5200 Dual Core processor.  I was stoked to see how linux performed on it, but when i booted up ubuntu, I had no power to any usb or ps/2 ports.  How can I get power to these ports?

---

### Post by |{urse on 2008-12-13
you might want to check your motherboards manual to be sure that the wires are properly connected RWGB (red, white, green, black)

---

### Post by idiotonuni on 2008-12-14
It was a factory pc, from gateway, and the usb works while running windows.

---

### Post by Sef on 2008-12-14
1) What are your system specs?

2) What version of Ubuntu are you running?

---

### Post by idiotonuni on 2008-12-16
System specs: Gateway dx4720-03
Processor: Intel E2500 Dual core, 4 gigs of ram, nvidia geforce 7100 integrated card, linksys wmp54g version 4.1.  Any other specs you want are here: [http://www.gateway.com/systems/product/529668198.php](http://www.gateway.com/systems/product/529668198.php)

And I was running the 64 bit version of Intrepid, and I tried the 32 bit version of most other recent releases.

---

### Post by idiotonuni on 2009-01-04
Any ideas would be greatly appreciated.

---

### Post by clandau on 2009-01-24
I have the same computer and the same problem with Ubuntu 8.04.1 LTS. 

I found by trial and error that if, after booting the CD and selecting the installation language, you press F6 and append the installation option "noapic" or "nolapic", it will run OK. 

Does this computer have a broken APIC? 

The "noapic" or "nolapic" option is also necessary when installing Fedora 8. Fedora 10 seems to have worse problems on this computer.

---

### Post by aeilos on 2009-01-25
I have this problem as well with 64 bit intrepid. USB port has power with windows.

---


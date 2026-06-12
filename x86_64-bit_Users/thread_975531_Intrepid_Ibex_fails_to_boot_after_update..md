---
title: "Intrepid Ibex fails to boot after update."
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by egarcia1970 on 2008-11-08
Hello folks. First time poster here. I downloaded and installed without hassle Ubuntu 8.10 64 on this machine:

-ASUS M2N-SLI Motherboard.
-AMD Phenom X3 Processor.
-4 GB Kingston DIMM.

First time boot was fine, and after configuring my LAN manually (I use static IPs in my home network) the updater wake up and told me there were several updates available, among them Compiz and a kernel upgrade. I accepted everything, downloaded, installed the packages, and rebooted as instructed by the updater. Then all hell broke loose. :confused: The beeper went ballistic, and the following message could be read briefly on the screen before going completely blank:

ACPI: Expecting a [Reference] .... (couldn't write down the rest)

What now? It seems obvious ACPI is causing problems here, but I'm not sure how to troubleshoot it. I'm afraid to damage the hardware. What's more puzzling is it worked perfectly OK before the update, and I don't know which one caused this, or how to revert changes to the "last known good configuration" or its equivalent. Any help will be greatly appreciated.

Thanks in advance,
ELG

---

### Post by tvtech on 2008-11-08
okay I would suggest going in and removing your manual changes to your network interface.  I had many problems with this where I would manually assign my desktop and it would no longer boot. similar error messages to what your experiencing, if you can't get into safe mode which I couldn't your going to need to do this via a live cd

so your going to want to navigate to /etc/network/interfaces 

if you've made it into text mode in rescue mode 

```
sudo nano /etc/network/interfaces
```

and your going to want to change it to
 ```
auto lo
iface lo inet loopback

```

this solved my problems before.  I gave up on the manual ip address what type of network adaptor are you using? I had a broadcom gigbit adaptor that caused these problems. my intelpro 1000 isn't a problem on my server. I've only run into this when using a gui

---

### Post by egarcia1970 on 2008-11-09
Hi tvtech, thanks for your repy. I was able to boot into recovery mode and edited the file /etc/network/interfaces, but it containts the same two lines as yours... :-k

---


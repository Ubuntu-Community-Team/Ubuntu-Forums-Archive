---
title: "How to Wlan to work"
date: 2005-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Isengrim on 2005-01-23
Hello,

I just installed ubuntu warthog hog and I was wondering how to gen my Wlan to work.
Ubuntu recognised my wlan card (broadcom) but I can't get a connection with my AP with that sstandard tool.
Does anyone know what tot do?

Thanks

---

### Post by s_p_a_r_k_y on 2005-01-23
cardname will be something like eth1 or wlan0

iwconfig <cardname> channel <chanelnumber>
iwconfig <cardname> essid <NETWORK ESSID>
iwconfig <cardname> key <ENCRYPTION KEY>
iwconfig <cardname> mode managed
"man iwconfig" for more options.

But the above commands should connect you to the access point. Simply type in iwconfig and see if it picks up an AP after you type in the above commands.

if so, dhclient <cardname>

---

### Post by Isengrim on 2005-01-23
Hmmz... It says no wireless extension.
My card is shown up in the device manager, so it is intalled right?

---

### Post by s_p_a_r_k_y on 2005-01-23
just the fact that it is showing up in the device manager does not mean that the driver for it is loaded. Do you know what module should be loaded for your card? If not google for it. 

Then see if the module is loaded.

lsmod | grep <module_name>

the | grep part will search lsmod's output for that module name. If it prints out a line then the driver is loaded and I'm not sure why you don't have wireless extensions. If no line appears, then 

modprobe <module_name>

If that works you will probably want to add the module to be loaded at startup time. You can do this by editing /etc/modules as root and simply adding the module name to the next available line.

---


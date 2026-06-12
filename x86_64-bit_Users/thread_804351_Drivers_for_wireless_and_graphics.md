---
title: "Drivers for wireless and graphics"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by serez on 2008-05-23
i`m helping my friend to solve his problem. he was using ubuntu 7.10 before he upgrading to 8.04
the problem is he can`t find or update the driver for his wireless device and graphic as well.
currently he use an Acer Aspire 4520 laptop.
while i`m not facing any problem on installing and managing my device drivers. i`m using Acer 4920G laptop.

hope somebody will try me (us) to find his problem. thanks

---

### Post by HunterThomson on 2008-05-23
I think all Acer laptops use athoros wireless cards. IF SO, you can use the madwifi wireless driver...

---

### Post by HunterThomson on 2008-05-23
Intel GPU's are plug and play. AMD and Nividia both need nwiswrappers drivers.

---

### Post by Jouke74 on 2008-05-23
You cannot use N**d**iswrapper for a videocard driver!! :-) 

Ndiswrapper is a tool to make Windows **Wireless** drivers run under Linux. It should be used in case you can't find any Linux driver, or if the drivers with Ndiswrapper are performing much better than the Linux drivers. According to specs you have a Acer InviLink 54Mbps Wi-Fi IEEE 802.11b/g in the Acer. I am unfamiliar what chipset this is. 

The nVIDIA GeForce 7000M is Integrated in the Acer Aspire 4520
The safer option to install these drivers is to use the restricted drivers manager under system > administration > restricted drivers. 

Another option is to download the linux drivers on the Nvidia website and use their instructiond]s to install it under Ubuntu.

Finally you can use the Envy tool / script. I don't like Envy because then I haven't got a clue what's happening, but for (many?) people it did it's magical work.

Whatever you do, just use one option and make it work. Using various "install methods" only half-way through usually messes  things up badly.

---

### Post by serez on 2008-05-23
> **Jouke74 said:**
> You cannot use N**d**iswrapper for a videocard driver!! :-) 

Ndiswrapper is a tool to make Windows **Wireless** drivers run under Linux. It should be used in case you can't find any Linux driver, or if the drivers with Ndiswrapper are performing much better than the Linux drivers. According to specs you have a Acer InviLink 54Mbps Wi-Fi IEEE 802.11b/g in the Acer. I am unfamiliar what chipset this is. 

The nVIDIA GeForce 7000M is Integrated in the Acer Aspire 4520
The safer option to install these drivers is to use the restricted drivers manager under system > administration > restricted drivers. 

Another option is to download the linux drivers on the Nvidia website and use their instructiond]s to install it under Ubuntu.

Finally you can use the Envy tool / script. I don't like Envy because then I haven't got a clue what's happening, but for (many?) people it did it's magical work.

Whatever you do, just use one option and make it work. Using various "install methods" only half-way through usually messes  things up badly.

thanks for noticing the laptop spec. btw before this i use automatix to fixed all the drivers. but now i heard that automatix is no longer for 8.04 so i`m in trouble bcoz i don`t really familiar with coding line. would u teach me?

---


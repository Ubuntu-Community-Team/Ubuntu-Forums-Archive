---
title: "RTL8111/8168B not working under feisty 64"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hannes Heller on 2007-05-05
hi,

i have troubles to get my network up.

history so far:
had the network working under edgy just fine.
upgraded to feisty upon release.
network worked initially, but then broke for unknown reasons!
(maybe unplugging / plugging the cable event, maybe battery recharger event, maybe...)
installed feisty from iso.
netwrok still doesnt work.

the hardware is detected just fine.
[lspci output line for network: 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 09)]

The Hardware is an ASUS F3JM

the network configuration was done via NetworkManagerApplet with manual IP gateway. I am supposed to be connected through a router. I am using the same configuration (with a different manual IP of course) for the workstation and it works just fine under feisty 64bit (upgraded since ubuntu warty).

the notebook does have several possible network interfaces: bluetooth and wlan. none of them are configured by myself. i want the simple ethernet to work again as in the beginning.

any ideas?

---

### Post by raidman on 2007-05-05
I'm having big problems with my Realtek RTL8111B  r8169 (ASUS M2A-VM), and different apps like samba.

I guess there is a good chance the drivers for some Realtek adaptors are broke.

---

### Post by John Jason Jordan on 2007-05-05
> **raidman said:**
> I'm having big problems with my Realtek RTL8111B  r8169 (ASUS M2A-VM), and different apps like samba.
I guess there is a good chance the drivers for some Realtek adaptors are broke.
I have the Realtek 8169SC on the motherboard for a desktop I just built for myself:

lspci|less
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)

After I put the system together I tried about a dozen different amd64 distros. Every single one failed to find and configure the onboard Realtek except Feisty and Debian Etch. Fedora 7 test3 even went into a kernel panic unless I disabled the Realtek in the BIOS.

I'm not sure, but I think the 8168 is the mobile version of the 8169. 

Mine is working just great and I haven't had any trouble at all under Feisty. I never tried any earlier versions of Ubuntu.

---

### Post by Hannes Heller on 2007-05-06
I have found a very similar and solved situation as mine:

[http://debianforum.de/forum/viewtopic.php?p=514910&sid=f9e00dea57c4feedeba2fd57b47e4a47](http://debianforum.de/forum/viewtopic.php?p=514910&sid=f9e00dea57c4feedeba2fd57b47e4a47)

the sole difference is, that it is not a notebook.
I take it, that i will need to update the bios, most likely because the r8169 driver seems to depend on it. alternatively, i guess i could install the propr. realtek driver as suggested in

[http://ubuntuforums.org/showthread.php?p=857923](http://ubuntuforums.org/showthread.php?p=857923)

---


---
title: "Ubuntu randomly freezes!! Help"
date: 2008-11-29
forum: x86 64-bit Users
---

### Post by ryclegman on 2008-11-29
hey,

I have had Ubuntu for a while now, and i really hate how it randomly freezes! It usually happens when Im watching a you tube video or on the web doing something! It also happens when i someone is uploading to my server.... My computer will freeze and my key board light will just flash,and then the files don't get uploaded. If there is any fix for this that would be great because this is really getting annoying! :mad::mad::mad::mad:

My computer:
nvidia 9600 gt
msi mother board
core 2 quad 64 bit
4 gigs of ram
500 gig sata

---

### Post by cariboo on 2008-11-30
You probably have some sort of misconfiguration that is causing a kernel panic. Is there anything in the logs that indicate why the kernel panic is happening. 

The logs are in /var/log, check  /var/log /messages and /var/log/syslog, You can view the current logs at System-->Administration-->System log. To view archived logs you will have to navigate to /var/log.

Jim

---

### Post by ryclegman on 2008-12-01
ok my freeze just happened 2 times in a row now... i was downloading something and it crashes... heres my log: 

> Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for ******** on wlan0.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address *********.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for fe80::218:f8ff:fe2d:f0f4 on wlan0.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface wlan0.IPv4 with address ************.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: New relevant interface wlan0.IPv4 for mDNS.
Dec  1 15:45:14 ryan-desktop avahi-daemon[5252]: Registering new address record for ******** on wlan0.IPv4.
Dec  1 15:45:15 ryan-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Dec  1 15:45:15 ryan-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

Also found this odd > Dec  1 15:44:54 ryan-desktop gdmgreeter[6012]: WARNING: Theme broken: must have pam-message label! 


If you need more let me know! but i think thats where it fails@!

---

### Post by dfowensby on 2008-12-01
this may sound dumb, but it seems like you need to run seperate environments: a server OS unit, and a surfing and fun machine. are you running two seperate boxes on an intranet, or running the whole thing from one command base all on the same computer without seperating the /home directory, /www directory or /var from your "fun"?
just curious.

luck -O.

---

### Post by ryclegman on 2008-12-02
I see what your saying... I will be creating a new computer soon for a dedicated server because when ever people upload to my server it crashes after a couple of minutes.... But also i had the 32 bit version be for this and it froze up as well when i was downloading things from the internet....

---

### Post by spongypants23 on 2008-12-03
Are you using an Intel 4965 AGN wireless card?

If so, download the package "linux-backports-modules-intrepid".

---

### Post by ryclegman on 2008-12-04
I figured it out its a wireless issue, and i used [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .... We will see if it works
!!!

---

### Post by ryclegman on 2008-12-05
well reverting back to hardy wont do anything.... My method did connect the hardware, but never would actually allow access to the internet. THE problem is the WIRELESS DRIVER! linksys does not provide linux drivers

---

### Post by Charlie708 on 2008-12-06
Is it a USB or PCI wireless?  Doing either lsusb or lspci will show devices connected to your computer, so you can find out the maker of the chipset of your device.

Linksys only packaged your card, a chip maker like Atheros, Broadcom or Ralink made the chipset used on it.  Finding out the chip maker is the best way to get drivers for the card.

---

### Post by ryclegman on 2008-12-07
its a pci Ralink.....

---

### Post by ryclegman on 2008-12-08
RaLink RT2561/RT61 802.11g PCI

---


---
title: "Help! Airport (non-extreme) on TiPBG4 400Mhz"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by innegable3 on 2005-10-24
Hey Linux world,

I took the plunge over the weekend to see what the fuss is about regarding Linux.  I've been a Mac user for about 5 years now, and have two Powerbooks, the one listed in the subject, and the one I'm writing this from (12in., 1.5Ghz of buttery smoothness)

I installed the PPC distro of Ubuntu 5.10 on my old Powerbook, but don't know where to start to get my Airport (NOT AIRPORT EXTREME) card running.  Can anyone help me?  

Also, I'm not a CS guy... I'm actually a graduate student in Public Affairs, so this is more of just a personal experiment. In other words, please respond in English.:smile:

---

### Post by ssam on 2005-10-24
hello

this should be very simple.

system -> administration -> networking

you will be prompted for your password.

now you see a window with the avaiable network interfaces shown. one of them will have a wireless card type icon, one a pci card type icon (for ethernet), and maybe a modem icon aswell.

select the wireless card, and click properties.

tick on the enable this connection box
put "any" for the networkname (the card will choose the strongest access point) or type in a name if you know it.

if you have a wep key put that in. (if it only has numbers and letters a-f it might be hex)

in most cases the configuration should be set to dhcp (dinamic host confuration protical) so that the router gives you an ip address, and dns information.

now click ok

now activate the card if it has not already activated.

you should have internet.

if not then there might be a more complicated problem, but we can help with that.

sam

---

### Post by jguz on 2005-11-01
Hello, 
I have a relate problem with an iBook dual USB G3 (5ooMhz 196MB RAM). I've got a non-extreme airport card in it, but it is not getting recognised. I know how to set up the network once it does (did it with the ethernet), just can't see the card. I've been digging around and recompiling the kernel is quickly becoming a possibility. Any suggestions?

---


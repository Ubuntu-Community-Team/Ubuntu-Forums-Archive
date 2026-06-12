---
title: "Ubuntu on a Blue &amp; White G3"
date: 2006-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ade234uk on 2006-01-18
My brother is moaning about the speed of OSX on his old Blue & White, so I decided to install OS9 again and guess what the Wireless adaptor does not work and no matter what I do it will never work in OS9.

I need to know what Wireless adaptor (PCI slot) works with Ubuntu on Mac. Its the only solution I have left. 

Apart from that I cannot see any other issues installing. The blue and white has 640mb of Ram.

---

### Post by disabled_20220313 on 2006-01-18
If your using Apple's Airport card then you should be OK. 

Otherwise these lists should help.

Ubuntu's own hardware compaitabilty list - [Ubuntu Hardare]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

Ndiswrappers list - incase you need it, hopefully your card will be in the above list. [Ndiswrapper List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

I'd also suggest downloading the live CD, that'd give you a good indication of what would work and what wouldn't.

---

### Post by wandesure on 2006-01-18
can u help with a matterial to study unbuntu

---

### Post by wandesure on 2006-01-18
I'm just starting from scratch, I don't have the stuff the OS has been burnt ,but i'm confused.

---

### Post by ade234uk on 2006-01-19
[QUOTE=ciaran.mooney]If your using Apple's Airport card then you should be OK. 

Otherwise these lists should help.

Ubuntu's own hardware compaitabilty list - [Ubuntu Hardare]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

Ndiswrappers list - incase you need it, hopefully your card will be in the above list. [Ndiswrapper List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

I'd also suggest downloading the live CD, that'd give you a good indication of what would work and what wouldn't.[/QUOTE]

I looked in the list and my card is there. The card is a Belkin fd57000 pci slot. I have downloaded the zip file for it.
See I thought these .inf files would not work on a mac due to the machine being PPC. If I can get this working this will be such a bonus. My brother will now get acceptable performance and hell if he misses the OSX looks I can just use an OSX theme for gnome.

I will let you know how I get on. 
Its a sad situation when you cant find anything that supports your card in os9 and it costs you money.

---

### Post by Rxke on 2006-01-19
I use a B&W as my main machine, and I just want to warn you: Gnome ain't a racehorse either on this old babe...

---

### Post by ade234uk on 2006-01-19
Ok agreed it aint a racehorse but its better than OSX and will keep my brother happy.

I tryed to search ndis in Ubuntu and I cant seem to find it in the packages? does the ndis wrapper come with the mac version?

---

### Post by beansbbq on 2006-01-25
[QUOTE=Rxke]I use a B&W as my main machine, and I just want to warn you: Gnome ain't a racehorse either on this old babe...[/QUOTE]


Agreed.  I have my B&W maxed out with a 1GB of ram, and it still a little sluggish at times.  I do enjoy keeping this machine around however.

---

### Post by Rxke on 2006-01-25
[QUOTE=ade234uk]I tryed to search ndis in Ubuntu and I cant seem to find it in the packages? does the ndis wrapper come with the mac version?[/QUOTE]

I thought ndiswrapper was an x86 thing, no? :(

---

### Post by sulobanks on 2006-01-25
You won't be able to use ndis wrapper in ppc linux.  You need to find out what chipset is in your wireless card and then find a driver for that chipset.  Unfortunately, I think that might be a broadcom chip.  If so, you may have to wait and try it when Dapper Drake comes out, unless you want to be adventurous and try the development version now.

---


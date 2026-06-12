---
title: "Ubuntu 64bit installation on Core 2 Duo &amp; Asus P5B"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by magnus07 on 2007-04-01
I have tried to install various versions of Ubuntu (all 6.10) on a Core 2 Duo & P5B motherboard.
Results have been very similar to those described in the link attached.
[http://www.win.tue.nl/~aeb/linux/misc/ubuntu_on_core2duo.html](http://www.win.tue.nl/~aeb/linux/misc/ubuntu_on_core2duo.html)
I'd like to know if there is something else and if the community is aware of this.
Thanks

PS: bottom line is that I'll switch to another motherboard and resell P5B to some win-fan

---

### Post by Concrete on 2007-04-01
I have the some problem....

I have Asus P5B32-e SLi and E6600 Intel 2.4ghz and can'ot install Ubuntu x64 :(

---

### Post by nsteussy on 2007-04-02
Guys,

I've got Feisty x86_64 running on the Asus p5b with 4 gb of ram.  It was interesting.

1. first off, I absolutely needed to add "blacklist intel_agp" to /etc/modprobe.d/blacklist.

2. I had to go with feisty as the ethernet on the motherboard would not work with edgy.  This varied with the BIOS setting for accessing more than 3 gb of memory.

3. I have an IDE hard drive as the main boot drive with Windows, and a SATA drive as a second, Linux drive.  This likely makes a difference with my experience.

duke out

---

### Post by wparsons on 2007-04-11
I just finished installing Kubuntu 6.10 x64 on this system and my only issue is the lack of a network driver(onboard LAN)..

Specs:

P5B-E
Core2duo 2.4ghz
2gb OCZ 800mhz
Seagate SATAII 320gb
ATI x1650 PCI-E.

---

### Post by engrpiman on 2007-04-13
Hi,

I installed Ubuntu 6.10 x64 on the p5b-e and i had to install the LAN drivers.

just insert the driver disk that came with the motherboard and  then install them.


i copied my driver folder to the desktop: 


cd /home/(user name)/Desktop/(driver folder name)/
sudo make install
sudo modprobe atl1

---

### Post by dabl on 2007-04-13
My Core 2 Extreme runs Feisty great on an Intel D975XBX motherboard.  It cost a little more, but being a Linux noob I decided to minimize the problem-solving part of it.

---

### Post by ruiruas on 2007-06-07
I'm having the same problems with asus p5b, except that I'm trying to install the 7.04 version amd64. The cpu is a intel core2duo e6420. It seems to install, but when it restarts, the system hangs hard.
It&#347; at the point of loading the infamous intel agp driver that shouldn't be loaded anyway (chipset P965) The kernel still recognizes the chipset as G965 instead of the right one P965.

If anyone can help...
Thanks.

---

### Post by scourge on 2007-06-07
I have a P5B and Core 2 Duo E6600, and didn't have to mess with network, agp or sound drivers at all. The only problem was the bug in the 64-bit VESA driver which made the boot splash not work.

---

### Post by mocha on 2007-06-09
> **scourge said:**
> I have a P5B and Core 2 Duo E6600, and didn't have to mess with network, agp or sound drivers at all. The only problem was the bug in the 64-bit VESA driver which made the boot splash not work.

So, you loaded the 64 bit kernel?

I'm in the process of putting together a P5B-E based system and will load Feisty when done.  It seems that there shouldn't be any problems with this motherboard based on other reviews I've read.  I plan to load the 32 bit kernel.

---

### Post by scourge on 2007-06-09
> **mocha said:**
> So, you loaded the 64 bit kernel?

Yes, but I also tried the 32-bit version of Feisty which worked equally well. The only problem I have with this mobo is that I can't seem to get the microphone to work. I haven't tried very hard though.

---

### Post by mocha on 2007-06-10
That's great.  I can't wait to get this machine finished.  Did you have to use the LAN driver on the Asus CD?  What about the onboard audio?  Any problems with it or special means to get it working?

---

### Post by praxis22 on 2007-06-10
This may work:

Install an earlier release (edgy?) and then upgrade.

I actually started on dapper on a AMD64, upgraded to Edgy, and then to Feisty, then I swapped out my motherboard and my CPU, and replaced my Athalon with a Core 2 Duo, It booted first time without issue and everything working.

I was running an Athalon64 3800 in an ASRock 939A8X-M Mobo, now I running an Core 2 Duo 6700 Conroe in an ASRock 775i65G R2.0 Mobo. I can heartily recommend ASRock boards, (an Asus brand) they're cheap, functional and rock solid. 

I've been buying them because I have an  X800XT and I'd have to pay a fair bit of cash even now, to buy a second hand PCI-E card that would give me the same level of performance. It runs Beryl using the Radeon driver, plays Sims2, etc.

---

### Post by scourge on 2007-06-10
> **mocha said:**
> That's great.  I can't wait to get this machine finished.  Did you have to use the LAN driver on the Asus CD?  What about the onboard audio?  Any problems with it or special means to get it working?

I didn't need the driver cd at all. LAN, audio and everything else worked right out of the box. Didn't have to configure anything either. In Windows the cd is needed though.

---

### Post by mocha on 2007-06-10
> **scourge said:**
> I didn't need the driver cd at all. LAN, audio and everything else worked right out of the box. Didn't have to configure anything either. In Windows the cd is needed though.

Awesome.  Hopefully I'll get it all done tonight.  thanks!

---


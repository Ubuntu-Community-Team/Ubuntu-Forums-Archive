---
title: "Low Watt Linux Server?"
date: 2005-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by matinicus61 on 2005-12-26
Greetings:

I am building a solar-powered linux server for my daughter's school's weather
station.  I would (of course) like to use Ubu for it.  I am trying to figure out if I would be better off with an Opteron 140EE chip (socket 940) or and AMD Athlon Mobile 64. 

I would also like to set up hardware raid 5 with a hot swap, But could live with raid 1 plus hot swap if necc.

Anyone have any advice?

TIA!

-Mike

---

### Post by Ribs on 2005-12-26
Check out mini-itx motherboards. Not only are they very small, they have low power requirements. They may not be able to give you all the features you require tho, but it's worth considering.

---

### Post by ninotob on 2005-12-26
I'll second the mini-itx solution.  They're designed specifically for low power (and as a result, low noise) applications.  I'm guessing that the weather station computer just needs to gather data and send it on.  That wouldn't be so much work.  I'm using a mini-itx/ubuntu system as a firewall -- it handles way more data than a weather station would be sending. ;-)

Here're some links:

[http://www.mini-itx.com/](http://www.mini-itx.com/):  Note, look at the Via C3 motherboards as opposed to the celeron models -- some are even fanless.
[http://www.via.com.tw/en/initiatives/spearhead/mini-itx/](http://www.via.com.tw/en/initiatives/spearhead/mini-itx/)
[http://minnow.cc.gatech.edu/squeak/3502](http://minnow.cc.gatech.edu/squeak/3502) (weatherstation built w/ one of the weakest VIA processors).
[http://www.solarpc.com/](http://www.solarpc.com/) (these are based on the VIA C3 too)

---

### Post by pmjdebruijn on 2005-12-26
'I would also like to set up hardware raid 5 with a hot swap, But could live with raid 1 plus hot swap if necc.'

I'd recommend against that, unless you have some really really serious solar power...

Harddrives are 25-35Watts a pop, so your RAID5 setup would cost 75-100Watts, assuming the hot standy doesn't use any power...

So I'd second the MiniITX solution too!! 

Regards,
Pascal de Bruijn

---

### Post by ruudiculus on 2005-12-26
Can't you use some uC-linux (or just your own assembly/C) on a microcontroller? I know they are used for datacollection (I thought Atmel microcontrollers/processors are often used for that. Or else you might find something useful in the Microchip microcontroller families). They're also known to be quite low-power (and they have stand-by/sleep modes). They're also equipped with communication means like SPI, USB, TCP/IP etc. for data storage solutions.

I think when you're designing something this specific there's much to gain when using microcontrollers. (Off course it may take more time ;) )

(You can request free samples from the Microchip site [www.microchip.com](www.microchip.com). Maybe too for the Atmel, but that I don't know for sure)

---

### Post by matinicus61 on 2005-12-26
Thank you very much for the feedback!

I am tentatively looking at AOpen's 37 watt mobo, and possibly Samsung's new SATA 2.5 inch drives.  I am not a huge fan of Samsung drives, but the power req's are good.

Re the ITX, will Ubu install off the CD, or do I need to build a kernel?

I'll be running apache and some php ans mysql.  I'll probably build a small kernel and so would be ok with a medium-powered chip.

-Mike

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
A solar powered weather station? that would indicate it will be outside in a case.. correct? if so, putting a spinning hard drive in that thing is dooming it to failure. When summer arrives a box mounted on a tower, unless it's north of the arctic circle, might reach 140 degrees or more WITHOUT the added heat of hard drive motors. If you're near some place like tucson, az you could add another forty degrees to that.. ouch.

Have you considered flash? You can get a 1GB flash drive now for about sixty bucks.

---

### Post by ninotob on 2005-12-26
Install the 386 version from the install distros.  I've never had to do anything special to get linux to install on my mini-itx system -- it's had RedHat, Fedora, and Ubuntu on it.  Maybe suse too but I can't be certain.  It's run knoppix and DSL live distros as well.  You wouldn't have to do squat but feed it a disk and say "install".

---

### Post by matinicus61 on 2005-12-27
It will be out of the elements - inside or in a well-built shed.  I will keep it cool in the Winter.

---

### Post by matinicus61 on 2005-12-27
[QUOTE=ninotob]Install the 386 version from the install distros.  I've never had to do anything special to get linux to install on my mini-itx system -- it's had RedHat, Fedora, and Ubuntu on it.  Maybe suse too but I can't be certain.  It's run knoppix and DSL live distros as well.  You wouldn't have to do squat but feed it a disk and say "install".[/QUOTE]


That's pretty compelling.  I just assumed I would need to compile an itx-friendly kernel.  I will look more closely at this option...

---


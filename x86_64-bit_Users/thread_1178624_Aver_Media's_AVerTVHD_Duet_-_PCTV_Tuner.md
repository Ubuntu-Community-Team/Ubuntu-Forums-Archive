---
title: "Aver Media's AVerTVHD Duet - PCTV Tuner"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by sylva on 2009-06-04
Hi all.

The AVerTVHD Duet - PCTV Tuner card (also available at Newegg) is a relatively new, well quoted, addition to AverMedia's products, but it has no Linux drivers. I am running Ubuntu 7.1 Server 64 bit Edition and I wonder whether the editions above this one (8.04 - 9.04) have some generic drivers that will run this card. 

Anyone know?

Thank you all, Sylva.

PS: [COLOR="Red"]Please, if possible, email me to [email]jtsylvanis@juno.com[/email][/COLOR]

---

### Post by rlogan on 2009-06-05
Hi

I am no expert on this but have just installed a DVB device in the last week which was using the AF9015 chipset which is not supported out of the box with Jaunty 64bit. Not sure what chipset you have in your device, but this may help ?

I had to download the firmware for the chipset for my device and install it. See [http://ubuntuforums.org/archive/index.php/t-606487.html](http://ubuntuforums.org/archive/index.php/t-606487.html)

Then installed the v4l-dvb and checked with :-

dmesg | grep dvb

See this at [http://ubuntuforums.org/showthread.php?t=1082866](http://ubuntuforums.org/showthread.php?t=1082866)

I am using Me-TV for TV viewing and recording , Version 0.8.14 is fine, the 0.9 version has a couple of issues. If you do use 0.9 you need to do some editing of the config file. See the Launchpad site for Me-TV.

Hope this helps in some way and wish I could be more precise

Cheers

Richard

---

### Post by sylva on 2009-06-05
Thank you, Richard!

I don't have the card yet. I am only prospecting, and a Google search could not find the chip set that's on the card. I may find it later somehow. I only have XP pro SP3, XP Pro 64 SP2 and Ubuntu 7.1 and have absolutely no intention to buy any media software that exceeds the price of the card. In fact, I tossed my TV years ago considering that I had many more useful things to do. Take that from an American, who is part of a notoriously avid nation of TV watchers. I thought getting a card because my 22 inch monitor is very good, getting a much clearer image than any TV monitor. Colors are completely gorgeous. But this is all beside the point, which is, I want to receive over the air broadcasts just for the heck of it. Some concerts and theater from PBS, but not sports or American Idol :) I can get the card for $66 dollars (shipping included). If any Linux variety would drive this card, well, that would be fair deal. Anyway, enjoy your new found HD video and thanks again for your suggestions.

Cheers, John.

---

### Post by sylva on 2009-06-05
Richard, apparently it's an ATI chip, but which one I could not tell. 

Will search further.

John.

---


---
title: "boot performance degrade"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by Alexbit on 2009-05-09
Hi all,

I'm runnig Ubuntu 9.04 x64 on my laptop (a Fujitsu Amilo Pro).
During the last few days I've done some optimization found over internet but today, when I've take look to some bootchart, I've noticed that boot performance are quite strange...

Cause I'm not a pro user, I've attach two png to better explain my question.

I hope that some one can understand where's the problem and help me to increase boot performance (and pc performance too).
Thank you in advance.
Ale

---

### Post by pixel :-) on 2009-05-09
I see a big hole in disk activity, around 10seconds, when he activates alsa?(sound) if i interpret it correctly. Apparently he stops and tryies something, then a timer passes and gives up.

post as an attachment, don't post it as a message, to big

/var/log/dmesg

have a look, you may recognize on what he get stock on.

begining of mine, the [] on the left is time

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested).....

---

### Post by Yellow Pasque on 2009-05-10
> post as an attachment, don't post it as a message, to big
Use a pastebin for that kind of thing.

---

### Post by Alexbit on 2009-05-10
> **pixel :-) said:**
> I see a big hole in disk activity, around 10seconds, when he activates alsa?(sound) if i interpret it correctly. Apparently he stops and tryies something, then a timer passes and gives up.

post as an attachment, don't post it as a message, to big

/var/log/dmesg

have a look, you may recognize on what he get stock on.

begining of mine, the [] on the left is time

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested).....

Yes, the big hole is the thing i'm talking about.
In the attachement you can find dmseg file.
Hope that help!

---

### Post by pixel :-) on 2009-05-10
......
[    8.635995] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.636180] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.669968] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.663386] lp: driver loaded but no devices found
.......

here's the problem, i was correct earlier, the problem is while he setup the driver for the sound chipset(ALC883 with driver alsa), it probes from bios for 8 seconds. You still have sound right?

Revert back to default on sound or the thing called "alsa". I can't help you further.

If you can't still fix it:This isn't a 64 bit issue, go here (with dmesg)

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

You'll find more knowledgeable peopol to help you, and further tweak your laptop.

---

### Post by Yellow Pasque on 2009-05-10
To prevent the auto-probe, manually specify the model in /etc/modprobe.d/alsa-base.conf
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add/modify the line that says the following where <modelname> is one from the list below:
```
options snd-hda-intel model=<modelname>
```
You may have to experiment to find the one(s) that work for your hardware.
```
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  lenovo-sky	Lenovo Sky
	  haier-w66	Haier W66
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  clevo-m720	Clevo M720 laptop series
	  fujitsu-pi2515 Fujitsu AMILO Pi2515
	  3stack-6ch-intel Intel DG33* boards
	  auto		auto-config reading BIOS (default)
```

---


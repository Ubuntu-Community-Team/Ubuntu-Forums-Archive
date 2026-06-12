---
title: "Amd 64 X2"
date: 2008-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ketzerei on 2008-03-14
Okay, well, I have two questions. The first of being, when I boot up my computer, the normal BIOS screen flashes up for a few seconds, and it beeps and a message comes up saying "processor unrecognized." Now, my question is is there a way to get the BIOS to recognize it? Will this hiccup have any affect on installing 64-bit *buntu? And finally, if its amd 64 does that mean I should run a 64-bit os? Thankee.

---

### Post by Kilz on 2008-03-14
> **ketzerei said:**
> Okay, well, I have two questions. The first of being, when I boot up my computer, the normal BIOS screen flashes up for a few seconds, and it beeps and a message comes up saying "processor unrecognized." Now, my question is is there a way to get the BIOS to recognize it? Will this hiccup have any affect on installing 64-bit *buntu? And finally, if its amd 64 does that mean I should run a 64-bit os? Thankee.

Im not positive, but if the bios isn't seeing the chip, thats a big problem. Did you recently upgrade the processor?
Second, if you have a 64bit processor I recommend the amd64 version so you get all the performance you paid for.

---

### Post by ketzerei on 2008-03-14
Yes. I went from an AMD Sempron 3200+ to a AMD Athlon 64 X2 6400 3.2Ghz 2mb cache 125w. Supposedly the guys at the local store said that I shouldn't have any problems.

---

### Post by Kilz on 2008-03-14
> **ketzerei said:**
> Yes. I went from an AMD Sempron 3200+ to a AMD Athlon 64 X2 6400 3.2Ghz 2mb cache 125w. Supposedly the guys at the local store said that I shouldn't have any problems.

It shouldnt affect anything if the computer starts and runs ok. You might want to look to see if there is a bios upgrade for your computer. But be careful, flashing the bios is tricky and if done wrong can leave you with a computer that wont run.

---

### Post by Red Shift on 2008-03-14
Does the motherboard support socket AM2?

---

### Post by ketzerei on 2008-03-15
> **Red Shift said:**
> Does the motherboard support socket AM2?

Yes.

---

### Post by Jiffyman on 2008-03-15
Could it be possible that it's not a genuine chip? Just an I Idea, but I highly doubt it. Has anyone even made a rip-off version?

---

### Post by Kilz on 2008-03-15
> **ketzerei said:**
> Yes.

Dose this error pop up and then go away,  and the computer starts up and runs normally? Secondly, what chip does the bios says is installed

---

### Post by dogson on 2008-03-15
Put the old CPU back, upgrade the BIOS and it will probably work just fine.

---

### Post by utUtu on 2008-03-15
> **ketzerei said:**
> Yes.

Instead of us shooting wildly, it would help very much if you post your computer specs - motherboard make, model, version, etc..

---

### Post by ketzerei on 2008-03-15
Okay, here's my specs:
  Motherboard: MSI K9N Neo F (the first one, not the V3 or whatever) with S/N: 601-7260-010k066024667 with the NVIDIA nFORCE 550 chipset, socket AM2, ver 1.0
  Processor: AMD Athlon X2 6400+ 3.2Ghz 2mb cache 90nm 125w

The error that pops up says something like: "Processor not recognized by BIOS" or something, but it detects the 2 cores and everything, so it knows that there is a processor there, but not a specific make/model. And for some reason, my MB always looks for a floppy when I boot, so I get an "A: Drive error" message and it says press F1 to continue, but thats it. Nothing more about the processor. Just a beep, a message headlined by asteriks, and then it boots. What more information do you need?

---

### Post by Yellow Pasque on 2008-03-15
ketzerei, the 6400 is a newer processor, and your system will most likely need a BIOS upgrade to correctly recognize it. As mentioned, the best way to do this would be to put the old CPU back in if you still have it.

As for the A: error, you probably have the BIOS set to look for a 3.5" drive. The setting is usually on the first option screen in AMI BIOS's.

EDIT: I'm not sure where you could get a BIOS update for this board. MSI doesn't offer the download separately, as they want you to use their LiveUpdate/Windows utility. I would contact MSI and tell them you need a BIOS file for the Rev 1.0 PCB K9N-Neo.
[http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=255](http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=255)

---

### Post by utUtu on 2008-03-15
> **ketzerei said:**
> Okay, here's my specs:
  Motherboard: MSI K9N Neo F (the first one, not the V3 or whatever) with S/N: 601-7260-010k066024667 with the NVIDIA nFORCE 550 chipset, socket AM2, ver 1.0
  Processor: AMD Athlon X2 6400+ 3.2Ghz 2mb cache 90nm 125w

The error that pops up says something like: "Processor not recognized by BIOS" or something, but it detects the 2 cores and everything, so it knows that there is a processor there, but not a specific make/model. And for some reason, my MB always looks for a floppy when I boot, so I get an "A: Drive error" message and it says press F1 to continue, but thats it. Nothing more about the processor. Just a beep, a message headlined by asteriks, and then it boots. What more information do you need?

I checked the MSI web site, and you are out of luck.  Your chip is not supported.

```
Athlon 64x2(Windsor, FSB200, L2 Cache 2x1M)
Athlon 64 x2 5200+ (F3, 65W) 	200 	13 	SINCE 1.9
Athlon 64 x2 5200+ (F3, 89W) 	200 	13 	SINCE 1.9
Athlon 64 x2 5600+ (F3, 89W) 	200 	14 	SINCE 1.9
Athlon 64 x2 6000+ (F3, 125W) 	200 	15 	NO
Athlon 64 x2 6000+ (F3, 89W) 	200 	15 	SINCE 1.9
Athlon 64 x2 6400+ (F3, 125W) sample 	200 	16 	

```

Here is the link

[http://global.msi.com.tw/index.php?func=prodcpusupport&prod_no=255&maincat_no=1&cat2_no=&cat3_no=#menu](http://global.msi.com.tw/index.php?func=prodcpusupport&prod_no=255&maincat_no=1&cat2_no=&cat3_no=#menu)

---

### Post by fjgaude on 2008-03-15
You can likely bring it back and get a CPU that works in your BIOS.

---


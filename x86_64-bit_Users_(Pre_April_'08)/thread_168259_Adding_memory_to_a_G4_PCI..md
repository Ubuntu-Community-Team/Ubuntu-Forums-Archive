---
title: "Adding memory to a G4 PCI."
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by jono.carnie on 2006-04-30
Hi All,

I've just added new memory to my G4 (PCI graphics) machine, two sticks of 256mb pc133.
It's showing up incorrectly as two sticks of 128mb

I remember reading somewhere about a firmware upgrade that may fix this, but can't seem to find this info??

Can someone 1) tell me if this is true?   2) point me in the direction of the firmware suitable for a G4 PCI graphics??

All the links I've managed to google so far, [this  ]("http://docs.info.apple.com/article.html?artnum=120171#English")and  [this]("http://docs.info.apple.com/article.html?artnum=86117") 

Seem to suggest I don't need an update...  it's very confusing...

The reported boot rom version is;
Apple PowerMac 1,2 1.2f2 built on 08/19/99 at 21:36:38

Any help would be most appreciated.

Jono

---

### Post by ssam on 2006-04-30
there is no mention on [http://www.lowendmac.com/ppc/g4.shtml](http://www.lowendmac.com/ppc/g4.shtml) . you sure the memory sticks are as big as they are meant to be?
how much other ram do you have?

---

### Post by jono.carnie on 2006-04-30
[QUOTE=ssam]there is no mention on [http://www.lowendmac.com/ppc/g4.shtml](http://www.lowendmac.com/ppc/g4.shtml) . you sure the memory sticks are as big as they are meant to be?
how much other ram do you have?[/QUOTE]

I've 2 X 256MB 1X 128MB 1X 64MB.

The 256 and 128 are both PC133, the 64 is PC100.

I've swapped the ram around but still only giving me a max of 448.

I had the 128 and 64 before, and I didn't specifiy the 256's were for a mac when i got them.

Looks like I've bummed out with this buy....

Oh well, just have to live with it. I guess.

JC

---

### Post by ssam on 2006-04-30
if you just put the 2x 256s in what do you get?

---

### Post by patC on 2006-04-30
from my understanding there is no difference between pc and mac ram. but if you have pc100 and pc133 on your mac it will only read all of them as the slowest. check this site out

href=http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G4/PowerMacG4/4Expansion/chapter_5_section_2.html

---

### Post by davygravy on 2006-04-30
[QUOTE=jono.carnie]...

I've swapped the ram around but still only giving me a max of 448.

I had the 128 and 64 before, and I didn't specifiy the 256's were for a mac when i got them.

Looks like I've bummed out with this buy....

Oh well, just have to live with it. I guess.

JC[/QUOTE]
jono,

You might **just maybe** have a fix for that problem.  Do you have a copy of OS 9? If so, you can use this program [Dimm First Aid]("http://www.macupdate.com/info.php/id/5714") and correctly repair the settings on these DIMMS.  I had to use it just once, and it worked.  On one of my Mac I had a DIMM that was acting funky - and it did not report correctly and I had some crashing.  I ran this, it said there was some sort of problem, but it fixed it.  After that it reported correctly and I had no more crashes.  This was years and years back...

Don't know if your DIMMS have the same problem mine had...but it might be worth a try.

The program only runs in OS 9, I'm sorry to say.  Good luck.

---

### Post by jono.carnie on 2006-05-01
[QUOTE=ssam]if you just put the 2x 256s in what do you get?[/QUOTE]


I get two slots showing 128mb apiece.

I've tried swapping the order around, ie a 64mb, then 128, then two 256's.
All sorts of combinations... it's almost like the chips ARE 128's.

But they couldn't be.. they're labeled 256mb!!??
Alas I've no way to verify them.

I"m going to give my local mac shop a call and see if they're able to help/test the chips.

Thanks anyway.
JC

---

### Post by jdp on 2006-05-09
How many chips are on the DIMMs?  Just 8 on one side? Or maybe just 4?  That may mean that they are high density RAM, and the G4 may not be able to address them.  If that is so, then you'll need low density DIMMs that use 16 chips (8 per side) for 256MB.  If they are 4 chip 256MB DIMMs, you may need to find some that have 8 chipsper side for 128MB per side.

---

### Post by Mukke on 2006-05-10
don't u need to have pairs of ram sticks ?
i know my old G3 had problems with that

---

### Post by jdp on 2006-05-10
[This Apple TechNote](http://docs.info.apple.com/article.html?artnum=58425) says that the Yikes! G4 (PCI graphics) supports 64Mbit and 128Mbit DRAMs with up to 16 DRAMs per DIMM.  The top size is also 256MB per DIMM.  Thus, unless your DIMMs are 16x128Mbit setups, then it will only recognize the first 128Mbit of each DRAM, multiplied by how many chips there are.  So, if you have an 8x256Mbit DIMM, which would be 256MB on one DIMM with 8chips on one side, and it would only be seen as 128MB.  To get 256MB DIMMs to work, they **must** be 16 chip DIMMs.

Also, no pairs are needed, nor do they help performance, as on older Power Macs.

---


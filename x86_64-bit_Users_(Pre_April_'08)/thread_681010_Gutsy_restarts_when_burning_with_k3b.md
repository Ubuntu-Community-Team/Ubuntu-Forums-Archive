---
title: "Gutsy restarts when burning with k3b"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by purefan on 2008-01-28
Hello all :)

Here is a problem I get when burning any dvd/cd with k3b or any other burning tool under ubuntu. I believe it is a problem with my hardware directly because it happens under windows as well but maybe you guys can help me figure it out.

Here is my hardware specs:
- Processor AMD Athlon 64 X2 6400+
- ATI Nvidia Radeon x1600 512MB
- 4x 1GB Corsair DDR2 RAM
- MSI motherboard k9 Platinum
- Had the Fatal1ty sound card but since its not supported just unplug it 

Using Ubuntu Gutsy Gibbon x86-64 Alternate

Scenario: 
[LIST=1]
[*]Start K3b
[*]Choose DVD Data project
[*]Drag some files/folders (tried with files smaller than 2GB and with over 2GBs, makes no difference)
[*]Choose to Burn and set the speed to 6x (device allows 16x but thought it might be the high speed requiring more voltage from the power supply)
[*]Start burning and logger window says its all good
[/LIST]

Sometimes it reaches 30% and then just restarts, no message at all is like if I pressed the restart button (which of course I didnt...), sometimes its just at the first 1%, others its just random between those two...

Any help please....

---

### Post by crjackson on 2008-01-28
> **purefan said:**
> Hello all :)

Here is a problem I get when burning any dvd/cd with k3b or any other burning tool under ubuntu. I believe it is a problem with my hardware directly because it happens under windows as well but maybe you guys can help me figure it out.

Here is my hardware specs:
- Processor AMD Athlon 64 X2 6400+
- ATI Nvidia Radeon x1600 512MB
- 4x 1GB Corsair DDR2 RAM
- MSI motherboard k9 Platinum
- Had the Fatal1ty sound card but since its not supported just unplug it 

Using Ubuntu Gutsy Gibbon x86-64 Alternate

Scenario: 
[LIST=1]
[*]Start K3b
[*]Choose DVD Data project
[*]Drag some files/folders (tried with files smaller than 2GB and with over 2GBs, makes no difference)
[*]Choose to Burn and set the speed to 6x (device allows 16x but thought it might be the high speed requiring more voltage from the power supply)
[*]Start burning and logger window says its all good
[/LIST]

Sometimes it reaches 30% and then just restarts, no message at all is like if I pressed the restart button (which of course I didnt...), sometimes its just at the first 1%, others its just random between those two...

Any help please....

Yes it's a hardware problem no doubt for me.  What are the specs. on you PSU?

Does it have any problems when reading a DVD or CD for an extended period?

I would look at:

1. PSU
2. MEMTEST you memory
3. Bad cable
4. Faulty drive or drive jumpers not configured correctly

---

### Post by purefan on 2008-02-07
Hi! Thanks,

Yeah I finally ran the test long enough... well had it for 40 minutes the memtest and here is what it showed at that point:
Memtest86 v1.70
Pass: 17%
Test:6%
Test #7 [Random Number Sequence]
Settings: RAM 400Mhz DDR800 / CAS 5-6-5-18 / DDR-2 128 bits

One thing I noticed is that "ECC OFF" on the chipset description, dont know if thats any relevant...

As for the UPS its a RexPower PX-450

For a while I thought it was some 64 library that updated my k3b but with a fresh install its still doing the same thing.

Now, having 4xGbs dimms in Ram and 2x160 Gbs SATA drives with 1 dvd-burner and 1 DVD-Rom and a Radeon x1600 attached, could it be the UPS not powerful enough for the hardware?? should I get a more powerful one??

thanks a bunch!

---

### Post by crjackson on 2008-02-07
> **purefan said:**
> Hi! Thanks,

Yeah I finally ran the test long enough... well had it for 40 minutes the memtest and here is what it showed at that point:
Memtest86 v1.70
Pass: 17%
Test:6%
Test #7 [Random Number Sequence]
Settings: RAM 400Mhz DDR800 / CAS 5-6-5-18 / DDR-2 128 bits

One thing I noticed is that "ECC OFF" on the chipset description, dont know if thats any relevant...

As for the UPS its a RexPower PX-450

For a while I thought it was some 64 library that updated my k3b but with a fresh install its still doing the same thing.

Now, having 4xGbs dimms in Ram and 2x160 Gbs SATA drives with 1 dvd-burner and 1 DVD-Rom and a Radeon x1600 attached, could it be the UPS not powerful enough for the hardware?? should I get a more powerful one??

thanks a bunch!

You keep referring to your UPS - Uninterruptable Power Supply (battery backup system), but that would have NOTHING TO DO WITH IT.

If however, you are talking about you PSU - Power Supply Unit then yes, look at number 1 on the list I provided in the previous post.  It was my #1 suspect.

---

### Post by purefan on 2008-02-07
yeah sorry about that, I did mean PSU and not UPS, my bad.

Thanks mate! will replace asap and post back :guitar:

---


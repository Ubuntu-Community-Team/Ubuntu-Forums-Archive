---
title: "Problems with trying to install Ubuntu 8.10 on AMD64"
date: 2009-03-09
forum: x86 64-bit Users
---

### Post by Ulysses on 2009-03-09
Hello

Biostar K8M800 Micro AM2 motherboard
AMD64 X2 4200+ Processor, 2.20 GHz, 1MB cache, Dual Core
2 x 1GB DDR2 RAM
HDD = 360GB Seagate Barracuda IDE

Live CD with HDD not plugged in, OK (that's what I'm doing now. And I am very tired doing this because I've been at it all night)

Live CD with HDD plugged into IDE1, Not OK
Error is as follows (as best as I could copy it down)
```

initramfs
ata4.00.exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata4.00 cmd c8/00:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
ata4.00 : status {DRDY}
```

And then it just hangs until I restart

I gathered that maybe it does not like my IDE HDD and before I go out and buy a SATA HDD I would like it confirmed for me that
[a] I can't work a fix around the existing HDD before I 
[b] go out and spend money on a new SATA HDD

Is there anyone at all who can help me out, please?

And, was 64bit AMD a good idea or was it a bit hasty for a newbie with too much guts and not enough money and brains (that's why the new computer - I played with and fried the old one ; really don't want to fry this one, please)

Thanks, folks.
I know I ask for alot of beans, but the coffee is so darned good
And, for the record, my daughter's nickname is Beans - partially because I would play with installing Ubuntu when she was first born.

RAR

---

### Post by cariboo on 2009-03-10
Is the drive detected properly in the bios, and is there an emulation mode  setting in the BIOS?

I've been using 64bit versions since dapper, never had any problems installing.

Jim

---

### Post by Yellow Pasque on 2009-03-10
Yes, check BIOS settings. Make sure your BIOS release is dated at least 1-08-09. If not, upgrade it: [http://www.biostar.com.tw/app/en-us/mb/bios.php?S_ID=141](http://www.biostar.com.tw/app/en-us/mb/bios.php?S_ID=141)

---

### Post by norwoods on 2009-03-10
if the drives (HDD and CDROM) are on the same cable, is one jumpered for master and one for slave?
if the drives are on different cables, are they both jumpered for master?

---

### Post by joeandrews0826 on 2009-03-10
Had a similar issue, try adding "nohpet" to your kernel options from grub.

Joe

---

### Post by Ulysses on 2009-03-11
Hello,

Wow. This is awesome. Thanks. I wish I could have got to these responses earlier, but there are simply not enough hours in the day and the time change always takes the wind out of my sails in the first week.

Anyway. Here goes.

> Had a similar issue, try adding "nohpet" to your kernel options from grub.

Joe 

I am too much of a newbie to know how to do that.
I would have to search the community for instructions on how to do that. I'll put it last on my list, I'm afraid.
Thanks, though. I have to start to learn to dig deeper on Linux and not just try to look cool to all of my friends and tell them that I use it.

> if the drives (HDD and CDROM) are on the same cable, is one jumpered for master and one for slave?
if the drives are on different cables, are they both jumpered for master? 

Nope. I put them on seperate cables because I have 2 IDE ports on the motherboard.
Though, I never considered putting them all on one cable and setting the jumpers to cable select.
I can do that and see what happens. Very Cool. Thanks. I'll try that.

> Yes, check BIOS settings. Make sure your BIOS release is dated at least 1-08-09. If not, upgrade it: [http://www.biostar.com.tw/app/en-us/...s.php?S_ID=141](http://www.biostar.com.tw/app/en-us/...s.php?S_ID=141) 

I checked the BIOS and tried to update it and, while the BIOS update was 01/08/09, it wouldn't let me. Kept on telling me that there was a floppy disk failure and to press ESC to go back or F10 to restart.
Does anyone know of anyway to get around that?
I have the floppy disk shut off ; it should not be looking for it.

> Is the drive detected properly in the bios, and is there an emulation mode setting in the BIOS?
I've been using 64bit versions since dapper, never had any problems installing.

BIOS sees the drive as the master in that IDE section. It sees it for what it is.
I sifted through the BIOS and could not find anything that looked like an emulation mode for anything.
Could you point me in the right direction?

I know it seems like alot, but I kid you not when I say 'newbie'.

My other alternative today was to
[01] Try and hook them all up on a single IDE cable and make sure the jumpers are set to cable select and see if that works
[02] If that doesn't work, buy a SATA HDD and try and see if it works
[03] Try and see if I can copy from my IDE to the SATA so my data will be intact
[04] If that doesn't work, buy a HDD enclosure and hook it up by USB and see if it can transfer that way
[05] If the IDE HDD doesn't work through the HDD enclosure, then build a system from scrap for the express purpose of transferring 360GB of data using SSH
[06] If none of that works, go to the post office, stock up on stamps, go to Business Depot and buy lots of pens and paper, and the buy a calculator or maybe an abacus and go live in the woods and off of the fat of the land, because technology, by step [05] will have completely failed me.

Thanks a tonne for the suggestions, though.
If anyone has any more of them, I would certainly appreciate hearing them.

---


---
title: "drive issues."
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by erniewinner on 2006-04-09
what to do? it seems the beige g3 ata interface is not ata 33 but a slower 16mbs? and the onboard scsi is 5mbs? i have an ide cd rom and will want to use an ide hard drive? ( although i could get a second scsi drive. i have also just picked an ls120... i know i could end up with data corruption or slowing the config down adding the ls120? perhaps the beiges scsi is a waste of time. well all is not lost as i have 2 add in scsi cards a fast siig ap-40 (acard 40mbs) this won't boot after the os installed in os 10.1 or 10.2 "cannot open pci device" yadda yadda. and os 9 doesn't see the card. and i have a aha 2930cu ( 20mbs) i think i've read this isn't bootable in the beige. i don't know if the issue is the mac bios the cards bios and i can't seem to find a bios update on the siig ap-40. i don't know if anyone has got theese cards working? i want to use them under ubuntu. i suppose my 1st choice solution would be... cd/ ls120/ siig ap-40 2 x ultra scsi drive. failing getting those devies working what other cards will be faster than the onboard ata ( both mine are.) bootable and working under ubuntu? anyone using such a config? :-k

---

### Post by jdp on 2006-04-09
You can just pu t a larger IDE drive on the internal IDE and it should work, if it's under 128GB.  Your bootable MacOS partition will probably have to be smaller than 8Gb and be the first on the drive.

---

### Post by erniewinner on 2006-04-09
yeah i guess. i had some issues with the other card i just tried... adaptec aha 2930cu it would have been slightly faster than the onboardstuff what with it's 20mbs an 10,000 rpm as opposed to 16mbs and 7200 rpm at best, but os 9.2.2 says unsupported drive altough it sees the card. i might see what other software could do drive setups job. it doesn't seem to wanna work my way i took out the floppy put in my ata drive with os 9 and bootx (working) i would use os 9 so thats not a waste. i could have put osx on there as well (osx supports the drive but not the card.) i wouldn't use it much but i like the novelty! i then planned on using the scsi drive in the hd bay (i only have one sled.) and to my joy that config was going ok. the ata drive would boot the cd rom os ubuntu install and i came to install it. but although it partitioned the drive and formatted it, when it came to putting the files on it, it just said it couldn't as the "deb was corrupt" well i know there's nothing wrong with the cd as i have installed off it several times and it works with the normal ata setup... but it's got an issue with installing to the scsi drive! i wonder if dapper would be a good bet? but they might have dropped support for that card with my luck. 
i suppose i could use another non apple drive setup like util. any ideas on the names of such a program??? failing that i probably will retire my mac to another room... i originally bought it with the idea that is was a mac so more secure etc. but ubuntu on pc is now a better bet... perhaps i'll stick the scsi drive in my oldest pc, i was wanting to up the drive perfomance in that and it's twice as fast as the g3. i don't think i can justify any expense on the mac because just getting a g3/ g4 would have been cheaper. i think linux gives me what i wanted out of apple.

so...

two last tries for the shear hell of it:

1. use a newer ubuntu and try to install it on the scsi drive with the ata as a bootx partition as os 9 cant use the scsi. (unsupported drive.)

2. use third party software i hope that would work to partition and format the scsi drive so i could put bootx on it... but i ain't got a clue what it may be called. :-k

---


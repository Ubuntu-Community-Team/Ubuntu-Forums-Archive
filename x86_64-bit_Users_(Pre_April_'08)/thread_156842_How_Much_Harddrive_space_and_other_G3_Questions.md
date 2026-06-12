---
title: "How Much Harddrive space and other G3 Questions"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tone on 2006-04-07
I've got an elderly B&W G3 (300 Mhz, 256 MB Ram) that I'm thinking might be a good candidate for Ubuntu. My wife, who is a teacher, still needs access to Mac 9.2 as her school still runs old Macs and she needs to be able to exchange files and run applications like FileMaker. 

However, browser support for 9.2 is drying up and I don't have the Microsoft Office suit, so working on files at home for my work (an XP environment) is a no-go. 

I tried Ubuntu live and the Open Office apps seem to read and write Office-compatible files. Plus, the browser worked great. 

However, before I take the plunge, a couple of questions:

- I've only got a 6 GB harddrive. If I reformat and partition, will I have enough room to dual-boot Mac OS 9.2.2 (plus applications), Ubuntu (plus applications) and still have room for data? How much room do I need in each partition to keep everything running smoothly? Apparently adding a second drive to the early G3s can be a bit of an issue. Do I need a bigger drive to make this work?

- The LiveCD was seemless, but slow. I'm assuming that running from the CD is slower than a harddrive install, but is it much slower or a little slower? Basically, what are the system requirements for a smooth, quick running Ubuntu install?

---

### Post by nkbj on 2006-04-08
I'll try to answer some of your questions from my experience using a beige G3 300 MHz with 576 MB RAM. The CPU is fast enough for normal use (anything but heavy graphics), but more memory is always better.

The live CD is a lot slower than a harddrive install. at least on my system (running from the original 24X cdrom drive).

About your harddrive: That depends on how much space your wife needs for data and how much space you need for data? The base Ubuntu install (including browser and openoffice) is about 2 GB + swap space. One possible partition setup would be:

Mac OS 9.2.2 - 2 GB (system and data)
Ubuntu - 3.5 GB (base install + 1.5 GB for extra programs and data)
swap - 0.5 GB (2 times RAM size)

Can you get by with this? Else you need a bigger harddrive.

Regards,
Niels Kristian

---

### Post by davygravy on 2006-04-08
Cool, I have a "smurf" (B&W), too.

My smurf has the same for RAM, but a cheap 60GB drive w/ a 8MB cache on it (got it as a closeout for about $15 after rebate).  I actually enjoy it a bit more than OS X for somethings, definitely better IMHO than 9.2.  Speed (as a user experiences it) is determined not just by the processor, but by the amount of RAM, the HD speed and responsiveness and network speed.  

It will definitely be faster w/ an actual install on the HD, but the OpenOffice programs take a lot of memory.

The some of the revision 1 B&Ws didn't have slave support, but some did (I have one in my classroom right now that is a rev 1 yet has 3 hard drives in it, but because of the controller chip, it does have slave support).  Adding another hard drive might not necessarily be a foregone conclusion, though its not a sure thing either. 

Will you want to be able to mount the Apple HFS/HFS+ shares while the B&W is running Ubunu?  I did that in a Beige years ago w/ YellowDogLinux, but haven't gotten around to trying it in Ubuntu.

davygravy

---

### Post by nkbj on 2006-04-08
[QUOTE=davygravy]
Will you want to be able to mount the Apple HFS/HFS+ shares while the B&W is running Ubunu?  I did that in a Beige years ago w/ YellowDogLinux, but haven't gotten around to trying it in Ubuntu.
[/QUOTE]

It can be done in Ubuntu too.

Regards,
Niels Kristian

---

### Post by erniewinner on 2006-04-08
as a user of a beige g3 233mhz i envy your 100mhz bus! if you look at the price of hard drives you shouldn't have to struggle with a 6gb drive... i know i could make that work good but then i'd use use another machine for other tasks. get one with a good rpm it'll speed operations up. if you can use slave drives keep this for a backup... or like me you could go scsi... with a "revision a" g3 it's the only option. i got a 9gb compaq drive 10,000 rpm for £5 with postage off ebay! :cool:

---

### Post by jdp on 2006-04-08
The slave issue with Rev A Beige G3s only applies to booting from the slave drive and under OS 9.  For OS X slave drives should work after boot, and I'd imagine that they'd work after boot on Ubuntu too.

---

### Post by erniewinner on 2006-04-08
well thats worth knowing... but i'm not a huge fan of osx. i'd rather ubuntu! (i would have been but apple drop support too quick making the os unuseable on the net from a security point of view. sort of £100 a release, once a year. at least classic has a history and good collection of apps.)
i was thinking the scsi interface is faster than the ata on board udma33? 10,000 is definately a faster drive speed 15,000 faster still. i think a sata interface for mac would be the standard £50 if they exist (too much.) and the beige came with the scsi interface built in. i'm not sure about the b&w... i honestly didn't think a b&w g3 would have slave issues? could point out if he does? he definately wants a big drive... go on treat yourself. [www.ebuyer.com](www.ebuyer.com) (uk) is a good place to buy new gear. and no i don't work for them. :mrgreen:

---


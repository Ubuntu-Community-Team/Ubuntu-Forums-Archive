---
title: "Crashes Using &gt;1GB RAM on New Phenom 9600 (Unable to handle kernel paging request)"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by professorYaffle on 2008-02-13
I'm trying to install gutsy on a newly built phenom 9600 machine: Gigabyte MA790X-DS4 motherboard, 2 sticks of 1GB PC2-6400 Corsair RAM, 300GB Maxtor HD, XFX GeForce 8400 GS (that's just a stop-gap until the 8800GTs come back into stock) plus peripherals.

I started trying to install kubuntu, but that hung part way through the file copying. Basic ubuntu installed okay and worked fine for half an hour or so but died part way through downloading and installing updates. After two or three reboots and picking up the updates where it left off the updates were on but the system still wasn't stable. It's okay to start with, but after a while some processes would crash or hang. Sometimes X would die or the whole system would freeze and need a hard reset.

Initial error messages indicated disk i/o problems so I blanked the entire disk and did a destructive scan for bad blocks - none found. Then I ran memtest86 all day and it found nothing wrong. I installed again from scratch and had pretty much the same problems. I tried it with and without the proprietory nvidia driver - no difference.

Eventually I happened to notice that the crashes started happening just after the system broke through the 1GB memory usage (reported by free/top.) So I took the system down and ran memtest again (20 full passes no errors.) Moreover, I could reproduce the general problem state (although not specific crashes) by running wc on all the files in /usr (which slowly filled up the filesystem cache.)

I took out 1 stick of memory and everything worked okay (can't go over 1GB with only 1GB installed!) Swapped it to just the other stick - still okay. Borrowed 4 sticks of 512M and  as soon as the usage gets over 1GB things start dying again. I've tried running the memory in ganged & unganged mode - no difference.

I flashed the motherboard with the latest bios and tried it with and without the TLB bug workaround - still no effect.

In desperation I installed OpenSuSE10.3 on a separate partition, and got exactly the same symptoms.

Finally I noticed kernel "oops" messages in /var/log (Doh!). Anybody else had this problem or know if there are any kernel options that can be used to avoid it?

A snapshot of the kernel messages is attached (it's over 100 lines.)

---

### Post by zubrug on 2008-02-13
looks like you are having a core 2 error, if you do a search for amd forums & phenom troubleshooting you will find some info regarding this.
Seams some phenoms have a faulty core 2 (third core), recent ones have been better. 
I have a 9500, and have found sidux to be completely stable and fast. Ubuntu partition freezes.

---

### Post by professorYaffle on 2008-02-14
Thanks for the pointers.> **zubrug said:**
> looks like you are having a core 2 error, if you do a search for amd forums & phenom troubleshooting you will find some info regarding this.
Seams some phenoms have a faulty core 2 (third core), recent ones have been better. Mmm - did some googling and that doesn't look very promising, but I'm not convinced it is the problem though. I've grepped through the logs and the faults don't just happen on one specific core. There's quite a selection on CPU2 & 3, some on CPU1 and none that I've seen yet on CPU0.> 
I have a 9500, and have found sidux to be completely stable and fast. Ubuntu partition freezes.What kernel version are you running?
Gutsy is currently using 2.6.22-14.

---

### Post by madrescher on 2008-07-05
Does someone has solved this issue? I'm having a very similar problem which I posted at launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/234085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/234085)

---

### Post by professorYaffle on 2008-07-08
> **madrescher said:**
> Does someone has solved this issue? 
'Fraid I never really got to the bottom of it. I managed to get the system going somewhat more stably (I.e. no definitive 1GB+ RAM kernel oopses, but still some occasional unexplained crashes and complete lockups) after the OS upgraded the kernel a bit (which I assumed was the cause) but after that I couldn't do any serious kernel testing as the OS had crashed whilst doing an upgrade and broken its own databases or something. I could still run the system using a backups but any further upgrades or messing with it just trashed it and had to be recovered from backup again.

Shortly after this the motherboard died completely (just wouldn't power on again.) I RMAd it and got it fixed after a few weeks. I also got some new RAM (2x2GiB) as well just to make sure. Put it all back together again and I was still getting occasional crashes or lockups (maybe once or twice a day.)

Eventually I gave up and bought a P35 motherboard and a Q6700 processor, and did a fresh install of Hardy (which had come out in the mean time) on a shiny new HD ... but still got problems! *Then,* after some serious testing, I realised that the *new* RAM was faulty and RMAd that. (This was really not my lucky build.) So it's possible that the repaired Gigabyte m/b and phenom9600 with a recent kernel would actually have been working fine, but I haven't got the time to take it all apart and rebuild the old version again to test it.

Replaced RAM is now installed and the system has been rock solid ever since. Sorry that this probably isn't much help to you, but good luck getting it sorted anyway.

---

### Post by netguy204 on 2008-07-23
I had a similar problem. I passed the "acpi=off" kernel option to disable acpi and I've been able to use all of my memory since then. I do still have occasional (every few week) crashes. Additionally, the system won't even post if I enable the virtualization instructions.

---


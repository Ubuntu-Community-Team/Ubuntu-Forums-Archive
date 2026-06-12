---
title: "Issues with shutdown, sata, and other general hell"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by craftybones on 2007-05-22
Hello,

I just installed Dapper and did a double upgrade over the net to Feisty. 64 bit.

I have a Gigabyte iDNA motherboard. I am posting the lspci output as well. 

I also have a SATA drive and my boot time takes forever. My issues with SATA have been legendary. I  posted a bug and it was accepted, but no progress has been made(the bug was however filed under kenerl 2.6.17). These issues persist and my Ubuntu experience is just getting worse. If I had all these issues to deal with, I'd have stuck to Debian ;)

Please help me. I am listing all the problems I have so far:

1) SATA acts weird. I am unable to see /dev/sda. There is no partition, but the disk doesn't show up in disk management either. It is a 300 Gb Maxtor I think. I've forgotten what it is.

2) Shutdown doesn't happen. When I shutdown, it shuts down, but the fan is still on and power still stays on even though linux itself shuts down. THe hardware is still up and running

These are primary issues. They are inter related, and I will ABSOLUTELY get down on my knees and say a thousand hail marys if someone were to guide me through this, or point me in the right directions.

Thank you,

Crafty

---

### Post by dabl on 2007-05-22
Is your BIOS version as current as possible?  It sounds like Ubuntu isn't loving that Gigabyte motherboard much.  The detection and operation of hard drives, memory, and the PCI bus are buried pretty deep into the Linux kernel, as I understand it -- I'm too much a noob to have a clue how one would tweak such things.  You don't happen to also have an IDE drive on that motherboard, do you?  Sometimes the IDE/PATA drives and SATA drives don't agree on who gets Grub, especially if Windows is already installed somewhere.  You might try downloading GParted Live CD from Sourceforge, and booting that, to see how well it recognizes your SATA drive.

Two cents' worth, maybe ....

---

### Post by craftybones on 2007-05-22
Yeah I do have an ide drive. 

But yeah, I suppose I can upgrade my BIOS firmware...

Thanks though, its always nice seeing a reply post really quickly.

Thanks,

crafty

---

### Post by shad0w_walker on 2007-05-22
Are you still running the older kernel or the latest fiesty one? It may simply be that some weird issues occur with an older kernel and fiesty.

---

### Post by craftybones on 2007-05-22
moonwolf@trantor:~/Desktop$ uname -r
2.6.20-15-generic


That is what I am currently running.

Thanks.

Jayanth

PS: no its not a kernel specific problem, I think its more hardware related etc.

---

### Post by dabl on 2007-05-22
I'd say these are hardware issues.  One experiment that might shed some light would be to disconnect the IDE drive (just pull the power cable off), and then work with your system as a SATA-only.  If it all of a sudden works great, you'll know there is contention, at some level, between the IDE bus and the SATA bus.  ;)

---

### Post by craftybones on 2007-05-22
I've performed a similar experiment

The linux install is on my IDE. so what I did was, disabled sata in bios, used a PCI sata card, and tried running it, same results,

Not sure if it is an IDE contention. The bug in launchpad was accepted. No work has been done on it, so I don't know what the deal is.

Jayanth

PS: my NTFS partition on SATA was messed up by the linux kernel at some point.

---

### Post by craftybones on 2007-05-22
Stupid question:

the last revision on my bios, according to the site was more than a year
ago. The "description" has nothing to do with SATA improvement etc etc, but
does this still make a difference?

Crafty

---

### Post by dabl on 2007-05-22
Not to be a cynic, but they rarely say "updated to correct my prior screwups" ...

;)

Yes, I'd flash my BIOS with the latest version -- be careful and follow the directions precisely.  No guarantee, but my fingers are crossed -- this could help you.  :D

---

### Post by John Jason Jordan on 2007-05-22
> **craftybones said:**
> Stupid question:
the last revision on my bios, according to the site was more than a year
ago. The "description" has nothing to do with SATA improvement etc etc, but
does this still make a difference?
Crafty
I have an Abit NF-M2S motherboard with SATA II and I had no end of problems with the two Western Digital SATA drives that I put on it and Linux software RAID. Setting up a RAID device with Linux requires constant disk activity for an hour or two, and I couldn't get more than a few minutes into it without suddenly getting a power off. I mean, it was just like I pulled the cable out of the back of the box.

I went to abit-usa and the only BIOS upgrade it showed was version 1.1, which is what I had. After several days of swearing I discovered that the abit-usa site was completely down. So I went to abit.tw instead and guess what? They had a version 1.3 and a version 1.5 BIOS upgrade. It took another couple of days of swearing before I figured out how to flash a BIOS in a computer that has no floppy drive, but once I succeeded in flashing the drive, the problems disappeared. OK, the truth is that the problems are 99% resolved, but just the other day I got a sudden power off again, so I have decided to pull the plug on Abit once and for all. I'm taking the board back to the store and getting an Asus instead.

So I definitely recommend flashing the BIOS to whatever is the latest, and make sure it really is the latest.

---

### Post by craftybones on 2007-05-22
Thanks 3J

Will try.

Crafty

---

### Post by craftybones on 2007-05-22
Darn.

My bios revision is about 7 versions old. Will flash it ASAP and see if it fixes things.

Crafty

---

### Post by craftybones on 2007-07-17
Ok,

So finally got some time to flash my BIOS. Flashed it to the current revision. The upgrade went fine, however, it seems that shutdown is still being a problem. My old 300 Gig Sata is toast, meaning I have to wait till my new drive arrives for me to try, but I am scared. 

Shutdown still doesn't shutdown entirely. I used to get some weird ata revalidation errors, those have vanished, but I suspect that owes a bit to the fact that my SATA actually died and was removed... :)

Can someone please please reply to this topic and have an active thread going? I am not sure, it doesn't seem like anyone else is having such problems. 

Thanks,

crafty

---

### Post by dabl on 2007-07-17
Too bad about that 300GB SATA drive!  :-({|=

The problems that you're having with hard drive shutdowns sound like they might be related to "power management" conflicts between Linux and your BIOS.  If so, you need to look into the acpi boot options, and maybe turn as much of it off as you can stand.  And maybe start turning some of it off in BIOS as well.

Two cents' worth (max ...).  :)

---

### Post by mommebu on 2007-07-18
the kernel option 'reboot=b' might help.
have a look here:

[http://ubuntuforums.org/showthread.php?p=3038421&posted=1#post3038421](http://ubuntuforums.org/showthread.php?p=3038421&posted=1#post3038421)

---

### Post by craftybones on 2007-08-06
I am afraid it didn't. In a sense reboot=b made it worse, before, I used to be able to restart without issues, with reboot=b, even restart is an issue.

I would REALLY like a solution to this issue, and I am SURE it is somehow connected to my SATA as well. I am just so scared putting in any SATA drive in it since my earlier SATA died. But I have no option, I need to store my data and I SO don't want to do Windows.

Crafty

---

### Post by wjp.reg on 2007-08-06
craftybones;

Maybe this thread will be of some help,
[URL="http://forums.whirlpool.net.au/forum-replies-archive.cfm/715456.html"]
Installing ubuntu on SATA drive[/URL]

---

### Post by craftybones on 2007-08-06
Hello,

I just went through the post and I am not sure that might help me much.

It is not that my drive doesn't get recognized, and it is not even that I can't install on it. It just would take eons, one install went on for 5 hours. I am pretty certain its a kernel issue and I even have a bug floating around somewhere.

GRUB virtually has no issues with mounting at all, so that was never a problem.

Currently I am concerned with the fact with the damned thing never shuts down. For some reason the Ubuntu guys accepted a bug on this and are following through with it.

If you are the user who has the Gigabyte K8 motherboard and if I had emailed you earlier, then well, I don't know what to say. If we have the same mobo, similar kernels and did nothing out of the ordinary and shutdown is somehow working for you and not for me, then something is weird yeah? :)

thank you,

crafty

---

### Post by wjp.reg on 2007-08-06
:confused:

---

### Post by nss0000 on 2007-08-08
I believe you have made angry the DKG (Dapper Karma Goddess ), for not worshipping at her command_line.  She is scr*wing with your kit. Cast-off the byte-baiting, rummy v_7.04 , return to the fold (Dx64) and all will be forgiven.

---

### Post by craftybones on 2007-08-09
Umm sorry to disappoint you...Dx64 had the same issues.  In fact, the upgrade happened to make this issue disappear.

Craftybones

---


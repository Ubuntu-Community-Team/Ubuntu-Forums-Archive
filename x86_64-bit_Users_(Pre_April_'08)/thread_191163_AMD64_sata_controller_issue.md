---
title: "AMD64 sata controller issue"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ashridah on 2006-06-07
Hey, 

I've run into a weird problem installing ubuntu64 6.06 on my a8n32-sli-deluxe motherboard.

The liveCD boots up fine, and the install goes fine too, but when the system reboots, it gets to the point of going to mount the root filesystem, and hangs.

Eventually, it drops to the busybox shell, and from what i can tell, it seems to have made no attempt to load the driver for my silicon image scsi controller (Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller). This stuff is all working under 32bit debian, and in windows, so the controller itself is operating properly.

The only hits i've seen for 'Waiting for root filesystem' talks about running evms_activate, but i manually partitioned, and didn't setup any kind of LVM or software RAID, and i'm also not using any hardware raid (ick). at any rate, running evms_activate manually talks about libgcc_s.so.1 being missing, something about pthreads, and then aborts, without doing anything, afaict.

Interestingly, attemting to install sata_sil plus the other scsi drivers doesn't seem to have any effect. modprobe works, they appear in /proc/modules, but the device nodes don't appear, and manually creating /dev/sda5 with mknod doesn't have the appropriate effect either.

it seems like the controller's just refusing to initialize, and i can't work out why.

Another interesting piece of the puzzle. running 'cat /proc/kmsg' prints out a chunk of dmesg's output, but then hangs at some random point, and can't be killed (since there's no job control, no ctrl-c, and since it's blocked in a kernel thread, there's nothing that can be done). Even tail hangs this way, so i can't work out where it's breaking :S

Sorry for the long-windedness, 
anyone got any ideas?

ash

---

### Post by ashridah on 2006-06-07
Okay, as an addendum to this post (after noticing a *lot* of issues that look similar), my problem seems to be in no-way related to any other examples of this. 

My issue seems purely related to the sata_sil driver not loading during bootup, which means that the single SATA drive in my system (aka, no ordering issues) never loads. this means that the initramfs environment simply can't find /dev/sda5, which is where the root filesystem is.

it's weird. it's loading sata_nv, which is another sata controller in my machine, but that device doesn't have any drives attached (and is infact disabled in the BIOS, but no matter), it just doesn't seem to attempt to load sata_sil.

ash

---

### Post by ashridah on 2006-06-07
Sigh, and just to make things more fun. 
I gave up and plugged my single SATA drive into the nforce controller, and now the sodding thing seems to be working okay.

Lord knows how the preexisting windows install is going to cope with this move, since it lives on the same disk hopefully it'll be okay with it. :S
*boggle*

ash

---


---
title: "AM2 - Asus M2NPV-MX Install Status"
date: 2006-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by geek.de.nz on 2006-08-27
I knew cutting egde hardware would pose a problem...

I'm configuring (K)Ubuntu Dapper on my new machine and, at the same time am compiling a howto on the subject.
[http://www.ihostnz.com/ubuntu_dapper_am2](http://www.ihostnz.com/ubuntu_dapper_am2)

I got up to the point where I need/want to compile my own kernel. I've done this before and am comfortable with it. But at the moment there is a problem with my Serial ATA Hard Drive (Seagate 250GB) drivers. I need the Serial ATA driver in the running kernel, so that Suspend2 (hibernate) works. /dev/sda7 (my swap) is not accessible at boot time -> kernel panic.

Does anyone know what kernel parameter has to be set how (make menuconfig)?

However, my LAN and Audio seem to function properly with the NVIDIA drivers, that I installed with a bit of a hassle. 

I'm not complaining and happy that it seems to be working after all.

So, the rest should only be a matter of time. If anyone has the same Motherboard and/or has any ideas, please participate in this thread.

Cheers

---

### Post by Milenko on 2006-08-28
Hey mate,
         Unfortunately I'm not going to be able to help you as I'm real new to Linux! Sorry, wish i could.  The reason I'm posting is because you seem to be the first person who has similar hardware.  I have an AMD64 dual core CPU and an ASUS M2N-MX Deluxe mobo.  I have 2 SATA drives (RAID-0).  I have a question if that's ok as you sound like you know what you're doing!

Running/installing Linux without boot parameters freezes every time.  I'm assuming from the messages of kernel not time syncing this is due to Dual core.  From doing some reading i see certain boot parameters that can be entered to get past this.

"irqpoll pci=noacpi noapic nolapic acpi=off"

I get all the way through then (Live CD) Due to this I can not see my wireless card which should work "out the box" .  Would you a) be able to tell me which boot parameters i should be using and b) how i go about doing device configuration.

Thanks alot mate, look forward to hearing from you!

Milenko

---

### Post by geek.de.nz on 2006-08-28
It seems to work "better" with 'noapic acpi=off'. My own kernel at least gets to the point of a panic. But I'm not sure why. When I boot a generic kernel, I see a message flashing that my bios has a bug. However, I installed the newest available bios version. Anyway, this doesn't surprise me, since I had a problem installing the acpi driver under windows xp as well. The new (windows) version of the driver fixed this problem.

Do you have the same Chipset?

I don't use RAID 0. Shouldn't this in theory/practice even be a little bit slower (at least for writes) than using a normal disk setup since it's just a mirror? I prefer incremental backups with my backup server (dirvish) ;-). For RAID 5, which seems to be the only RAID from which you can actually gain something, you need more than 2 hard disks which should only be an option on server setups. So, I can't really help with that. As far as I know, you cannot run hardware RAID in linux as yet, but I could be wrong. Anyway, I think RAID is over-rated. If you have 2 hard drives with the same capacity, I would consider doing incremental dirvish, rsnapshot, ... (something using rsync)? backups from hd1 to hd2. I do this every hour (automatically, via cron of course). That way, it is like a time machine. Also, this way, you can save space by not backing up (excluding) downloads, unimportant video data, not having a double swap, operating system files that you can get back easily, etc. As far as I know you can use dirvish also in windows.

Once I find enough time to continue my 64 bit quest, I will update the above website. For now I have to do my assignments (implementation of a DBMS buffer manager, Haskell, project) with my old machine, which actually runs better than the new one up to now. :-)

---

### Post by FRAMBO on 2006-09-02
I thought I would throw my name in the ring here as I too have the same motherboard and processor. 

However I'm a complete newbie when it comes to Ubuntu.  I really like what I see so far but I'm having a difficult time understanding how to configure hardware as I only really know how to do so from a Windoze point of view. 

Is there a guide that explains the equivents of Winxp in Ubuntu?  I could really use something like that as I'm scratching my head a lot right now when it comes to how to check if my system is installed correctly...

---

### Post by kuja on 2006-09-03
Well, I'm not really sure about your problem, but I thought I'd clear a few things up. As per RAID-0, it delivers up to a 100% boost (in theory) for each drive added to the array as it distributes data between the disks. As per hardware RAID, it works fine in Linux, so long as it is actually hardware RAID. Most of the RAID controllers in modern motherboards aren't actually real hardware RAID controllers. Getting Linux to recognize it and boot from it takes a little work, but is actually quite doable, in fact, I'm running from it right now :P

---

### Post by geek.de.nz on 2006-09-03
You are right, RAID 0 is striping, so not really RAID (Redundancy Array of Independent Disks), which the level indicates ;-).
I was thinking of RAID 1 when writing the above, where one disk is just mirrored. 
I regard RAID 0 as too dangerous though although it does give a real performance boost (200%). 

The chance of (total) data loss is also increased by 100%, because the chance of one disk failing is doubled and one cannot infer the data from the other disk. But if you are doing incremental backups on another disk or machine it does provide an advantage.

The issue here is not RAID though.

---

### Post by Milenko on 2006-09-04
Kuja,
     Would you be able to tell me how you got your RAID array up and running?  I am trying to install Dapper from the Live CD.  I have downloaded the dmraid package so now Gparted sees my array/partitions.  But when i try and create a new ext3 partition it gives me an error and won't do it?! When i let it try automatically it managed to create the swap partition inside my current extended but still no primary ext3 partition.  

Any advice would be greatly appreciated.

my spec :

M2N-SLI deluxe mobo
AMD64 x2 4400 dualcore
2 x hitachi 250gb hds (RAID-0)

thanks M.

"Build a man a fire and he'll stay warm for a day.  Set a man on fire and he'll stay warm for the rest of his life..."

---

### Post by kuja on 2006-09-05
Well, Milenko, it looks like you're on the right track.

I personally didn't have any luck getting the install going from the GUI. I followed the guide in the wiki (https://help.ubuntu.com/community/FakeRaidHowto") to set it up manually. As I said, it takes a bit of work to get it going, most of it is mindless copying and pasting though, with the exception of the partitioning. When I got to the partitioning part, I pulled upf a terminal and used the parted command. It's not very difficult to figure out how to use, though it seemed kind of foreign to me. I ran into trouble at the stage where it has you install dmraid inside the chroot as well... it came in a frame with about 5 commands with it, moving it to be the last of the 5 commands fixed it for me. Also, don't forgot to add a user to use, and add that user to the audio, cdrom, video, and admin groups. If you have any trouble, let me know.

---

### Post by doducchinh86 on 2006-09-09
geek.de.nz
I have trouble with my mobo (Asus M2NPV-MX ). It can't connect internet, I don't know why :confused: . Can you show me how to install the driver of nvidia (I see it in the cd included), please? And how to configure the network? I tried a lot but I still can't connect internet through adsl.
thanks.

---

### Post by geek.de.nz on 2006-09-22
Keep looking at my site on this. I'm at the stage of installing suspend2 with initrd which seems to be quite a hassle, but once that's done, I will post all the details on [http://www.ihostnz.com/ubuntu_dapper_am2](http://www.ihostnz.com/ubuntu_dapper_am2) . I've got the LAN, audio and NVIDIA graphics drivers working using the newest stable kernel release. Sound and LAN worked out of the box with that one, so no need to install the nvidia nforce drivers if you update the kernel to 2.6.17.13. The next 4 weeks I'm too busy with other stuff though.

---

### Post by vester on 2007-03-31
thanks for the post! got the install working, phew. using asus m2n-mx amd x2 3600+ for my home cinema/bacup/server.... siliet-ish pc.

---


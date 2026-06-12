---
title: "No hard disk detected during install"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by Photon on 2008-06-27
I tried installing Ubuntu 8.04 64 bit on my Core 2 Duo system. I could go all the way to the live screen, but during install, the partition manager does not detect any of the hard drives. I'm sure its not an issue with my system as Ubuntu 32 bit and Open suse 11 x86_64 both install fine. 

Is there a known issue, or am i doing something wrong?

Processor : Core 2 Duo E6550
Motherboard : Abit IP35-E
Hard Disks : 2 seagate sata without RAID

---

### Post by Rocket2DMn on 2008-06-27
You may want to try the alternate install cd, and may need to add some kernel boot options.  When I used the alternate install cd I had to add "acpi=off noapic" to the kernel boot options for my hard drives to be detected correctly.

---

### Post by Dimtar on 2008-07-02
How do i add boot options to the Kernel?

---

### Post by Rocket2DMn on 2008-07-02
I don't actually recall exactly how it goes down on a LiveCD or Alternate CD, but there should be an option somewhere about when to boot, or a GRUB screen where you select the kernel.  You want to edit that where it says "kernel" (the second line) and append those options to the end.
After you install you will need to add those options to a config file, but I can help you with that when the time comes.
Here is more info about changing boot options from GRUB - [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

If this post doesn't help, please post back and I'll see what I can do.  I'll boot from either a LiveCD or Alternate if necessary.

---

### Post by flytripper on 2008-07-02
side question... do you need drivers for a sata drive to be visible like some drives do for windows?

---

### Post by Rocket2DMn on 2008-07-02
> **flytripper said:**
> side question... do you need drivers for a sata drive to be visible like some drives do for windows?

No, I haven't heard of ever needing that.  Some people do have problems recognizing SATA drives at boot though, which is the topic of this thread :)

---

### Post by phlembob on 2008-07-02
Try going into bios and into your hdd boot selection order.  You can rearrange your SATA Drives order of recognition.  You may have both with NTFS formats, which sometimes will confuse the live version.  If your live cd still can't find your hdds, you can physically disconnect one SATA hdd to eliminate the computer choice --- to see if your live cd will find one SATA. I've noticed problems with SATA and IDE both being selected to Master, but by strapping the IDE to slave tends to stops that confusion. :guitar:

---

### Post by Dimtar on 2008-07-02
> **Rocket2DMn said:**
> No, I haven't heard of ever needing that.  Some people do have problems recognizing SATA drives at boot though, which is the topic of this thread :)

Using the alternate install CD it picked up my drive fine. Sorry i know it's off topic but after a successful install Ubuntu loads for ages. The progress bar that only has a small bar that moves from left to right continuously. It never loads and eventually goes to a black screen saying BusyBox. 

I have used Ubuntu before and this has never happened. Am i doing something wrong?

Thanks,
Daniel

---

### Post by Dimtar on 2008-07-02
> **phlembob said:**
> Try going into bios and into your hdd boot selection order.  You can rearrange your SATA Drives order of recognition.  You may have both with NTFS formats, which sometimes will confuse the live version.  If your live cd still can't find your hdds, you can physically disconnect one SATA hdd to eliminate the computer choice --- to see if your live cd will find one SATA. I've noticed problems with SATA and IDE both being selected to Master, but by strapping the IDE to slave tends to stops that confusion. :guitar:

The problems i was having were for a single Sata Drive only. It did have two NTFS partitions which may have confused the live version as you said.

I did have 40 gig of unallocated space on the drive setup for ubuntu. It is suprising that it did not pick up the free space either.

---

### Post by Rocket2DMn on 2008-07-02
It sounds like your install went bed somewhere.  Try adding those kernel boot options
```
acpi=off noapic
```
Use the link I provided in post #4 to help you out with that.  Otherwise you may need to start a new thread so people more experienced with booting into busybox can help you out.

---


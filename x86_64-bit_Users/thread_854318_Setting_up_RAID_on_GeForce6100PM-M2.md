---
title: "Setting up RAID on GeForce6100PM-M2"
date: 2008-07-09
forum: x86 64-bit Users
---

### Post by bjk on 2008-07-09
I have Ubuntu x86_64 bit installed on my new GeForce6100PM-M2/AMD Athlon 64 x2 and I would like to set up RAID 1. I have looked around the net and read various howto's on the subject, but to be honest, I'm finding it a little difficult to get a clear picture on exactly what I need to do. 

Could someone please advise me or point me in the right direction?

Thanks.

---

### Post by traderpats on 2008-07-12
Since no one has answered yet I'll share my limited knowledge.  I recently dove into RAID - using raid 1 for mirroring of the drives.  I'm using the A770M-A MB which has raid setup from a bios utility.  That would be hardware based which is really, really the way you want to go.  From what I've read you do NOT want a software based raid.  I enter the bios and form the raid array with the included utility.  Different MB's have different ways to enter the raid setup utility so check with the manufacturer.  

Once in the setup utility it's as easy as pie, seriously it is.   Select which type of raid, (0,1, 0+1, etc), then chose what disks to add to the array.  The HDs in the system should be listed there.  I only had a pair of 500GB drives so it was a no-brainer.  NOTE: You need at least TWO disks to form a raid and it's best if they're they're identical just to be safer.  After the array if formed, (lets see... raid 1 - "click", use this hd -"click", and this hd - "click",  done - "click"), reboot and install the OS ... whatever one you're going to run.  The hardware raid is independent of the OS.  It's not even seen by the OS.   For example my pair of Maxtor 500GB sata drives in a RAID 1 array are seen by the OS as a single 500GB drive. Just the way I want it too.  

You could build the array after you have a disk already setup but I haven't done it yet.  I guess it would be pretty much the same as rebuilding the array as if a disk went bad or if using an OS based raid.  

Anyway that's about all I have.  This is one of those things that you do it once you say, "That's it?"  Hope this helped.

---

### Post by rbstern on 2008-07-30
Follow up question on this:  Anybody know how the system warns you when a drive is going bad?  And what the recovery process is?  Is a drive swap and rebuild handled at the bios/hardware level?

I'm thinking about using this board as the basis for a NAS box in my home/office network, as opposed to a dedicated NAS device.

---

### Post by traderpats on 2008-07-30
On my system, during boot-up, there's a message flashed that the the RAID is "functional".  (Hope it stays that way too.)

As to rebuilding the hardware raid I think it would have to be done at the bios level.  As far as I've been able to determine the OS doesn't interact with the RAID array.  I've never had to rebuild one but the overall process has been fairly intuitive so far.  I'll bet if you replaced a bad drive and reformed the ARRAY, (RAID 1 anyway), the data would simply be mirrored on the new disk before continuing.

I would find out what RAID is included with the board and that should point you in the right direction.

---

### Post by rbstern on 2008-07-31
Thanks, tp.  Sounds logical.  I just set up my RAID 1 array on an ECS GeForce6100PM-M2 motherboard.  My impression from the bios RAID interface and the startup diagnostics messages matches what you described.

Am now getting started on Unbuntu Server 8.04.1 install now...

---


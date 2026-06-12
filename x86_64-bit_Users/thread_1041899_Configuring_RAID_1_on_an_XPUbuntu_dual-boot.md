---
title: "Configuring RAID 1 on an XP/Ubuntu dual-boot"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by Ben Webber on 2009-01-17
Hello, all,

I have a brand new system with three SATA hard disks. One is about 200 GB, the other two are about 300 GB. All three are formatted as NTFS. Windows XP x86-64 is installed on the 200 GB partition.

I am thinking of dual-booting Windows XP and Ubuntu 8.10 64-bit edition by partitioning the 200GB drive into an NTFS partition and an Ext3 or XFS partition. I've configured dual-boot systems before, so that's not a problem. The two 300 GB drives are meant for storage, and to be accessible from either OS. I intend to use software RAID 1 to mirror the data on the two 300 GB drives. While I have never set-up a RAID array before, I have read that for Linux this is not a challenge, and it can be done for XP as well. On their own, each OS can access and write to the RAID array flawlessly (in theory).

My concern is whether or not the software RAIDs from each OS will interfere in some way, corrupting the data. In some (admittedly scant) research, I've read this could be an issue, but those websites and forums were dated from a few years ago.

I would like to know if any of you have experience with RAID in dual-boot systems. Can it be done while protecting the data? Does it work flawlessly? Any information would be appreciated.

Regards,

Ben

---

### Post by bbqpope on 2009-02-12
I am curious about this as well, my sitaution is a little different, but maybe the solution this his problem will help me.

I am dual booting XP and 8.10 from a Sata hooked to my mobo.  I also have an IDE drive hooked to my Mobo, both work.   

In addition to the first two drives I have a SiI  3132 PCI express sata raid card with two 500 gb drives hooked up.  They are set up as a Raid 1, and I keep lots of critical photo data on them (which is backed up as well) They are formatted as NTFS and I would like it if linux could see them (it sees them but...)  and mount them.  

I cannot change them because, as it stands I am married to Photoshop, and I am trying out ubuntu and see if it is viable to use for a low budget photo editing solution.  I huess unsing a simple mavhine setup would have been best, but I don't have one right now.

---


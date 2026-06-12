---
title: "Intermittent IDE identification"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by phlembob on 2008-06-18
Hi,  I have installed NTFS-3g and named the drive.  It is located by Ubuntu 8.04 LTS 64 bit about 50% of the time.  I have both Ubuntu and XP Pro x64 on the same disk, but not the 120gb IDE.  I use it for back up and storage.  I use the Ubuntu more than the XP but lets face it some online things will not operate inside Linux/GNU.  I use OpenOffice and save back ups in .doc, which gives me both world access.

Any suggestions on curing an intermittent problem.  I think it is a bit that gets stuck on the IDE interface.  I sometimes go and boot windows and access the IDE then boot in Ubuntu and find it.  Sometimes not!

---

### Post by ScornForSega on 2008-06-18
Make sure you shut down Windows properly.

On an NTFS partition, Windows marks the partition as "closed" when it exits and if Ubuntu doesn't see that flag, it won't automatically mount it.

Alternatively, you can force a mount.  
```

sudo mount -t ntfs-3g /dev/[DEVICENAME] [LOCATIONOFMOUNT] -o force

```

---

### Post by phlembob on 2008-06-18
Thanks for the info, but a force mount won't work when the name isn't in memory.  Why, I have no idea.  I have shut down windows properly.  It still is intermittent.  I have tried to mount it before, but it registers as scsi in the Computer visual of Ubuntu.  Crazy things happen.  When I worked on Unix and Unisys we had occasional boot problems.  Mag tape, to paper tape, all the way to punch cards to load sometimes.  Once things were in order they would work for months with the occasional hardware failure.  Intermittent problems are the worst things because they don't stay broke or stay fixed/

---


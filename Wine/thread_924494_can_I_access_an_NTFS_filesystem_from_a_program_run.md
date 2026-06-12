---
title: "can I access an NTFS filesystem from a program running on wine?"
date: 2008-09-19
forum: Wine
---

### Post by klemperal on 2008-09-19
What I'm asking is can I access a NTFS file system from a program running in wine?  For example, if I'm using a DVD ripper in wine, could I select the output be a NTFS file system/partition?  The reason I ask is because I noticed I couldn't select my windows partition from a wine program.

---

### Post by asdfoo on 2008-09-19
Wine has nothing to do with your windows install, most often they should be kept completely seperate.

If you want to access part of your windows install you need to mount it using Nautilus or otherwise then you can define a drive letter to a path (such as  /media/disk/ or whereever the drive is mounted) using winecfg.

---


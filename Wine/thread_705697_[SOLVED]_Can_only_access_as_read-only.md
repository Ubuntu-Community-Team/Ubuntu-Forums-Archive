---
title: "[SOLVED] Can only access as read-only"
date: 2008-02-23
forum: Wine
---

### Post by superzorro on 2008-02-23
Hi, recently I'm having a problem opening documents in Office 2003 using crossoveroffice or Wine.

I run a dual-boot Ubuntu - Vista, I have one NTFS partition with all my documents.

Until a few weeks I was able to  open, edit, write, and save all doc, xls, ppt files in  Office 2003. 

However l haven't been able to this anymore. When I open doc files it opens as **read-only** and excel files, xls , wont even open it gives an error [B]could not find file[B] check spelling....

I know this is not a privilieges issue because I can modify the name, cut, copy the files in nautilus, and I can open them with read and write access in Openoffice.

The strange thing is that this is something new I don't know if it broke with some update.


I would appreciate some help.

---

### Post by superzorro on 2008-02-25
Well I've been searching, and I was wrong Crossover office doesn't support writing in NTFS partitions, I think I was opening the files on an external drive (has the same files as my partition) and as this is a FAT32 it ha no truble.

Well I decided to pass all of my files to the ext3 partition.

---


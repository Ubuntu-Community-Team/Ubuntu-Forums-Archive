---
title: "Can i install Ubuntu on my pc?"
date: 2005-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ..::Linus::.. on 2005-06-27
Hi all,


this is my first post in this forum.. :) 

I want to install Ubuntu on my pc:

A64 3800+ 
A8N Sli-deluxe
2x512 MB ram ddr
HD Maxtor Sata Dmax10 200GB
x850xt pci-e

Now i've only two partitions and in one i've installed windows xp, the other is empty and i'd like to put ubuntu in dual boot with windows

Do you think that i can have some installation problems with my pc, in particular with my Maxtor S-ata?

thanks for your help and answers.
L.

---

### Post by rachii on 2005-06-27
try the ubuntu live cd.   that way you dont have to install anything, and potentially ruin your setup, but you can find out whether your hardware is supported or not

---

### Post by apollo2011 on 2005-06-27
Welcome to the Ubuntu Forums ..::Linus::.. :)

I don't think you should have any problems installing Ubuntu on your system with that hardware configuration.  The best way to find out is to try :).  If you are worried that your hard drive will cause problems, you should be okay if when the partitioner comes up, it shows your current partition setup properly.  You might also want to try the Live CD version of Ubuntu, which will load right off the CD and doesn't require any installation.

I assume the second partition you have is unformatted and doesn't have any data on it.  If it is formatted, Ubuntu can reformat into Ext3 or Reiserfs (the 2 most common Linux file systems).  If it does have data on it, you will need to backup/move that data either on to the other partition or to another hard drive/CD/DVD, at least temporarily.

You might want to do some research on the two filesystems (Reiserfs and Ext3).  Both are very similar but Reiserfs has better methods of preventing file/disk fragmentation and disk corruption.  Therefore, I would recommend you use Reiserfs for your Ubuntu partition

The other thing you might want to know, is that any file system you install Ubuntu on, Windows XP won't be able to see it.  You might want a 3rd FAT32 partition if you are going to need to have data available on both operating systems.  Also, assuming your WinXP is on an NTFS-formatted partition, Ubuntu won't be able to write to it. You can set it up later to read it, but not write to it.  This is because Microsoft has kept the specs on how to write to NTFS closed so the Linux developers can't see them.  There is software that will write to NTFS but most of it is not foolproof and might corrupt your NTFS partition.  If you do need to write to NTFS, your best bet would be CaptiveNTFS, which loads the Windows NTFS driver on Linux.

Hope this helps you sort out the best way to install Ubuntu on your PC.  :smile:

---

### Post by ..::Linus::.. on 2005-06-27
Thanks apollo2011, rachii for your help.

[OT]
thanks for "welcome" apollo2011...you live in Usa, connecticut!! wow!!
I hope to visit usa very soon...it's a dream for me!  :) but before i need to improve my english ....eheh!
[/OT]

I've just started downloading the live-cd as you have suggested to me...

before trying to install ubuntu, yesterday l tried to create an image-dvd of my HD with Norton Ghost, and also with Acronic True Image, but it was impossible because my hard disk was not recognized at all, by norton Ghost or True Image.....so...here why i've asked about my maxtor sata.

sincerely
L.

---

### Post by apollo2011 on 2005-06-27
Sounds like you are on your way to installing Ubuntu :).

From your posts, your English seems quite good ;)

---

### Post by Darkscot on 2005-06-28
[QUOTE=..::Linus::..]Hi all,


this is my first post in this forum.. :) 

I want to install Ubuntu on my pc:

A64 3800+ 
A8N Sli-deluxe
2x512 MB ram ddr
HD Maxtor Sata Dmax10 200GB
x850xt pci-e

Now i've only two partitions and in one i've installed windows xp, the other is empty and i'd like to put ubuntu in dual boot with windows

Do you think that i can have some installation problems with my pc, in particular with my Maxtor S-ata?

thanks for your help and answers.
L.[/QUOTE]

I installed Ubuntu on my Athlon64 based PC last night.  It also has a Maxtor 200GB SATA drive and it had no problems with it at all.  In fact everything worked like a dream and it runs like hot snot, much faster than Mandriva LE2005 that I had installed previously (sorry starry eyed pengiun!).

One word of caution though!  The section of the installation where it partitions the disk is NOT very intuitive.  I new what I was doing because I have previously installed Ubuntu on my other PC.  I strongly advise you look at the options carefully and do not rush that bit.  Plus the default option is to format your whole hard drive!!!  :roll:

---

### Post by Darkscot on 2005-06-28
[QUOTE=apollo2011]Welcome to the Ubuntu Forums ..::Linus::.. :)

SNIP

You might want to do some research on the two filesystems (Reiserfs and Ext3).  Both are very similar but Reiserfs has better methods of preventing file/disk fragmentation and disk corruption.  Therefore, I would recommend you use Reiserfs for your Ubuntu partition

SNIP

[/QUOTE]

This was very useful info and came just in time for my install last night.  I wasnt even aware Reiserfs existed and would have just plumped for Ext3.  It sounds an improvment on ext3 but time will tell.  My PC is certainly seems to be accessing the HD faster than it does with XP.  But maybe that is just wishful thinking?   

Here is a tip for others who want to find out more about Reiserfs. You should Google for 'Reiser File System'.  That brings up a lot more relevant stuff than just Reiserfs.

---

### Post by apollo2011 on 2005-06-28
[QUOTE=Darkscot]This was very useful info and came just in time for my install last night.  I wasnt even aware Reiserfs existed and would have just plumped for Ext3.  It sounds an improvment on ext3 but time will tell.  My PC is certainly seems to be accessing the HD faster than it does with XP.  But maybe that is just wishful thinking?   

Here is a tip for others who want to find out more about Reiserfs. You should Google for 'Reiser File System'.  That brings up a lot more relevant stuff than just Reiserfs.[/QUOTE]

Yes, when I first tried Linux, I used SuSE and by default it used Reiserfs.  Many distros have/are going to switch to using Reiserfs by default, Aome don't even have support for it unless you install the drivers/software after installation.  Ubuntu doesn't use it by default yet, but it does have support for it out of the box.

P.S. For you or anyone else interested, the best place I found for information on Ext3 and Reiserfs was on Wikipedia. [Wikipedia:Reiserfs](http://en.wikipedia.org/wiki/Reiserfs) 
[Wikipedia:ext3](http://en.wikipedia.org/wiki/Ext3) 
Both of those articles link to several other articles that are also really interesting.

---


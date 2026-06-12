---
title: "Making the transition (are my Windows days over?)"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Levdir on 2006-01-31
Okay, I've got the knowledge neccessary to install Ubuntu as a second boot on a new partition on my hard drive and am planning on going ahead with this. What I need to know is, once I have my hard drive partitioned off, will I be able to move files from one section to another? I'll have the NTFS partition with Windows on it, a FAT32 logical partition, and an Ubuntu partition. Can I move files from one to the other? And, looking ahead, if I get everything moved over to the Ubuntu partition, can I reformat the NTFS partition and merge it with the Ubuntu partition so I've not got a large portion of my hard drive as dead space?

Also, I've been reading some of the previous forum posts and it sounds like even though I'm running a 64-bit system, the 32-bit version of Ubuntu is the way to go for now. I'm a Linux neophyte and it sounds as though the 64-bit versions takes a degree of familiar with the system. Is this correct? What benefits does the 64-bit version have for 64-bit users?

Finally, I've heard tell of an app called WINE that allows emulation of Windows apps in Ubuntu. What sort of apps does this include? Will it run, for example, World Of Warcraft, Photoshop 7, or The Elder Scrolls IV: Oblivion? Eventually I'd like to be rid of Windows entirely, but that'll be dependant on Ubuntu's ability to run some of my core Windows apps. Can WINE do what I need?

Thanks in advance for any help.

---

### Post by aysiu on 2006-01-31
[QUOTE=Levdir]Okay, I've got the knowledge neccessary to install Ubuntu as a second boot on a new partition on my hard drive and am planning on going ahead with this. What I need to know is, once I have my hard drive partitioned off, will I be able to move files from one section to another? I'll have the NTFS partition with Windows on it, a FAT32 logical partition, and an Ubuntu partition. Can I move files from one to the other?[/quote] First of all, I want to say "Kudos." You've really done your research. That's rare. In any case, yes, you can share files on a FAT32 partition. You'll have to mount that partition, but you can see the fourth link of my signature for instructions on that. 

> And, looking ahead, if I get everything moved over to the Ubuntu partition, can I reformat the NTFS partition and merge it with the Ubuntu partition so I've not got a large portion of my hard drive as dead space? As I understand it, you can tack more onto the *end* of an existing partition, but not more on the beginning. If Windows is at the beginning of your drive, you may just have to keep it as a separate data partition.

> 
Finally, I've heard tell of an app called WINE that allows emulation of Windows apps in Ubuntu. What sort of apps does this include? Will it run, for example, World Of Warcraft, Photoshop 7, or The Elder Scrolls IV: Oblivion? Eventually I'd like to be rid of Windows entirely, but that'll be dependant on Ubuntu's ability to run some of my core Windows apps. Can WINE do what I need? Wine will run most things that would work on Windows 98. Crossover Office will run most stuff that would run on Windows 2000 or XP. Cedega is a modified version of Wine specifically for games.

---

### Post by RAOF on 2006-02-01
[QUOTE=Levdir]...Is this correct? What benefits does the 64-bit version have for 64-bit users?

Finally, I've heard tell of an app called WINE that allows emulation of Windows apps in Ubuntu. What sort of apps does this include? Will it run, for example, World Of Warcraft, Photoshop 7, or The Elder Scrolls IV: Oblivion? Eventually I'd like to be rid of Windows entirely, but that'll be dependant on Ubuntu's ability to run some of my core Windows apps. Can WINE do what I need?

Thanks in advance for any help.[/QUOTE]
The 64bit version appears to be significantly faster at some things.  (See benchmarks here: [http://www.anandtech.com/linux/showdoc.aspx?i=2213&p=1](http://www.anandtech.com/linux/showdoc.aspx?i=2213&p=1)).

To check out what programs work with wine, check out the wine applications database: [http://appdb.winehq.org/](http://appdb.winehq.org/).  And for games, the Ubuntu Gaming forum is also a good bet.  I know that Photoshop 7 works (with a specific version of wine - 0.9.2, I believe).  World of Warcraft works.

---

### Post by UrbanFallout on 2006-02-02
Careful with your choice of partition type.

For linux NTFS partitions can only be mounted in Read-Only mode. I looked into this and there are programs that can write to NTFS partitions, but none of these appear to be trusted.

For myself I keep an addition FAT32 partition for sharing data between windows and linux that I need to write to regularly from either operating system.

You can also read info from EXT2FS partitions in windows using a handy application called Explore2fs, but its very slow.

Removing your NTFS partition at some later stage is easy. Use "parted". If you want to merge partitions I'd advise copying your data first and the deleting the partition you want to remove.

Backing up your ntfs partitions via linux is also very easy! Install the "ntfsprogs" package. It has many handy ntfs manipulation utilities but the one you'll want to use is ntfsclone.

Hope this helps!
Nick

---

### Post by RAOF on 2006-02-02
You can actually read/write to ext2/3 partitions from Windows natively using the ext2 filesystem driver from [www.fs-driver.org](www.fs-driver.org).

Edit:  Additionally, if you use LVM you can add space to your existing partitions no matter where it is - you can set it up from the Ubuntu installer.

---

### Post by Levdir on 2006-02-03
Thanks, everyone, this has been a big help. I think (since I'm getting an unusually fat paycheck tomorrow) that I am simply going to buy a second hard drive exclusively for Ubuntu and eventually reformat the current one for storage. Of course, that opens up some further questions; will Ububntu recognise the data on the original drive (as in, can it read and understand the old Windows file structure)? If it can, it'll be no matter to get things moved over, but if not, what can I do to make Ubuntu a) notice the old hard drive, or given that, b) be able to manipulate the files therein?

Also, am I right to assume that universal filetypes such as .jpg and .mp3 behave similarly in a Linux environment as in Windows? I have no problem moving such things between Windows and MacOS, but I've never had the opportunity to do so with Linux and I'll go mad without me tunes!

---

### Post by onesojourner on 2006-02-03
you will be able to mount the windows partition whether its on your first hdd or your second. mp3 and other codecs are easy to install. you just need the win32 codecs and that will take care of about everything. just do a search on here if you want to learn more.

---

### Post by Levdir on 2006-02-04
Perfect. Thank you.

---


---
title: "Azureus -  Error: Disk write error - Input/output error, write fails, flush fails"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by frenchdm on 2006-05-28
Hi All,

Installed ubuntu 5.10 AMD64 the other day and all has been going well and i must say these forums have been a big help to little issues i have been having.

There is however one thing i can't figure out. Azureus gives the following error when downloading on some torrents (and hashing other larger ones (i.e. > 10GB)):

Error: Disk write error - Input/output error, write fails, flush fails

I can't quite figure it out.  The disk is a 200GB WD SATA, formatted FAT32.  No other programs are having any issues writing to the disk at all and the reading/writing speeds are quite fast (i.e. as fast as it was on XP).

Stopping and starting the torrent gets it going again but it can take a few tries before it has enough time to completely download the file.  Needless to say, this is quite annoying.

I would appreciate any help you guys can give.

Cheers,
frenchdm

edit: i just realised this might be better served in the begineers forum O_o.  I apologise if this is in the wrong place.

---

### Post by chrestomanci on 2006-05-28
Perhaps the Fat-32 filesystem is the problem. I know that you cannot store files bigger than 4Gb on Fat-32. Are any of the files in your torrents bigger than this?

On linux, Azureus will create sparse files where it can, so when you start downloading it will create a file that will appear to be one size, but will actually take less size on disc, as all the empty parts of the file will not be stored. As the more stuff is downloaded, the file will gradually take more space, without appearing to get bigger. 

If the torrent fails part way through the download, then this might be the cause.

---

### Post by frenchdm on 2006-05-28
Hi chrestomanci,

Thanks for your reply.  The > 4GB file size was my initial thought as well but all files are alot less then this (i.e. ~ 350mb each).

This is the only thing downloading at the moment, so i can't imagine the cacheing of large amounts of data will be an issue.

---

### Post by chrestomanci on 2006-05-28
Sorry, I can't think of anything else, Perhaps there is an Azureus forum you could try?

---

### Post by e99swa on 2006-05-28
Have you activated "sequential writing" in setting, you have to if you have a FAT filesystem.
But it's true like said before that the filesystem have a limit for individual files for approx 4Gb

---

### Post by frenchdm on 2006-05-29
heh...ok, do you think this might have something to do with it?

frenchdm@frenchdm:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24321/255/63, sectors = 390721968, start = 0

or this?

frenchdm@frenchdm:~$ sudo sdparm /dev/sda
    /dev/sda: ATA       WDC WD2000JD-22H  08.0
Read write error recovery mode page:
  AWRE        1  [ sav:  1]
  ARRE        1  [ sav:  1]
  PER         0  [ sav:  0]
Caching (SBC) mode page:
  WCE         1  [ sav:  1]
  RCD         0  [ sav:  0]
Control mode page:
  SWP         0  [ sav:  0]

---

### Post by Pentajet on 2008-02-29
The REAL reason is a memory leak caused by Trend Micro Internet Security Scan engine 8.500.

Solution: Use system restore to roll back your PC to some point before the horrid thing was installed (Trend Micro distributed the monster on 14th September 2007 for the first time). Note: this might not be required but it's what I did. Maybe you can run some memory fixing program instead or skip this step completely. Download scan engine 8.320 and overwrite the three dlls for 8.500 with those from 8.320 (8.320 is easy to find around with google.  It can still be downloaded from the TM site.  I am not including it as an attachment). You will have to overwite the files each time TMIS updates because it will keep up trying to install 8.500. WARNING: using old components with TMIS might pose your computer at greater risk against viruses or spyware. I suggest using a different program until Trend fix this issue. I am very surprised that nobody on the net has noticed this before I did considering the number of people to whom this is happeneing....

NB: Considering the information supplied by the poster I am not sure if this is actually the problem he is experiencing.  Typically people who have this problem have problems also with all other applications on their system plus the error message always says "Insufficient system resources" so rather than TMIS messing with your memory it might be some other program messing with your hard disk. But you may give a try and others who have the same problem but for all programs on their machine with memory being the culprit I am sure it will work.

---

### Post by Sabeeh on 2008-05-28
I'm having the very same problem...Its working on Vista and on Transmission too on ubuntu without any problems...I think its more of an Azureus bug.
Any effort to solve this issue will be highly appreciated!

---


---
title: "best filesystem for largeish raid volume"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by techtrickster on 2009-01-25
Hello, I just created a 3TB raid volume for my computer.  My system is as follows
quad core phenom processor
8GB ddr2 
32GB patriot solid state boot disk w 10GB for root
300GB sata hard drive for torrents 
4 x 1TB hard drives in a software raid 5 and I may add more later
9800gt video card
I am running kubuntu 8.04 but I am flexible on that

I would like advice on the best file system for the 3TB volume.  Speed isn't really a problem for me as all i do with the system is crunch numbers for boinc, download and watch video. My main requirement is that I want the most reliable file system for long term use.  If a hard drive dies I can replace it immediately. But I need a file system that is stable. I will be storing mostly movie and mp3 on the file system, but I will probably back up anything and everything to it once it is up. 

I have already read around about this topic somewhat but most of the post are either a few years old or deal mostly with speed.  As I said I don't really care about speed or resources or compatibility, only the reliability.

Thanks

---

### Post by Alterax on 2009-01-25
Depends mainly on the file sizes; since you mentioned you do a lot of video, I'm assuming these videos are mostly over the 2GB mark.  That being the case, I'd recommend xfs or ext4; both are very capable when it comes to handling large file sizes.

Now if they're mainly smaller files, you're working with, I'd stick with ext3.

---

### Post by srt4play on 2009-01-25
Ext3 works fine for me on a 2.5TB six disk array holding 4.5-17GB video files, streamed via samba to several clients.

---

### Post by techtrickster on 2009-01-25
As for file sizes I have about 50,000 4MB or so. Right now a few thousand at 200 -300 MB another few thousand at 700MB. I have a few dozen at about 5 GB a pop, and backups of other stuff like my home directory at varied sizes.  The speed of search and access add and delete isn't a problem for me as the difference in those times is of little consequence compared to the idea of losing the files. Usable size really isn't a problem either.  Stability, the time for a rebuild or grow, and the time for a fsck (hours not a problem months would be) are what matter to me.  Any info or links I get will be helpful.
Thanks

---

### Post by click170 on 2009-09-15
Bump?
Hey techtrickster  did you end up picking one?  Which one?  Was there a motivating reason for choosing that one for you or was it a roll of the dice?

I have a 2.5Tb RAID6, which is in the process of formatting thanks to filesystem corruption.  It was using Ext3 at the time, but I can't say for sure what the cause of the corruption was so I'm not comfortable blaming Ext3 for it either; there had been one instance where the power had failed and the system wasn't on a UPS a while back.

The great and mighty Google has suggested JFS and XFS in my recent googlings, mostly 'cause they are fast at deleting large files it seems like.  

Trying to cleanup my video library stored under Ext3 was painful, best way was to do it from the command line and send every rm job to the background with '&', creating a pile of running rm jobs in the background.

I'm leaning towards XFS, but the number of reports about corruption are troubling.

---

### Post by techtrickster on 2009-09-16
I ended up going with ext3.  Mostly for the stability and proven track record.  The main two reasons I considered anything else were curiosity and the lack of a defrag tool.  I figured that I could always upgrade to ext4 (which does have a defrag tool) once my drives got more full and the format was more stable and proven.  Another thing that you should consider when picking out a fs is whether or not you have a multi-core processor.  I know some of the f-systems make use of the "big kernel lock" I'm pretty sure that results in poor performance on multi-core systems.  good luck and don't panic

---

### Post by techtrickster on 2009-09-16
> **click170 said:**
> Bump?
Hey techtrickster  did you end up picking one?  Which one?  Was there a motivating reason for choosing that one for you or was it a roll of the dice?

I have a 2.5Tb RAID6, which is in the process of formatting thanks to filesystem corruption.  It was using Ext3 at the time, but I can't say for sure what the cause of the corruption was so I'm not comfortable blaming Ext3 for it either; there had been one instance where the power had failed and the system wasn't on a UPS a while back.

The great and mighty Google has suggested JFS and XFS in my recent googlings, mostly 'cause they are fast at deleting large files it seems like.  

Trying to cleanup my video library stored under Ext3 was painful, best way was to do it from the command line and send every rm job to the background with '&', creating a pile of running rm jobs in the background.

I'm leaning towards XFS, but the number of reports about corruption are troubling.
One thing for you specifically.  I can grow my raid 5 if I feel like it so the defrag is not such a big deal (it does take forever though).  As far as I know you can't grow that raid 6 of yours even if your fs gets really full. you may wish you had that defrag ability. just saying.
good luck and don't panic

---

### Post by laluz on 2009-09-16
I have just installed a RAID6 with JFS on Intrepid and it fell apart on a second day. Three of five disks were found to be non-fresh after a reboot. 
The problem does not seem to be with the JFS. JFS seems to be OK as after reassembling all data was there.
BTW, to --assemble --force the array I had to compile mdadm 2.7.9 from source as the 2.7.6 has a bug within --force. 
People are talking everywhere that raid is no substitute for a back-up, and now I see why. 
I wonder if raid is supposed to be so fragile and what are you experiences with your arrays?

---

### Post by techtrickster on 2009-09-17
> **laluz said:**
> I have just installed a RAID6 with JFS on Intrepid and it fell apart on a second day. Three of five disks were found to be non-fresh after a reboot. 
The problem does not seem to be with the JFS. JFS seems to be OK as after reassembling all data was there.
BTW, to --assemble --force the array I had to compile mdadm 2.7.9 from source as the 2.7.6 has a bug within --force. 
People are talking everywhere that raid is no substitute for a back-up, and now I see why. 
I wonder if raid is supposed to be so fragile and what are you experiences with your arrays?

I have had my raid go down several times.  I have rebuilt almost every time (had a second piece of hardware die during rebuild) thats the point.  hardware dies but most of the time raid should be able to be rebuilt. i like the raid 5 with a redundant backup of the really important stuff on a totally different system  preferably located somewhere else. I.E. right now my main raid 5 is down. it has all of my archived stuff.  I am confident I can get it back with a little effort.  I have all of my important info in two other locations.  Thats the way i like it. do i want to lose anything at all? obviously no.  but this way it is extremely unlikely that i will lose my really important stuff. the other stuff is simply less likely to be lost than most peeps data.  

Ask yourself, how important is that data?  The answer to that question will led you how well should it be backed up.
-vital - multiple copies, different geological locations, different media
- shame to lose - at least  1 primary and 2 secondary copies at least two types of media
- sorta nice - single copy on a redundant method
-transitory - single copy
thats my advicee
good luck - dont panic

---

### Post by click170 on 2009-09-19
I've so far only had the one problem with my RAID drive, and that was a filesystem corruption problem (not sure what caused it though :( ).

I have never had a problem restarting my system and having the RAID come up with ONE exception; External USB Drives.  If I use an external usb hard drive (I'm guessing this would apply to firewire as well?), you seem to have to re-add the drive to the array on boot.  I'm not sure exactly what the cause is, still pondering.  I don't have my array set with the configuration file though, I use Linux Raid Autodetect paritions and mdadm automagically has sex^h^h^h makes them do things so that my data is available.  Only reason I know is because I lost 2 drives (bought them together *facepalms*) at the same time, so I used my USB drive to prop up my RAID until the drives came back from warranty repair.

No, you most certainly can grow a RAID6 array, I tried it once already out of curiosity.  Unfortunately, there is no shrink function though.  

I ended up going with XFS because its fast at deleting stuff, and the files stored on it will be watched by a program I'm writing (for another purpose), so any corruption that may happen will be caught immediately.  Also probably because of my recent EXT3 mess up I have a little negative bias towards it right now.  We'll see how XFS does.  
On the other hand, it HAS to be said, recovery from my ext3 was not difficult thanks to how you can mount an ext3 filesystem as ext2 (it was my journal preventing proper mount as ext3).

---

